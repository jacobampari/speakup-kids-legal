# Designed for Families — compliance audit

Reference: https://support.google.com/googleplay/android-developer/answer/9893335

Status as of 2026-06-03 against the SpeakUp Kids release build (`1.0.0+1`). Each row maps a specific policy clause to whether the app currently complies, the evidence in the codebase, and any open item we have to address before submission.

Legend: ✅ compliant · ⚠️ partial / needs disclosure · ❌ non-compliant (blocker)

---

## 1. App content and behaviour

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 1.1 | App's primary audience is children | ✅ | Curriculum explicitly age-banded 5–7, 8–10, 11–14. Kid mode is the default experience after onboarding. |
| 1.2 | No sexually explicit, violent, drug-related, or otherwise inappropriate content | ✅ | All 68 seed + advanced + seasonal topics reviewed. Content is age-appropriate practice prompts. |
| 1.3 | No content that promotes hate, discrimination, or bullying | ✅ | Topic curriculum is encouragement-only. No competitive language. |
| 1.4 | App does not allow children to communicate with strangers | ✅ | Zero chat, zero in-app social, zero "find friends." Sharing is OS share sheet only, gated by 3-tap parent consent dialog. |
| 1.5 | No misleading content about child-safety features | ✅ | Privacy policy now matches app reality (share-time ads disclosed). |

## 2. Ads and in-app purchases

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 2.1 | Ads must not be disruptive, deceptive, or interfere with normal app use | ✅ | Only one ad placement: a single interstitial when the parent taps Share. Not shown during kid-facing flow. |
| 2.2 | Ad content must be appropriate for children | ✅ | AdMob `tagForChildDirectedTreatment: yes` + `tagForUnderAgeOfConsent: yes` + `maxAdContentRating: G`. Code: `lib/services/ads_service.dart`. |
| 2.3 | No interest-based advertising / behavioural targeting of children | ✅ | Tag For Families mode is the AdMob mechanism that enforces this; we set it before the first ad request. |
| 2.4 | Ad-related disclosures must be clear in the privacy policy and listing | ✅ | `legal/privacy.md` §4 explicitly describes the share-time placement and the AdMob mode. Store listing §"AD AND DATA POLICY" repeats it. |
| 2.5 | In-app purchases must be guarded against accidental child purchases | ⚠️ | We do not currently expose IAP — premium is purchased via Play Billing only, which has its own parent-gate (Play's built-in "Require authentication for purchases" setting). When we wire premium in v1.1, the purchase prompt must sit behind the math gate. **TODO before v1.1.** |
| 2.6 | Listing description must accurately disclose whether the app has ads | ⚠️ | Store listing says "one non-personalised ad shows when a parent taps Share." Verify Play Console "Contains ads" flag is set to YES during upload. **TODO at upload time.** |

## 3. Data practices

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 3.1 | App must not collect personally identifiable information from children | ✅ | Kid mode collects only on-device nickname (not real name required), age band, mascot. No sign-in for kids. Nothing leaves the device. |
| 3.2 | App must obtain verifiable parental consent if collecting any data from children | ✅ | Not applicable — we don't collect data from children. Mentor sign-in (which does collect data) is gated by the math problem + Firebase Auth for adults. |
| 3.3 | App must not contain SDKs whose use would put it out of compliance | ✅ | Audited SDKs: `firebase_*` (compliant), `google_mobile_ads` (TFF mode), `share_plus` (OS native), `flutter_local_notifications` (no data collected). No Facebook SDK, no third-party analytics, no data brokers. |
| 3.4 | App must declare data practices via Data Safety form | ⚠️ | Draft answers in `legal/data_safety.md`. **TODO submit at upload time.** |
| 3.5 | App must link to a privacy policy from the Play Console listing and from inside the app | ⚠️ | In-app screen exists at `/parent/privacy`. Public URL pending — Jacob needs to host `legal/privacy.md` (see `legal/README.md`). **TODO before upload.** |

## 4. Permissions

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 4.1 | Request only the minimum permissions needed | ✅ | Requested: CAMERA, RECORD_AUDIO, POST_NOTIFICATIONS (13+), SCHEDULE_EXACT_ALARM, USE_EXACT_ALARM, RECEIVE_BOOT_COMPLETED. Each is justified in §6 of the privacy policy. |
| 4.2 | Sensitive permission prompts must be triggered by a clear user action | ✅ | Camera + mic prompt fires inside `PermissionsScreen` after the onboarding flow has explained why. Notifications prompt fires when parent taps "Set a time" on the reminder tile. |
| 4.3 | Background location, contacts, SMS, call log are forbidden | ✅ | Not requested. |
| 4.4 | Foreground service usage must be declared | ✅ | We don't use any foreground services. |

## 5. App design and behaviour

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 5.1 | Age-appropriate UI: no scoring, no leaderboards, no public profiles | ✅ | Belts measure attendance, never quality. No leaderboards, no friends list. CLAUDE.md product rule #2 prohibits AI judging kids; enforced. |
| 5.2 | No misleading rewards / dark patterns aimed at kids | ✅ | Belts are deterministic by session count. No surprise mechanic. No paid lootboxes. |
| 5.3 | No bait-and-switch monetisation | ✅ | Free tier ships every topic + every belt. Premium removes watermark and ads only; no functional gate. |
| 5.4 | App must function offline for primary use cases | ✅ | Kid mode works fully offline. Only Mentor sign-in + B2B class sync need connectivity. |
| 5.5 | No links to websites or social media that aren't kid-appropriate | ✅ | Audited: in-app links go to Mentor Dashboard sub-screens (Privacy, Data, Daily Reminder), the printable certificate share, and the OS share sheet. No outbound links to social platforms from inside the kid flow. |

## 6. Operational

| # | Policy clause | Status | Evidence / notes |
|---|---|---|---|
| 6.1 | Target audience declared correctly in Play Console | ⚠️ | Will declare 5–14 (multiple age groups). **TODO at upload time.** |
| 6.2 | Content rating (IARC) completed | ⚠️ | Expect "Everyone" / "PEGI 3." **TODO at upload time.** |
| 6.3 | Designed for Families programme enrolment | ⚠️ | Optional but recommended. Adds the "Teacher Approved" lane eligibility. **Apply after first internal track is live.** |
| 6.4 | App Store category set to Education / Educational | ✅ | Documented in `legal/play_store_listing.md`. |
| 6.5 | Privacy policy URL on the listing must be live and accessible | ⚠️ | Pending hosting (see 3.5). |

---

## Open items the audit found (rolled up)

These are the only items not in a ✅ state. Each maps to either an existing task or a step that happens at Play Console upload time.

1. **Privacy policy URL** — must be live and public before upload. Owner: Jacob. Tracked in #140.
2. **Data Safety form answers** — drafted but not yet submitted. Owner: Jacob (clicks through), me (drafts answers). Tracked in #142.
3. **"Contains ads" flag** in Play Console must be set to YES. Owner: Jacob at upload time. Add to D2-D5 checklist.
4. **Target audience age groups** declared 5–7, 8–10, 11–14 (multiple). Owner: Jacob at upload time.
5. **Content rating IARC** questionnaire. Owner: Jacob at upload time.
6. **Premium IAP gate** — purchase prompt must sit behind the math gate when v1.1 wires it. Owner: me, for v1.1.

## Items NOT flagged (worth knowing)

- Crashlytics is fine for kids apps — it's a stability tool, not a profiler. Allowed under Families Policy.
- App Check is fine — it's an anti-abuse mechanism, not data collection.
- Firebase Auth is fine — it only authenticates adult mentors, never children.
- AdMob via Tag For Families is the canonical Google-approved ad path for kids apps. No other configuration is acceptable.

## Audit conclusion

**No blockers.** Six items are "pending at upload time" — none require code changes before submission. The app is structurally compliant with Google's Designed for Families policy as written.

Last reviewed: 2026-06-03.
