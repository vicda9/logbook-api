# Security and Non-Functional Requirements

Each requirement should be testable: "passwords are hashed with Argon2id" beats "passwords are secure".
Priority: **Must** = v1, **Should** = v1 if time allows, **Could** = later.

## Authentication (SR-01 to SR-09)
| ID | Priority | Requirement |
|----|----------|-------------|
| SR-01 | Must | Passwords are 12 to 64 characters. No composition rules (like "must include a symbol"), per NIST SP 800-63B. |
| SR-02 | Must | Passwords are hashed with Argon2id. Plain-text passwords are never stored, logged, or returned by the API. |
| SR-03 | Must | After 5 failed password attempts, password log-in is disabled for that account. The user can only log in by email link until they succeed. |
| SR-04 | Must | Email links are single-use, expire after 15 minutes, are generated with a cryptographically secure random source, and are stored hashed. |
| SR-05 | Must | Log-in and email-link responses look the same whether or not the account exists, so attackers can't discover registered emails. |
| SR-06 | Must | Email sending is rate limited per email address and per IP address. |
| SR-07 | Should | New passwords are checked against a list of known breached passwords. |

## Sessions (SR-10 to SR-19)
| ID | Priority | Requirement |
|----|----------|-------------|
| SR-10 | Must | Access tokens (JWT) expire after 15 minutes. |
| SR-11 | Must | Refresh tokens expire after 7 days without use. They are replaced with a new one every time they are used (rotation). |
| SR-12 | Must | Refresh tokens are stored hashed on the server, so they can be revoked. |
| SR-13 | Must | Logging out revokes that device's refresh token. "Log out of all devices" revokes all of them. |
| SR-14 | Should | If an old, already-rotated refresh token is used again, all of that user's sessions are revoked (it likely means the token was stolen). |

## Authorization and data isolation (SR-20 to SR-29)
| ID | Priority | Requirement |
|----|----------|-------------|
| SR-20 | Must | Every request for a check-in verifies it belongs to the logged-in user. Requests for someone else's check-in return 404 (not 403, which would confirm it exists). |
| SR-21 | Must | There is no admin role or endpoint that can read check-in content. Admin tools only see accounts and system health. |
| SR-22 | Must | Direct database access is limited to the deployment and one operator account, and access is logged. |
| SR-23 | Must | Automated tests prove user A cannot read, edit, or delete user B's check-ins. |
| SR-24 | Must | Check-ins and users use random IDs (UUID), not sequential numbers. Sorting always uses timestamps. |

> **Known limit (v1):** SR-21 and SR-22 make content unreadable through the app, not mathematically impossible. Someone with the database credentials could still read rows. True "no one can read it" needs end-to-end encryption, which is out of scope for v1.

## Data protection (at rest, in transit, sent to third parties)

## Secrets management

## Logging, monitoring, and audit

## Supply chain and CI/CD

## Privacy and retention
