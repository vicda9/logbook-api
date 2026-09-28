# Functional Requirements

Priority: **Must** = v1, **Should** = v1 if time allows, **Could** = later.
IDs are grouped by tens so new requirements can slot in without renumbering.

## Accounts and auth (FR-01 to FR-09)
| ID | Priority | Requirement |
|----|----------|-------------|
| FR-01 | Must | A user can sign up with an email and password. |
| FR-02 | Must | A user can log in and receive an access token. |
| FR-03 | Must | A user can log out, and their token stops working. |
| FR-04 | Should | A user can change their password. |
| FR-05 | Must | A user can log in with a one-time email link (magic link), and reset their password that way. |
| FR-06 | Must | After a failed password attempt, the log-in page offers the email link option. |
| FR-07 | Must | A user can log out of all devices at once. |

## Check-ins (FR-10 to FR-19)
| ID | Priority | Requirement |
|----|----------|-------------|
| FR-10 | Must | A user can create a check-in with: mood, sleep, rest, movement, and an optional note. Mood is required; every other field can be skipped. |
| FR-11 | Must | Mood is one of: happy, calm, grateful, tired, anxious, sad, angry, stressed. |
| FR-12 | Must | Sleep is entered as hours, or as sleep and rise times (hours are calculated). |
| FR-13 | Must | Rest is a whole number from 1 to 5. |
| FR-14 | Must | Movement is one of: none, movement, stretch, yoga. |
| FR-15 | Must | The note is optional, max 280 characters. |
| FR-16 | Must | A user can make more than one check-in per day. Each one is timestamped with the device's local time and time zone. |
| FR-17 | Must | A user can list their own check-ins, newest first, a page at a time. |
| FR-18 | Should | A user can edit or delete one of their check-ins. |
| FR-19 | Could | A user can filter their check-ins by date range. |

## Data rights (FR-20 to FR-29)
| ID | Priority | Requirement |
|----|----------|-------------|
| FR-20 | Must | A user can export all of their data as JSON. |
| FR-21 | Must | A user can delete their account. All their data is permanently deleted after a 7-day grace period. |
| FR-23 | Must | During the grace period, a user can cancel the deletion and restore their account. |
| FR-24 | Must | Before confirming deletion, the user is offered a full export of their data. |
| FR-22 | Could | A user can export their data as CSV. |

## Web page (FR-30 to FR-39)
| ID | Priority | Requirement |
|----|----------|-------------|
| FR-30 | Must | A sign-up and log-in page. |
| FR-31 | Must | A check-in form that works well on a phone screen. |
| FR-32 | Should | A page listing past check-ins. |
| FR-33 | Could | An optional timer per question, to encourage quick answers (see 05-ux-notes.md). |

## Decisions log
- Mood required, other fields skippable: keeps check-ins quick (see UX principle in 05-ux-notes.md).
- Note limit 280 characters: say what comes to mind, don't dwell. Also data minimization.
- Check-in time comes from the device, not the server.
- Account deletion has a 7-day grace period, with an export offered first.
- Email is in v1: magic-link log-in replaces hard lockouts (see SR-03).
