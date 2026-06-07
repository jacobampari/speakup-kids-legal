---
title: SpeakUp Kids — Delete your account
---

# Delete your SpeakUp Kids account

**Effective date:** 2026-06-07

You can ask us to delete your SpeakUp Kids account and the personal data associated with it at any time. This page tells you how to do that, what gets deleted, and what's retained for legal reasons.

## Two ways to delete

### 1. From inside the app (kid profile + on-device data — instant)

On the device where you use SpeakUp Kids:

1. Open the app and tap **Mentor**
2. Sign in if prompted
3. **Mentor Dashboard → Privacy & data → Delete all data**
4. Confirm

This permanently removes the kid profile, all recordings, all session history, analytics, and notification schedules from this device. It runs without our involvement and cannot be reversed once confirmed.

### 2. By email (Mentor account in Firebase — requires our team)

If you signed in as a Mentor (parent, teacher, or school admin) we also store your account in Firebase (email + display name + role). To delete that, email us:

**Subject:** `Delete my SpeakUp Kids account`
**To:** **jacobsproject101@gmail.com**
**Include in the body:**
- The email address you signed in with
- (Optional) The name of your school if you're an admin

We respond within **3 business days** and complete deletion within **30 calendar days**. The 30-day window lets us reverse accidental requests if you tell us within a week.

## What gets deleted

When we process your request:

- Your Firebase Authentication record (email, password hash, last sign-in)
- Your Firestore user document (display name, role)
- If you're a school admin: the school document, all classes, all student records (nickname + age band)
- If you're a teacher: your link to the school
- All session metadata in Firestore that referenced your account

## What's retained, and why

- **Anonymous crash reports** in Firebase Crashlytics — these contain no personal identifier and are retained per Google's standard retention (90 days for full crashes, 5 years for aggregate counts). They can't be tied back to you after deletion.
- **Anonymous aggregate analytics** — daily active counts and similar metrics, all already anonymous. Cannot be reverse-linked to an individual.
- **Legal/financial records** — if you held a paid subscription, billing records are retained for 7 years per Malaysian tax law.

## Children's data

If you're a parent and your child has a kid profile on a device you control, the in-app delete (option 1) is the right path — kid data never leaves the device, so there's nothing on our servers to delete.

For B2B accounts where a school has enrolled students, only the **school admin** can request bulk deletion of the school's student records via option 2.

## Other rights

You also have the right to **access** the data we hold about you, **correct** it if it's wrong, **export** it in a portable JSON format, and **object** to processing. Email **jacobsproject101@gmail.com** for any of these.

## Contact

- Email: **jacobsproject101@gmail.com**
- WhatsApp: **+60 16-322 5065**
- Mail: Jacob Ampari, Kuala Lumpur, Malaysia
