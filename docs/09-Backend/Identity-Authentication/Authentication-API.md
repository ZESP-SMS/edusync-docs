# Authentication API Specification

| Field | Value |
| --- | --- |
| Title | Authentication API Specification |
| Document ID | EDUSYNC-BE-AUTH-API-001 |
| Version | 1.0 |
| Status | Draft |
| Author | Pushpraj Jaiswal |
| Created Date | 2026-07-05 |
| Last Updated | 2026-07-05 |
| Reviewers | Product Owner, Architect, Security Engineer, Backend Lead, QA Lead |
| Approval Status | Pending Review |
| Confidentiality | Internal |

---

## Revision History

| Version | Date | Author | Changes |
| --- | --- | --- | --- |
| 1.0 | 2026-07-05 | Pushpraj Jaiswal | Initial API specification. |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Purpose](#2-purpose)
3. [Objectives](#3-objectives)
4. [Scope](#4-scope)
5. [Out of Scope](#5-out-of-scope)
6. [Audience](#6-audience)
7. [Definitions](#7-definitions)
8. [Assumptions](#8-assumptions)
9. [Dependencies](#9-dependencies)
10. [API Standards](#10-api-standards)
11. [Endpoint Summary](#11-endpoint-summary)
12. [Endpoint Details](#12-endpoint-details)
13. [Common Errors](#13-common-errors)
14. [References](#14-references)
15. [Conclusion](#15-conclusion)

---

## 1 Executive Summary

This document defines the Identity & Authentication API contract for EduSync Phase 1.

It covers login, token refresh, logout, password reset, email verification, current user profile, sessions, roles, permissions, and role assignment.

---

## 2 Purpose

Define the backend API contract before implementation starts.

---

## 3 Objectives

| ID | Objective | Priority |
| --- | --- | --- |
| OBJ-001 | Define authentication endpoints. | Critical |
| OBJ-002 | Define session and token endpoints. | Critical |
| OBJ-003 | Define RBAC read and assignment endpoints. | Critical |
| OBJ-004 | Define request, response, validation, and error standards. | High |

---

## 4 Scope

| In Scope |
| --- |
| Login |
| Refresh token |
| Logout |
| Logout all devices |
| Forgot password |
| Reset password |
| Email verification |
| Change password |
| Current user profile |
| User sessions |
| Roles |
| Permissions |
| User role assignment |

---

## 5 Out of Scope

| Out of Scope | Reason |
| --- | --- |
| Student APIs | Academic module |
| Fee APIs | Finance module |
| Notification APIs | Communication module |
| Subscription APIs | Platform module |
| OAuth and SSO APIs | Future enhancement |
| MFA APIs | Future enhancement |

---

## 6 Audience

| Role | Purpose |
| --- | --- |
| Backend Lead | API implementation |
| Frontend Lead | Web integration |
| Mobile Lead | Mobile integration |
| Security Engineer | Security review |
| QA Lead | API test planning |

---

## 7 Definitions

| Term | Meaning |
| --- | --- |
| Access Token | Short-lived JWT used for API access |
| Refresh Token | Long-lived token used to rotate access |
| RBAC | Role-Based Access Control |
| Tenant Context | Active school context for a tenant user |

---

## 8 Assumptions

| ID | Assumption |
| --- | --- |
| ASM-001 | All endpoints use HTTPS in deployed environments. |
| ASM-002 | Access tokens are sent using `Authorization: Bearer <token>`. |
| ASM-003 | Refresh tokens are stored and validated by hash. |
| ASM-004 | Tenant APIs require active school context. |
| ASM-005 | All timestamps use ISO 8601 UTC format. |

---

## 9 Dependencies

| Dependency | Source |
| --- | --- |
| Identity & RBAC schema | `docs/07-Database/Identity-RBAC-Phase-1.md` |
| Epic Overview | `docs/09-Backend/Identity-Authentication/Epic-01-Identity-Authentication.md` |
| Sprint Plan | `docs/09-Backend/Identity-Authentication/Sprint-01-Plan.md` |

---

## 10 API Standards

### 10.1 Base URL

```text
/api/v1
```

### 10.2 Common Headers

| Header | Required | Description |
| --- | --- | --- |
| `Content-Type: application/json` | Yes | Required for JSON requests |
| `Authorization: Bearer <access_token>` | For protected APIs | JWT access token |
| `X-Request-Id` | Recommended | Request tracing |
| `X-School-Id` | For tenant context APIs | Active school context |

### 10.3 Common Success Envelope

```json
{
  "success": true,
  "data": {},
  "message": "Request completed"
}
```

### 10.4 Common Error Envelope

```json
{
  "success": false,
  "error": {
    "code": "AUTH_INVALID_CREDENTIALS",
    "message": "Invalid email or password"
  }
}
```

---

## 11 Endpoint Summary

| Method | Endpoint | Purpose | Authentication |
| --- | --- | --- | --- |
| POST | `/api/v1/auth/login` | Login | Public |
| POST | `/api/v1/auth/refresh` | Rotate refresh token | Public with refresh token |
| POST | `/api/v1/auth/logout` | Logout current session | Required |
| POST | `/api/v1/auth/logout-all` | Logout all sessions | Required |
| POST | `/api/v1/auth/forgot-password` | Request password reset | Public |
| POST | `/api/v1/auth/reset-password` | Reset password | Public with reset token |
| POST | `/api/v1/auth/verify-email` | Verify email | Public with verification token |
| POST | `/api/v1/auth/change-password` | Change password | Required |
| GET | `/api/v1/me` | Current user profile | Required |
| GET | `/api/v1/me/sessions` | List active sessions | Required |
| DELETE | `/api/v1/me/sessions/{id}` | Revoke one session | Required |
| GET | `/api/v1/roles` | List roles | Required |
| POST | `/api/v1/roles` | Create role | Required |
| GET | `/api/v1/permissions` | List permissions | Required |
| POST | `/api/v1/users/{id}/roles` | Assign role to user | Required |

---

## 12 Endpoint Details

### 12.1 POST `/api/v1/auth/login`

| Item | Value |
| --- | --- |
| Purpose | Authenticate user and create session |
| Authentication | Public |
| Authorization | Not required |
| Headers | `Content-Type`, `X-Request-Id` |
| Request Body | `email`, `password`, optional `schoolId`, `deviceId`, `deviceName` |
| Response | Access token, refresh token, user summary, active context |
| Status Codes | `200`, `400`, `401`, `423`, `429` |
| Validation | Email and password are required |
| Errors | Invalid credentials, locked account, inactive account, rate limited |

```json
{
  "email": "admin@school.com",
  "password": "********",
  "schoolId": "uuid",
  "deviceId": "browser-device-id",
  "deviceName": "Chrome on macOS"
}
```

### 12.2 POST `/api/v1/auth/refresh`

| Item | Value |
| --- | --- |
| Purpose | Rotate refresh token and issue new access token |
| Authentication | Refresh token |
| Authorization | Active session required |
| Headers | `Content-Type`, `X-Request-Id` |
| Request Body | `refreshToken` |
| Response | New access token and refresh token |
| Status Codes | `200`, `400`, `401`, `409` |
| Validation | Refresh token is required |
| Errors | Invalid token, expired token, revoked token, token reuse |

### 12.3 POST `/api/v1/auth/logout`

| Item | Value |
| --- | --- |
| Purpose | Revoke current refresh token and session |
| Authentication | Required |
| Authorization | Current user |
| Headers | `Authorization`, `Content-Type` |
| Request Body | Optional `refreshToken` |
| Response | Logout confirmation |
| Status Codes | `200`, `401` |
| Validation | Access token must be valid |
| Errors | Unauthorized |

### 12.4 POST `/api/v1/auth/logout-all`

| Item | Value |
| --- | --- |
| Purpose | Revoke all active sessions for current user |
| Authentication | Required |
| Authorization | Current user |
| Headers | `Authorization` |
| Request Body | None |
| Response | Revoked session count |
| Status Codes | `200`, `401` |
| Validation | Access token must be valid |
| Errors | Unauthorized |

### 12.5 POST `/api/v1/auth/forgot-password`

| Item | Value |
| --- | --- |
| Purpose | Send password reset instructions |
| Authentication | Public |
| Authorization | Not required |
| Headers | `Content-Type` |
| Request Body | `email` |
| Response | Generic confirmation |
| Status Codes | `202`, `400`, `429` |
| Validation | Valid email is required |
| Errors | Invalid request, rate limited |

### 12.6 POST `/api/v1/auth/reset-password`

| Item | Value |
| --- | --- |
| Purpose | Reset password using reset token |
| Authentication | Reset token |
| Authorization | Valid reset token |
| Headers | `Content-Type` |
| Request Body | `token`, `newPassword` |
| Response | Password reset confirmation |
| Status Codes | `200`, `400`, `401` |
| Validation | Token and valid password are required |
| Errors | Invalid token, expired token, weak password |

### 12.7 POST `/api/v1/auth/verify-email`

| Item | Value |
| --- | --- |
| Purpose | Verify email address |
| Authentication | Verification token |
| Authorization | Valid verification token |
| Headers | `Content-Type` |
| Request Body | `token` |
| Response | Email verification confirmation |
| Status Codes | `200`, `400`, `401` |
| Validation | Token is required |
| Errors | Invalid token, expired token |

### 12.8 POST `/api/v1/auth/change-password`

| Item | Value |
| --- | --- |
| Purpose | Change current user password |
| Authentication | Required |
| Authorization | Current user |
| Headers | `Authorization`, `Content-Type` |
| Request Body | `currentPassword`, `newPassword` |
| Response | Password change confirmation |
| Status Codes | `200`, `400`, `401` |
| Validation | Current and new password are required |
| Errors | Invalid current password, weak password |

### 12.9 GET `/api/v1/me`

| Item | Value |
| --- | --- |
| Purpose | Get current user profile and active roles |
| Authentication | Required |
| Authorization | Current user |
| Headers | `Authorization`, optional `X-School-Id` |
| Query Parameters | None |
| Response | User profile, contexts, roles, permissions summary |
| Status Codes | `200`, `401` |
| Validation | Access token must be valid |
| Errors | Unauthorized |

### 12.10 GET `/api/v1/me/sessions`

| Item | Value |
| --- | --- |
| Purpose | List current user sessions |
| Authentication | Required |
| Authorization | Current user |
| Headers | `Authorization` |
| Query Parameters | Optional `status` |
| Response | Session list |
| Status Codes | `200`, `401` |
| Validation | Access token must be valid |
| Errors | Unauthorized |

### 12.11 DELETE `/api/v1/me/sessions/{id}`

| Item | Value |
| --- | --- |
| Purpose | Revoke one user session |
| Authentication | Required |
| Authorization | Current user owns session |
| Headers | `Authorization` |
| Path Parameters | `id` |
| Response | Session revocation confirmation |
| Status Codes | `204`, `401`, `403`, `404` |
| Validation | Session ID must exist and belong to current user |
| Errors | Unauthorized, forbidden, session not found |

### 12.12 GET `/api/v1/roles`

| Item | Value |
| --- | --- |
| Purpose | List roles |
| Authentication | Required |
| Authorization | `role.read` |
| Headers | `Authorization`, optional `X-School-Id` |
| Query Parameters | `scope`, `status`, `schoolId` |
| Response | Role list |
| Status Codes | `200`, `401`, `403` |
| Validation | Tenant role query requires school context |
| Errors | Unauthorized, forbidden |

### 12.13 POST `/api/v1/roles`

| Item | Value |
| --- | --- |
| Purpose | Create tenant or platform role |
| Authentication | Required |
| Authorization | `role.create` |
| Headers | `Authorization`, `Content-Type`, optional `X-School-Id` |
| Request Body | `name`, `code`, `scope`, optional `description`, `permissionIds` |
| Response | Created role |
| Status Codes | `201`, `400`, `401`, `403`, `409` |
| Validation | Code must be unique in scope |
| Errors | Invalid request, forbidden, duplicate role |

### 12.14 GET `/api/v1/permissions`

| Item | Value |
| --- | --- |
| Purpose | List available permissions |
| Authentication | Required |
| Authorization | `permission.read` |
| Headers | `Authorization` |
| Query Parameters | `module`, `scope`, `status` |
| Response | Permission list grouped by module |
| Status Codes | `200`, `401`, `403` |
| Validation | Query parameters must be valid |
| Errors | Unauthorized, forbidden |

### 12.15 POST `/api/v1/users/{id}/roles`

| Item | Value |
| --- | --- |
| Purpose | Assign role to user |
| Authentication | Required |
| Authorization | `user.role.assign` |
| Headers | `Authorization`, `Content-Type`, optional `X-School-Id` |
| Path Parameters | `id` user ID |
| Request Body | `roleId`, optional `schoolId`, optional `expiresAt` |
| Response | User role assignment |
| Status Codes | `201`, `400`, `401`, `403`, `404`, `409` |
| Validation | Role scope must match assignment scope |
| Errors | Invalid request, forbidden, user not found, role not found, duplicate assignment |

---

## 13 Common Errors

| Code | HTTP Status | Meaning |
| --- | --- | --- |
| `AUTH_INVALID_CREDENTIALS` | 401 | Email or password is invalid |
| `AUTH_ACCOUNT_LOCKED` | 423 | Account is locked |
| `AUTH_TOKEN_EXPIRED` | 401 | Token has expired |
| `AUTH_TOKEN_REVOKED` | 401 | Token has been revoked |
| `AUTH_REFRESH_REUSE_DETECTED` | 409 | Old refresh token was reused |
| `AUTH_FORBIDDEN` | 403 | User lacks required permission |
| `VALIDATION_ERROR` | 400 | Request validation failed |
| `RESOURCE_NOT_FOUND` | 404 | Requested record was not found |
| `DUPLICATE_RESOURCE` | 409 | Unique constraint conflict |
| `RATE_LIMITED` | 429 | Too many requests |

---

## 14 References

| Document | Location |
| --- | --- |
| Epic Overview | `docs/09-Backend/Identity-Authentication/Epic-01-Identity-Authentication.md` |
| Sprint Plan | `docs/09-Backend/Identity-Authentication/Sprint-01-Plan.md` |
| Identity & RBAC Schema | `docs/07-Database/Identity-RBAC-Phase-1.md` |

---

## 15 Conclusion

This API specification defines the Phase 1 Identity & Authentication endpoints. It must be reviewed before backend implementation starts.
