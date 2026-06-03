# Play Console — Data Safety form answers

Submit these answers via Play Console → App content → **Data safety**. Wrong answers here are a high-rejection-risk item AND can trigger post-launch enforcement (app pulled from store, listings flagged). Every claim here must match what `privacy.md` says AND what the code actually does.

If you change any of the following after launch, you MUST update this form within 14 days per Play policy:
- Add or remove a third-party SDK
- Start collecting a new data type (e.g. add the email parent-invite flow)
- Change what data is shared with whom
- Change retention rules

---

## Form section 1: Data collection and security

### Q: Does your app collect or share any of the required user data types?

**Answer: Yes**

(We collect Mentor email and the on-device kid profile metadata. Even though the kid profile never leaves the device, Play counts it as "collected" because it's stored persistently on the device by our app.)

### Q: Is all of the user data collected by your app encrypted in transit?

**Answer: Yes**

All Firestore + Storage + Auth + Crashlytics traffic uses TLS 1.2+. The Firebase SDK does not allow plain HTTP. No data leaves the device unencrypted.

### Q: Do you provide a way for users to request that their data be deleted?

**Answer: Yes**

- On-device data: Mentor Dashboard → Privacy & data → Delete all data wipes the kid profile + all recordings + analytics + notification schedules.
- Mentor account: email `jacobsproject101@gmail.com` and we delete the Firebase Auth user + Firestore docs within 30 days.
- This is documented in `legal/privacy.md` §7.

---

## Form section 2: Data types collected — declare each

For each data type, you'll see four questions. The pattern repeats; answers below.

### 2.1 Personal info → Name

- **Collected?** Yes (Mentor display name only)
- **Shared with third parties?** No
- **Processing reason(s):** App functionality, Account management
- **Optional?** User-provided. The mentor types it when they sign up.

### 2.2 Personal info → Email address

- **Collected?** Yes (Mentor email)
- **Shared with third parties?** No (transits Firebase only)
- **Processing reason(s):** App functionality, Account management
- **Optional?** Required (without email no mentor sign-in)

### 2.3 Personal info → User IDs

- **Collected?** Yes (Firebase Auth UID for mentors)
- **Shared with third parties?** No
- **Processing reason(s):** App functionality, Account management
- **Optional?** Required (mechanically tied to Firebase Auth)

### 2.4 Personal info → Other personal info (nickname, age band)

- **Collected?** Yes (kid nickname + age band)
- **Shared with third parties?** No (stored on-device only)
- **Processing reason(s):** App functionality, Personalization
- **Optional?** Required for kid mode (no nickname = no profile)
- **Disclosure note:** Even though stored on-device only, Play asks us to declare it because the app persists it. Source: the kid profile in `ChildProfile.fromJson`.

### 2.5 Photos and videos → Videos

- **Collected?** Yes (recordings made by the kid)
- **Shared with third parties?** No
- **Processing reason(s):** App functionality
- **Optional?** Yes — the user (kid) chooses when to record
- **Disclosure note:** Videos NEVER leave the device. We declare collection because the app saves them in private app storage. If the parent taps Share, the OS share sheet hands the file off to whichever app they choose — that is the user's action, not ours.

### 2.6 Audio files → Voice or sound recordings

- **Collected?** Yes (audio track is inside the MP4)
- **Shared with third parties?** No
- **Processing reason(s):** App functionality
- **Optional?** Yes
- **Same on-device-only disclosure as 2.5.**

### 2.7 App activity → App interactions

- **Collected?** Yes (local analytics events)
- **Shared with third parties?** No
- **Processing reason(s):** Analytics, App functionality
- **Optional?** Required (we log automatically while the parent uses the app — but log is stored on-device only)
- **Disclosure note:** `AnalyticsService` writes to SharedPreferences only. No third-party analytics SDK.

### 2.8 App info and performance → Crash logs

- **Collected?** Yes
- **Shared with third parties?** Yes — **Google Firebase Crashlytics**
- **Processing reason(s):** App functionality (debugging), Analytics
- **Optional?** Required
- **Third-party disclosure:** Crashlytics receives the crash stack trace, device model, OS version, and an anonymous installation ID. No personal information is attached. Configured in `lib/main.dart` after `Firebase.initializeApp`.

### 2.9 App info and performance → Diagnostics

- **Collected?** Yes
- **Shared with third parties?** Yes (Firebase Crashlytics for stability metrics + Firebase App Check tokens)
- **Processing reason(s):** App functionality, Fraud prevention
- **Optional?** Required

### 2.10 Device or other IDs → Device or other IDs

- **Collected?** Yes (Firebase installation ID — anonymous, regenerated on uninstall)
- **Shared with third parties?** Yes (Google Firebase, AdMob)
- **Processing reason(s):** App functionality, Advertising or marketing, Fraud prevention
- **Optional?** Required
- **Advertising disclosure:** AdMob in Tag-For-Families mode receives a non-personalised, non-resettable advertising signal. This is the standard child-directed-treatment mode and does NOT use the Android Advertising ID.

### Everything else — declare "Not collected"

The following data types are NOT collected (do not check these boxes):
- Personal info: address, phone number, race/ethnicity, political views, sexual orientation, religion
- Financial info (all)
- Health and fitness (all)
- Messages (all)
- Photos (photo library access only when uploading a school logo — but the photo itself doesn't leave the device unless it's the logo)
- Files and docs (all)
- Calendar (all)
- Contacts (all)
- App activity: search history, installed apps, other user-generated content
- Web browsing (all)

---

## Form section 3: Security practices

- **Data encrypted in transit?** Yes
- **Users can request data deletion?** Yes
- **Independent security review?** No (small team — answer truthfully)
- **Committed to Play's Family Policy?** Yes
- **Committed to Play's Data Safety Section policy?** Yes

---

## Form section 4: Target audience

- **App's target age groups:** Ages 5–7, 8–10, 11–14 (multiple)
- **App primarily directed at children?** Yes
- **Acknowledge: app cannot use the Android Advertising ID for children?** Yes
- **Acknowledge: app cannot transmit personal/sensitive identifiers from children?** Yes

---

## Form section 5: Government apps & news apps

Not applicable.

---

## Sanity checks before submitting

1. Open the app on a fresh install. Tap through every screen a child or mentor would normally hit. Confirm the data you described above is the only data being touched.
2. Open `lib/services/` and verify no `http` / `dio` / network call we don't know about.
3. Open `pubspec.yaml` and verify the SDK list matches the third parties declared (Firebase, AdMob — nothing else).
4. Read your own `privacy.md` one more time. Every word must hold up.

If anything in those four checks surprises you, **fix it before you submit this form**. Mismatches between Data Safety and reality are how kids apps get pulled from the Play Store.

---

## When to re-run this audit

- Before submitting the very first internal-track build
- Before every Play Console submission where you've added or removed an SDK
- At least annually, even with no changes (Google updates policy)
- Whenever Crashlytics or App Check usage shifts (e.g. adding a new collection)
