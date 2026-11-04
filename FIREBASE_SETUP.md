# Insurance Dashboard — Firebase Team Access (Preparation)

This branch is a safe preparation snapshot. The existing dashboard remains unchanged and uses localStorage until the Firebase integration is implemented and tested. Do not deploy this branch as a shared production dashboard yet.

## Approved requirements
- Google Sign-In for each pharmacist.
- New users are pending until approved by the sole administrator.
- Approved pharmacists can read, create and edit prescriptions.
- Only administrator can delete prescriptions and approve/revoke accounts.
- Shared Cloud Firestore storage, with server-enforced access control.

## Setup sequence
1. Create Firebase project; register a Web app; enable Google in Authentication.
2. Add authorized hosting domain under Authentication settings.
3. Create Cloud Firestore; configure Security Rules (never use open test rules in production).
4. Set the administrator Firebase Authentication UID through a trusted one-time setup, not a client-side email check.
5. Implement Google sign-in, pending access requests, approval/revocation, and denied/pending UI.
6. Replace localStorage persistence with Firestore reads/writes and realtime subscriptions. Do not auto-upload sample initialPatients or browser-local patient data.
7. Enforce admin-only deletion in Firestore rules and in UI; protect user-role changes against self-promotion.
8. Add immutable audit metadata and test with admin, approved pharmacist and pending/blocked user.
9. Export and back up existing browser-local prescriptions before migration; import only after deliberate review.

## Current app observations
- The main page is index.html, a standalone HTML application.
- Data currently uses localStorage key insurance_patients_db.
- Initial sample patient records exist in the code. Never automatically publish them to shared Firestore.
- Existing delete action calls executeDelete() and currently removes data from the browser only.

## Data protection
Prescription data can be sensitive. Minimize personal data, restrict access by approved user UID, avoid analytics or public indexing, and agree on backup and retention policies before production use.
