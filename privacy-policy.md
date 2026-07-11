# Novelist — Privacy Policy

**Effective date:** July 12, 2026

Novelist is an AI-assisted story-writing app: you pick a genre and a few options, create characters, and Novelist writes chapters with you — plus a bundled "Discover" library of ready-to-read stories. This policy explains, in plain English, what data the app handles and the choices you have.

---

## 1. Who we are

Novelist is an iOS app developed and operated by **Abdullah Al Hadi** (publishing as Mukashi) ("we", "us"). For the purposes of the EU/UK/EEA General Data Protection Regulation (GDPR) and the California Consumer Privacy Act (CCPA/CPRA), Abdullah Al Hadi is the **data controller** for personal data handled through the app. For any privacy question, contact **mukashi.dev@gmail.com**.

---

## 2. Data we collect

### Stays only on your device — never sent to us

Everything below is stored locally on your device using Apple's SwiftData framework and iOS user defaults. **We have no server that stores your stories, and we cannot read them.**

- **Your stories and chapters** — titles, prose, chapter order, and export history.
- **Characters** you create — names, archetypes, and descriptions.
- **Story memory** — the running summary Novelist keeps of a story so later chapters stay consistent.
- **Discover reading progress** — which bundled stories you've opened or finished.
- **Settings** — theme, language, reader preferences, and onboarding state.
- **Purchase/entitlement state** — whether Novelist Pro is currently active on this device.

Uninstalling the app removes all of it. If you have iCloud Backup enabled, Apple includes this data in your encrypted iCloud backup — that backup is between you and Apple; we have no access to it.

### Anonymous account

On first launch, Novelist creates an **anonymous account** for your device using Firebase Authentication's anonymous sign-in. **No name, email address, or password is ever requested or collected.** This anonymous account exists so our backend can:

- Track your entitlement (whether Novelist Pro is active) so it can be restored if you reinstall or switch devices while signed into the same anonymous session.
- Meter free-tier usage — Novelist offers a limited number of free chapter generations and regenerations before prompting you to subscribe.
- Record how much backend/AI usage your account has consumed per day, so we can operate fair usage limits and decide which AI model tier (see below) handles your requests.

This identifier is a random string tied to your device/app install, not to you personally, and cannot be used by us to look up your name, email, or any other directly-identifying information — we don't have any to look up.

### Sent to our backend, and forwarded to Anthropic's AI models

When you generate or regenerate a chapter, redirect the plot, or use Fine-Tune steering, the app sends the following to our backend (Firebase Cloud Functions), which forwards it to **Anthropic's Claude AI models** (a "Sonnet" model, or a faster "Haiku" model depending on your usage tier) to write the requested text:

- The genre, tone, point of view, ending style, pacing, target audience, and writing-style options you selected.
- The names, archetypes, and descriptions of any characters you created for that story.
- The previous chapters of that story (so new chapters stay consistent with what came before).
- Any custom instructions you type into **Fine-Tune** or **Redirect Plot**.

This content is associated only with your anonymous account ID described above — never with a name or email, because we don't collect one. Anthropic processes this content to generate the requested text; per Anthropic's API terms, content submitted through its API is not used to train Anthropic's models by default. We do not send your character/story content to any other AI vendor, and Discover's bundled library stories are pre-written and never sent anywhere.

### Firebase Analytics

We use Firebase Analytics (configured **without** advertising-identifier support — no IDFA, no ad personalization, no cross-app tracking, no ads) to understand feature usage. It collects:

- A per-install device identifier (a Firebase app-instance ID) that resets if you reinstall.
- Device model, OS version, app version, language, and country (derived from IP, then discarded by Google).
- Categorical feature-usage events — for example: a screen was viewed (by name), a story was generated or regenerated (genre only), a chapter was added, a story was exported (format only), a Discover genre or collection was opened, the free-tier paywall was shown (with a reason code), a subscription plan was viewed/selected, a purchase started/completed/cancelled/failed (product ID and, on failure, a reason code — never price, receipt, or payment details), a purchase was restored, a setting was changed (theme/language — the new value only), or the App Store review prompt was shown/accepted/declined.

**We never send** the text of your stories, character descriptions, Fine-Tune/Redirect Plot instructions, or any other creative content to Analytics — only the categorical events listed above. **We do not request App Tracking Transparency** and never read your device's advertising identifier. **We never tie an analytics event to your name or email**, because we don't have one.

Novelist does **not** use Firebase Crashlytics or any other crash-reporting or third-party analytics/advertising SDK.

### Firebase App Check

Novelist uses Firebase App Check to confirm that requests to our backend come from a genuine, unmodified copy of the app (anti-abuse). App Check tokens are attestations about the app binary and device, not personal data.

### In-app purchases (Novelist Pro)

Novelist offers **Novelist Pro**, an auto-renewing subscription (weekly, monthly, or yearly) handled entirely through Apple's StoreKit 2. **Apple processes the payment** — your card and billing details are never seen by the app or by us. The app stores locally whether Pro is currently active. As described above, Analytics receives only non-financial purchase events (product identifier and outcome) — never your payment method, receipt, or transaction ID. **Restore Purchases** asks Apple (not us) which products are tied to your Apple Account.

### Export and sharing

Novelist can export a story as EPUB, PDF, or plain text and hand it to iOS's standard share sheet. Where that file goes next (Files, Mail, Messages, AirDrop, a third-party app, etc.) is entirely your choice — we never receive a copy.

### Narration

The "Listen" feature uses Apple's on-device `AVSpeechSynthesizer` (the system text-to-speech engine already built into iOS). Narration happens entirely on your device — no story text is sent anywhere to produce it, and there is no cloud text-to-speech vendor involved.

---

## 3. Permissions the app asks for

Novelist does not request access to the camera, microphone, photo library, contacts, location, motion data, or notifications. It has no need for any of them.

---

## 4. How we use this data

- **Local data** (stories, characters, settings) powers the app's core features for you and is not used for anything else.
- **Your anonymous account** lets us apply free-tier limits fairly, keep your Pro entitlement in sync across reinstalls, and route requests to the right AI model tier.
- **Story/character content sent to Anthropic** exists solely to generate the chapter, plot redirection, or fine-tuned continuation you asked for.
- **Firebase Analytics** tells us, in aggregate, which features are used and where people get stuck (e.g., at the paywall) so we can decide what to fix or improve. We look at counts, not individuals.

We do **not** sell your personal information, and we do not share it for cross-context behavioural advertising (as those terms are defined under the CCPA/CPRA). We do not build advertising profiles or share data with data brokers.

---

## 5. Who we share data with

- **Google LLC** (and, for EEA/UK/Swiss users, Google Ireland Limited) operates **Firebase** — Authentication, Cloud Functions, App Check, and Analytics — as our service provider, under the [Firebase Data Processing Terms](https://firebase.google.com/terms/data-processing-terms) and [Google Privacy Policy](https://policies.google.com/privacy).
- **Anthropic, PBC** processes the story/character content described in Section 2 through its Claude API to generate text, under [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy) and [Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms).
- **Apple Inc.** processes your in-app purchases under the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
- We may also disclose information where required by valid legal process.

No other third-party analytics, advertising, or tracking SDK is bundled in the app. These providers primarily process data on servers in the **United States**; for EEA/UK/Swiss users, international transfers rely on Standard Contractual Clauses incorporated into each provider's terms.

---

## 6. How long we keep it

- **Local data** — kept on your device until you delete it or uninstall the app.
- **Story/character content sent for generation** — used to produce the response and not retained by us beyond what's needed to serve that request and to operate short-lived abuse/rate-limit safeguards; Anthropic's retention of API content is governed by its own terms, linked above.
- **Anonymous account and usage-metering data** — retained for as long as your account is active (i.e., the app remains installed and in use), so entitlement and free-tier limits keep working correctly.
- **Firebase Analytics** — retained by Google per Firebase's default event retention (up to 14 months).

---

## 7. Your rights and choices

- **Delete or edit** any story, character, or setting directly in the app; uninstall the app to remove all local data and reset your anonymous account.
- **Turn off analytics system-wide** — iOS **Settings → Privacy & Security → Analytics & Improvements → Share iPhone Analytics**.
- **Access or erasure** under GDPR (EEA/UK), CCPA/CPRA (California), or similar laws — email **mukashi.dev@gmail.com**. Because we don't collect a name or email through the app itself, the most reliable way to reset your data is uninstalling the app, which invalidates your anonymous account and local data.
- **Lodge a complaint** with your local data-protection authority if you're in the EEA, UK, or Switzerland — though we'd appreciate the chance to help first.

---

## 8. Children's privacy

Novelist is a general-audience creative-writing app and is **not directed to children under 13** (or the minimum age in your country). It includes an optional content-tone setting that lets you steer generated stories toward more age-appropriate themes, but this is a creative preference, not a child-directed mode — the app can also generate mature themes (e.g., horror, dark/gritty tone, romance) at your request. We do not knowingly collect personal information from children. If you believe a child has used the app and provided us information, email **mukashi.dev@gmail.com** and we will address it.

---

## 9. Security

- Local data is stored in iOS's app sandbox.
- Data sent to our backend, Anthropic, and Firebase travels over HTTPS (TLS).
- We operate a minimal server footprint by design — no account database of names/emails, no payment data. No method is perfectly secure, but we keep our data footprint deliberately small and will notify you of a breach as required by law.

---

## 10. Changes & contact

If we change this policy, the new version replaces this page and the "Effective date" above is updated; material changes (e.g., a new third-party service, a new category of data) are noted in the app's release notes. This policy applies alongside our [Terms of Use](terms.html).

Questions, requests, or complaints: **mukashi.dev@gmail.com**.

---

© 2026 Abdullah Al Hadi (Mukashi). Novelist.
