# SpeakUp Kids — Privacy Policy

**Effective date:** 2026-06-03
**Last updated:** 2026-06-03

SpeakUp Kids is an Android and iOS mobile app that helps children ages 5–14 practise speaking on camera. We are built around a simple promise: a kid's recording stays on the kid's device. This Privacy Policy explains exactly what data we collect, what we do with it, and the choices you have.

If you have a question that this policy doesn't answer, email us at **jacobsproject101@gmail.com** or WhatsApp **+60 16-322 5065**.

## 1. Who we are

SpeakUp Kids is operated by Jacob Ampari (`amparijacob@gmail.com`), based in Malaysia. We are the data controller for the personal information described below.

## 2. The three groups of people who use SpeakUp Kids

The app behaves differently depending on who is using it. We have separate disclosures for each group.

### 2.1 Students (children — accounts created on the device, no sign-in)

A child's profile is created locally on the device with a nickname, age band (5–7, 8–10, or 11–14), and a chosen mascot. We store the following on the device only, in private app storage:

- Nickname, age band, mascot choice, coins, streak, total session count, earned badges
- Daily-reminder time (if a parent sets one)
- A list of session records (which topic was practised, how long, when)
- The actual video and audio files of each recording

**Children's recordings are never uploaded to our servers.** They are stored only in the app's private storage on the device. They are never analysed, never scored, never shared with anyone outside that device — unless an adult explicitly taps the Share button on a specific recording, which opens the operating system's native share sheet (e.g. WhatsApp, Email) so the adult chooses where to send it.

### 2.2 Mentors (parents, teachers, school admins — signed in)

If you sign in as a Mentor we collect:

- Your email address (used as your sign-in identifier)
- A display name you choose
- The role you signed up with (parent / teacher / school admin)
- The school you belong to (for teacher / admin roles)

This is stored in Google Firebase (Cloud Firestore + Firebase Authentication), in the Singapore region. We use this so you can sign in across devices and manage your students. We do not sell, rent, or share this information with anyone.

### 2.3 Schools (B2B accounts created by school admins)

If your school subscribes:

- School name, city, state, country, billing email
- Optional school logo (uploaded as an image, stored in Firebase Cloud Storage)
- List of classes, teachers, and enrolled student nicknames + age bands
- Per-student session metadata: which topic was practised, how long, when (NOT the recording itself)

The actual videos and audio of children in a B2B school never leave the kid's device — only metadata (topic ID, duration, timestamp) syncs back to Firestore so the teacher can see "Maya practised today."

## 3. Third-party services we use

| Service | What it does | Data it sees | Data residency |
|---|---|---|---|
| Google Firebase (Authentication, Firestore, Cloud Storage) | Mentor sign-in, school + class data, school logos | Mentor email + name + role; school metadata; class roster | Singapore |
| Google AdMob | One non-personalised ad on parent-initiated share, free tier only | None tied to a child; AdMob's standard non-personalised ad signals only | Google global |
| Firebase Crashlytics | Crash reports for stability | Anonymous device model, OS version, and the crash stack trace | Google global |
| Firebase App Check | Blocks fraudulent traffic to our backend | App attestation token only | Google global |

We do not run any other third-party SDKs: no Facebook SDK, no behavioural tracking pixels, no data brokers, no third-party analytics, no AI scoring services.

## 4. Advertising — and why it doesn't reach children

SpeakUp Kids does not show ads inside the kid's practice flow. There are NO ads on the home screen, no ads during recording, no ads in the reward or belt-up celebrations, no ads on the topic library — anywhere a child taps.

On the free tier, one ad plays at one specific moment: **when an adult taps the Share button on a recording**, an interstitial ad shows in the share-time confirmation flow, and after the adult dismisses it, the operating-system share sheet opens. The ad is shown to the adult who initiated the share, never to a child.

Because the app is designed for children, we use Google AdMob in **Tag For Child-Directed Treatment** mode (USA COPPA) plus **Tag For Under Age Of Consent** mode (EU GDPR-K). Both modes restrict AdMob to non-personalised, family-safe demand only. The maximum allowed ad content rating is **G**. AdMob does not receive any device identifier tied to a child, does not perform behavioural targeting, and does not retain personal data from these requests.

Premium subscribers and every child enrolled in a B2B school account see zero ads.

## 5. Children's data and COPPA / GDPR-K / PDPA

SpeakUp Kids is designed for children. We adhere to the following:

- **USA Children's Online Privacy Protection Act (COPPA)** — children under 13 may use the app, but we collect no personal information from them. The on-device child profile (nickname + age band + mascot) is not personal information because it never leaves the device, it is not associated with a real identity, and there is no sign-in.
- **EU General Data Protection Regulation, Children's Provisions (GDPR-K, Articles 6 + 8)** — for any data that is collected (Mentor accounts), we require a verifiable adult sign-up. The kid-facing flow on the same device collects no personal information.
- **Malaysia Personal Data Protection Act 2010 (PDPA)** — the same standards apply for Malaysian users.

There is no child-directed sign-in flow, no child-directed in-app chat, no child-directed friend-list, no public profiles, no leaderboards, no behavioural targeting of children. Every sensitive control (data export, data deletion, daily reminder settings) is behind a Mentor sign-in gate.

## 6. Permissions the app requests

- **Camera + Microphone** — used only on the recording screen when a child taps the record button. Required so the child can practise on camera. Released as soon as the recording stops.
- **Notifications** — used only if a parent sets a daily reminder. Releases the schedule as soon as the parent turns the reminder off.
- **Photos / Media library** — used only when a school admin uploads a school logo from their gallery.

We never request location, contacts, calendar, SMS, call logs, or background-mic.

## 7. Data retention and deletion

- **On-device kid data** (profile, recordings, session history) — kept until the parent taps **Mentor Dashboard → Privacy & data → Delete all data**, which permanently wipes profile, recordings, video files, and analytics from the device.
- **Mentor account data** in Firebase — kept while the account is active. Email us at **jacobsproject101@gmail.com** to request deletion; we'll purge the Firestore documents and your Firebase Auth record within 30 days.
- **School data** in Firebase — kept while the school subscription is active. School admins can request deletion at any time.
- **Crash reports** — retained per Firebase Crashlytics' standard retention (90 days for full crashes, 5 years for aggregate counts).

## 8. Your rights

You have the right to:

- **Access** the data we hold about you
- **Correct** it if it's wrong
- **Delete** it
- **Export** it in a portable format (we export as JSON on request)
- **Object** to processing for any reason

Email **jacobsproject101@gmail.com** to exercise any of these rights. We'll respond within 30 days.

## 9. Where data is stored

Mentor and school data is stored in Google Firebase, region **asia-southeast1** (Singapore). Crash reports and App Check tokens may transit Google's global infrastructure. We never sell, transfer, or share data outside the services listed in section 3.

## 10. Children's data sent to third parties — confirmation

For absolute clarity: SpeakUp Kids does **not** send any data identifying a child (nickname, age band, recording, voice sample, photo) to any third party at any time. The only data we send anywhere is mentor account information and school metadata, all of which is created by an adult who has signed in with an email address.

## 11. Changes to this policy

When this policy changes, we update the "Last updated" date at the top, and for material changes we will notify signed-in Mentors via email. Continuing to use the app after a change means you accept the new version.

## 12. Contact

- Email: **jacobsproject101@gmail.com**
- WhatsApp: **+60 16-322 5065**
- Mail: Jacob Ampari, Kuala Lumpur, Malaysia

If you have a complaint we cannot resolve, you have the right to lodge a complaint with the Malaysian Personal Data Protection Department (JPDP) or your local data protection authority.
