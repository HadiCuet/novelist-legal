# Novelist — Privacy Policy

**Effective date:** July 12, 2026

Novelist is an AI-assisted story-writing app: you pick a genre and a few options, create characters, and Novelist writes chapters with you — plus a bundled "Discover" library of ready-to-read stories. This policy explains, in plain English, what data the app handles and the choices you have.

---

## 1. Who we are

Novelist is an iOS app developed and operated by **Abdullah Al Hadi** (publishing as Mukashi) ("we", "us"). For the purposes of the EU/UK/EEA General Data Protection Regulation (GDPR) and the California Consumer Privacy Act (CCPA/CPRA), Abdullah Al Hadi is the **data controller** for personal data handled through the app. For any privacy question, contact **mukashi.dev@gmail.com**.

---

## 2. Data we collect

### An anonymous account (no name, email, or password)

On first launch, Novelist creates an **anonymous account** for your device using Firebase Authentication's anonymous sign-in. **No name, email address, phone number, or password is ever requested or collected.** This anonymous account is a random identifier tied to your app install; we cannot use it to look up who you are, because we hold no directly-identifying information about you. Everything our backend stores (below) is keyed to this anonymous ID.

### On your device

The app keeps a local copy of your content on your device (using Apple's SwiftData framework and iOS user defaults) so it works smoothly and can be read back quickly:

- **Your stories and chapters** — titles and the full chapter text.
- **Characters** in your character library and the running **story memory** Novelist keeps so later chapters stay consistent.
- **Discover reading progress** — which bundled stories you've opened or finished.
- **Settings** — theme, language, reader preferences, and onboarding state.
- **Purchase/entitlement state** — whether Novelist Pro is currently active on this device.

### On our backend (Firebase Cloud Firestore)

Because Novelist generates each chapter on our server and continues your story across sessions, **the story content you create is also stored on our backend** (Google's Firebase Cloud Firestore), keyed to your anonymous account ID. This server-side copy — not just the on-device copy — is where your story lives between chapters. It includes:

- **The story's setup** — the genre, tone, point of view, ending style, pacing, target audience, language, creativity level, and the **premise/idea text** you wrote.
- **Characters you attached to the story** — their names, roles, traits, and descriptions.
- **AI-generated story data** — the outline, title, and topic hashtags Novelist produced for the story.
- **Every chapter's full text**, and the **story "memory"** (a running summary plus tracked characters, world facts, and canon facts used to keep chapters consistent).
- **Per-account operational data** — usage counters (how many chapters you've generated, and daily/hourly counts used for fair-use limits), token/cost totals for the AI generation your account has consumed, and your subscription entitlement (tier, product identifier, and expiry).

Because we operate this backend, **our systems can technically access this stored content** — for example, through the administrative tools we use to run usage limits, prevent abuse, monitor cost, and provide support. It is never linked to your name or email, because we don't collect one. We do not sell it, use it for advertising, or share it with anyone except the service providers in Section 5.

### Sent to Anthropic's AI models to generate text

When you generate or regenerate a chapter, add a chapter, redirect the plot, use Fine-Tune steering, or edit a paragraph, our backend sends the material needed to fulfil that request to **Anthropic's Claude AI models** (a "Sonnet" model for prose, or a faster "Haiku" model for utility and rate-limited fallback). This includes your story setup and characters, the running story memory/summary, the tail of the previous chapter (for continuity), and any custom instructions you type into **Fine-Tune**, **Redirect Plot**, or **Edit paragraph**. Generated and submitted text may also be passed through an automated **content-safety check** (also performed by Claude) before it is returned.

This content is associated only with your anonymous account ID — never with a name or email. Anthropic processes it to generate the requested text and safety result; per Anthropic's commercial API terms, content submitted through its API is not used to train Anthropic's models by default. We do not send your story or character content to any other AI vendor. Discover's bundled library stories are pre-written and are not generated per-user.

### Firebase Analytics

We use Firebase Analytics (configured **without** advertising-identifier support — no IDFA, no ad personalization, no cross-app tracking, no ads) to understand feature usage. It collects:

- A per-install device identifier (a Firebase app-instance ID) that resets if you reinstall.
- Device model, OS version, app version, language, and country (derived from IP, then discarded by Google).
- Categorical feature-usage events — for example: a screen was viewed (by name), a story was generated or regenerated (genre only), a chapter was added, a story was exported (format only), a Discover genre or collection was opened, the free-tier paywall was shown (with a reason code), a subscription plan was viewed/selected, a purchase started/completed/cancelled/failed (product ID and, on failure, a reason code — never price, receipt, or payment details), a purchase was restored, a setting was changed (theme/language — the new value only), or the App Store review prompt was shown/accepted/declined.

**We never send** the text of your stories, your premise/idea, character descriptions, or your Fine-Tune/Redirect Plot/Edit instructions to Analytics — only the categorical events listed above. **We do not request App Tracking Transparency** and never read your device's advertising identifier. Novelist does **not** use Firebase Crashlytics or any other crash-reporting, or any other third-party analytics/advertising SDK.

### Firebase App Check

Novelist uses Firebase App Check (Apple's App Attest) to confirm that requests to our backend come from a genuine, unmodified copy of the app (anti-abuse). App Check tokens are attestations about the app binary and device, not personal data.

### In-app purchases (Novelist Pro)

Novelist offers **Novelist Pro**, an auto-renewing subscription (weekly, monthly, or yearly) handled entirely through Apple's StoreKit 2. **Apple processes the payment** — your card and billing details are never seen by the app or by us. Your entitlement status is stored locally and on our backend (keyed to your anonymous ID) so limits and access work correctly. As described above, Analytics receives only non-financial purchase events (product identifier and outcome) — never your payment method, receipt, or transaction ID. **Restore Purchases** asks Apple (not us) which products are tied to your Apple Account.

### Export and sharing

Novelist can export a story as EPUB, PDF, or plain text and hand it to iOS's standard share sheet. Where that file goes next (Files, Mail, Messages, AirDrop, a third-party app, etc.) is entirely your choice — we never receive a copy.

### Narration

The "Listen" feature uses Apple's on-device `AVSpeechSynthesizer` (the system text-to-speech engine already built into iOS). Narration happens entirely on your device — no story text is sent anywhere to produce it, and there is no cloud text-to-speech vendor involved.

---

## 3. Permissions the app asks for

Novelist does not request access to the camera, microphone, photo library, contacts, location, motion data, or notifications. It has no need for any of them.

---

## 4. How we use this data

- **On-device data** gives you fast, offline-friendly access to your library and settings.
- **Your anonymous account and server-side story data** let our backend generate chapters, continue your story across sessions with consistency, apply free-tier and fair-use limits, keep your Pro entitlement in sync, prevent abuse, and monitor operating cost.
- **Content sent to Anthropic** exists solely to generate the chapter, plot redirection, edit, or continuation you asked for, and to screen it for safety.
- **Firebase Analytics** tells us, in aggregate, which features are used and where people get stuck (e.g., at the paywall) so we can decide what to fix or improve. We look at counts, not individuals.

We do **not** sell your personal information, and we do not share it for cross-context behavioural advertising (as those terms are defined under the CCPA/CPRA). We do not build advertising profiles or share data with data brokers.

---

## 5. Who we share data with

- **Google LLC** (and, for EEA/UK/Swiss users, Google Ireland Limited) operates **Firebase** — Authentication, Cloud Functions, **Cloud Firestore** (which stores your story content), App Check, and Analytics — as our service provider, under the [Firebase Data Processing Terms](https://firebase.google.com/terms/data-processing-terms) and [Google Privacy Policy](https://policies.google.com/privacy).
- **Anthropic, PBC** processes the story/character content described in Section 2 through its Claude API to generate and safety-check text, under [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy) and [Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms).
- **Apple Inc.** processes your in-app purchases under the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
- We may also disclose information where required by valid legal process.

No other third-party analytics, advertising, or tracking SDK is bundled in the app. These providers primarily process data on servers in the **United States**; for EEA/UK/Swiss users, international transfers rely on Standard Contractual Clauses incorporated into each provider's terms.

---

## 6. How long we keep it

- **On-device data** — kept on your device until you delete it in the app or uninstall the app.
- **Server-side story content** (setup, premise, characters, outline, chapter text, and story memory in Firestore) — retained on our backend until it is deleted on request. **Important:** deleting a story inside the app removes the copy on your device, but does **not** automatically delete the copy on our backend, and neither does uninstalling the app. There is no automatic expiry. To have your server-side content erased, email us (see Section 7).
- **Anonymous account, usage counters, spend totals, and entitlement** — retained on our backend so limits and access keep working; erased on request as above.
- **Firebase Analytics** — retained by Google per Firebase's default event retention (up to 14 months).

---

## 7. Your rights and choices

- **Edit or delete on your device** — change or delete any story, character, or setting directly in the app; uninstalling removes all on-device data.
- **Erase your server-side content** — because we don't collect a name or email, we can't look you up automatically. Email **mukashi.dev@gmail.com** to request deletion of the story content and account data stored on our backend, and we will locate and erase it. (If you still have the app installed, mention that so we can help identify your account ID.)
- **Turn off analytics system-wide** — iOS **Settings → Privacy & Security → Analytics & Improvements → Share iPhone Analytics**.
- **Access or erasure** under GDPR (EEA/UK), CCPA/CPRA (California), or similar laws — email **mukashi.dev@gmail.com** and we'll respond within 30 days.
- **Lodge a complaint** with your local data-protection authority if you're in the EEA, UK, or Switzerland — though we'd appreciate the chance to help first.

---

## 8. Children's privacy

Novelist is a general-audience creative-writing app and is **not directed to children under 13** (or the minimum age in your country). It includes an optional content-tone setting that lets you steer generated stories toward more age-appropriate themes, but this is a creative preference, not a child-directed mode — the app can also generate mature themes (e.g., horror, dark/gritty tone, romance) at your request. We do not knowingly collect personal information from children. If you believe a child has used the app and provided us information, email **mukashi.dev@gmail.com** and we will address it.

---

## 9. Security

- On-device data is stored in iOS's app sandbox.
- Server-side story content is stored in Firebase Cloud Firestore, protected by owner-scoped security rules so one anonymous account cannot read another's stories. Administrative access is limited to us as the operator, for running and supporting the service.
- Data sent to our backend, Anthropic, and Firebase travels over HTTPS (TLS).
- We deliberately keep our data footprint small — no name/email account database, no payment data. No method is perfectly secure, but we will notify you of a breach as required by applicable law.

---

## 10. Changes & contact

If we change this policy, the new version replaces this page and the "Effective date" above is updated; material changes (e.g., a new third-party service, a new category of data) are noted in the app's release notes. This policy applies alongside our [Terms of Use](terms.html).

Questions, requests, or complaints: **mukashi.dev@gmail.com**.

---

© 2026 Abdullah Al Hadi (Mukashi). Novelist.
