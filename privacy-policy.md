# Novelist — Privacy Policy

**Effective date:** October 22, 2026

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
- **Settings** — theme, language, reader preferences, onboarding state, the **pen name** you choose to show on your covers and exports, narration voice and speed, and the time of any **bedtime-series** reminder.
- **Your cover design** — if you replace a story's cover with your own picture (from Photos, Files, or the camera), that picture is copied into the app and **stays on your device**. It is never uploaded. The same goes for how you style the cover: its framing, filters, fonts, colours, subtitle, and the name you set on it.
- **Purchase/entitlement state** — whether Novelist Pro is currently active on this device.

### On our backend (Firebase Cloud Firestore)

Because Novelist generates each chapter on our server and continues your story across sessions, **the story content you create is also stored on our backend** (Google's Firebase Cloud Firestore), keyed to your anonymous account ID. This server-side copy — not just the on-device copy — is where your story lives between chapters. It includes:

- **The story's setup** — the genre, tone, point of view, ending style, pacing, target audience, language, creativity level, and the **premise/idea text** you wrote.
- **Characters you attached to the story** — their names, roles, traits, and descriptions.
- **AI-generated story data** — the outline, title, and topic hashtags Novelist produced for the story; for a story started as **a novel**, a private plan of its chapters; and for each chapter, a title, three suggested directions for the next chapter, a short recap, one quoted line, and a list of the characters and places so far.
- **The story's cover image** — the one picture generated for the story (see "Cover images" below), stored as an image file in Google Cloud Storage at an unlisted address that includes a random code.
- **Every chapter's full text**, and the **story "memory"** (a running summary plus tracked characters, world facts, and canon facts used to keep chapters consistent).
- **Per-account operational data** — usage counters (how many chapters you've generated, and daily/hourly counts used for fair-use limits), token/cost totals for the AI generation your account has consumed, and your subscription entitlement (tier, product identifier, and expiry).

Because we operate this backend, **our systems can technically access this stored content** — for example, through the administrative tools we use to run usage limits, prevent abuse, monitor cost, and provide support. It is never linked to your name or email, because we don't collect one. We do not sell it, use it for advertising, or share it with anyone except the service providers in Section 5.

### Sent to Anthropic's AI models to generate text

When you generate or regenerate a chapter, add a chapter, pick a suggested direction, redirect the plot, use Fine-Tune steering, or edit a paragraph — and when a chapter's extras (title, suggestions, recap, character list), a novel's plan, or a cover description are prepared — our backend sends the material needed to fulfil that request to **Anthropic's Claude AI models** (a "Sonnet" model for prose, or a faster "Haiku" model for utility and rate-limited fallback). This includes your story setup and characters, the running story memory/summary, the tail of the previous chapter (for continuity), and any custom instructions you type into **Fine-Tune**, **Redirect Plot**, or **Edit paragraph**. Generated and submitted text may also be passed through an automated **content-safety check** (also performed by Claude) before it is returned.

This content is associated only with your anonymous account ID — never with a name or email. Anthropic processes it to generate the requested text and safety result; per Anthropic's commercial API terms, content submitted through its API is not used to train Anthropic's models by default. We do not send your story text to any other AI vendor; the only thing another AI vendor receives is the short cover description described under "Cover images" below. Discover's bundled library stories are pre-written and are not generated per-user.

### Cover images

Each story can get **one** cover picture. To make it, our backend first asks Claude (see above) to write a short description of a scene from the story's genre, tone, premise, and characters, instructed to describe people only by appearance and never by a real person's name. That description can mention your characters' names and looks, but it never includes your story text or anything that identifies you. It is sent to **fal.ai** (Features and Labels, Inc.), which generates the image with an image model we choose: **Muse Image** by Meta, **Nano Banana** by Google, or **FLUX** by Black Forest Labs. FLUX runs on fal.ai's own servers; for Muse Image or Nano Banana, fal.ai passes the description on to Meta or Google, which draws the picture. We ask fal.ai to return the image directly rather than keep it in its request history. The image is then stored with your story as described above. Covers are capped per day, and your own cover photo (if you choose one) never leaves your device.

### Shared chapters and gifts

Sharing is optional and happens only when you tap **Share chapter one as a link** or **Gift this story**. When you do, we publish a **read-only copy** of that story's **title, first chapter, cover image, and the pen name you entered** — and, for a gift, the recipient's name and your note — on a web page at an unlisted address (`mukashi-novelist.web.app/s/` followed by a random code). Anyone you give the link to, and anyone they pass it on to, can read that page. The page is not listed anywhere, is marked so search engines don't index it, and does not show any other part of your story or account.

- **Stop sharing at any time** in the app's Share & export sheet. This switches off that story's link and every gift link you made for it, and within about a minute the page says the story isn't available. Deleting the story in the app switches its links off too.
- When someone opens the page, their browser sends the usual request data (such as IP address and browser type) to Google's Firebase Hosting, which serves it. We keep only a **count** of page views and of taps on the button that opens the App Store — not who viewed.
- Every shared page has a **Report this story** form. A report stores the reason chosen and a one-way hash of the reporter's IP address (to stop duplicate reports); after three reports a page is hidden automatically, and we may review, hide, or remove any shared page.

### Firebase Analytics

We use Firebase Analytics (configured **without** advertising-identifier support — no IDFA, no ad personalization, no cross-app tracking, no ads) to understand feature usage. It collects:

- A per-install device identifier (a Firebase app-instance ID) that resets if you reinstall.
- Device model, OS version, app version, language, and country (derived from IP, then discarded by Google).
- Categorical feature-usage events — for example: a screen was viewed (by name), onboarding was completed (how, and at which slide), a story generation was requested (genre and length) or was blocked by the free-tier paywall (with a reason code), a story was generated or regenerated (genre only), a chapter was added, a story was opened (from where), finished, or deleted, the Fine-Tune sheet was opened, a story was exported (format only), a suggested next-chapter direction was picked, your own cover photo was chosen, a share link was created (and whether it was a gift), a bedtime series was started, narration was started (with the quality level of the voice, such as "Premium"), a Discover genre or collection was opened, a subscription plan was viewed or selected, a purchase started/completed/cancelled/failed (product ID and, on failure, a reason code — never price, receipt, or payment details), a purchase restore was started and its outcome recorded, the theme setting was changed (the new value only), or the App Store review prompt was shown (with a trigger reason).

**We never send** the text of your stories, your premise/idea, character descriptions, or your Fine-Tune/Redirect Plot/Edit instructions to Analytics — only the categorical events listed above. **We do not request App Tracking Transparency** and never read your device's advertising identifier. Novelist does **not** use Firebase Crashlytics or any other crash-reporting, or any other third-party analytics/advertising SDK.

### Firebase App Check

Novelist uses Firebase App Check (Apple's App Attest) to confirm that requests to our backend come from a genuine, unmodified copy of the app (anti-abuse). App Check tokens are attestations about the app binary and device, not personal data.

### In-app purchases (Novelist Pro)

Novelist offers **Novelist Pro**, an auto-renewing subscription (weekly, monthly, or yearly) handled entirely through Apple's StoreKit 2. **Apple processes the payment** — your card and billing details are never seen by the app or by us. Your entitlement status is stored locally and on our backend (keyed to your anonymous ID) so limits and access work correctly. As described above, Analytics receives only non-financial purchase events (product identifier and outcome) — never your payment method, receipt, or transaction ID. **Restore Purchases** asks Apple (not us) which products are tied to your Apple Account.

### Export, sharing, and story cards

Novelist can export a story as **EPUB, PDF, plain text, or story-card images (PNG)** — with its cover and your pen name — and hands the result to iOS's standard share sheet. Where that file goes next (Files, Mail, Messages, AirDrop, a third-party app, etc.) is entirely your choice — we never receive a copy.

If you pick **Save Image** for a story card or a cover, iOS asks for permission to **add** to your photo library. Novelist requests add-only access: it can place the exported image there and **cannot read, browse, or list your photos**.

### Dictation (microphone and speech recognition)

Novelist lets you **speak** your story idea or a steering instruction instead of typing it. This happens only when you tap the microphone button:

- The first time, iOS asks for **Microphone** and **Speech Recognition** permission. You can decline, and everything else in the app keeps working.
- Audio is captured only while dictation is running, and stops the moment you finish or leave the screen.
- **We never receive or store the audio.** It is not sent to our backend, to Anthropic, or to Analytics.
- Transcription runs **on your device** wherever iOS supports on-device recognition for your language. Where it does not, iOS sends the audio to **Apple's** speech-recognition service to transcribe it, under the [Apple Privacy Policy](https://www.apple.com/legal/privacy/). That exchange is between you and Apple; we have no access to it.
- The **transcribed text** simply appears in the text box, exactly as if you had typed it. From there it is treated like any other text you type — if you then generate a story, it travels to our backend and to Anthropic as described above.

### Narration

The "Listen" feature uses Apple's on-device `AVSpeechSynthesizer` (the system text-to-speech engine already built into iOS), with the best voice installed on your device. Narration happens entirely on your device — no story text is sent anywhere to produce it, and there is no cloud text-to-speech vendor involved. While it plays, the story's title, chapter, and cover appear in iOS's **Now Playing** controls on your lock screen, which iOS keeps on your device.

### Reminders

If you turn them on, Novelist schedules **local notifications** on your device: a nudge when a story's next chapter is waiting, and a nightly reminder for a bedtime series at the time you choose. They are created by the app on your device; nothing is sent to us to deliver them.

---

## 3. Permissions the app asks for

Novelist asks for five optional permissions, each only at the moment you first use the feature that needs it. Decline any of them and the rest of the app keeps working normally.

- **Microphone** — to capture audio while you dictate a story idea or a steering instruction, and only while dictation is active.
- **Speech Recognition** — to turn that audio into text (see "Dictation" in Section 2).
- **Photo library (add only)** — so iOS can save an exported story-card image or cover if you choose "Save Image" from the share sheet. Novelist cannot read, browse, or list your photos.
- **Notifications** — for the optional next-chapter and bedtime-series reminders (see "Reminders" in Section 2).
- **Camera** — only if you choose **Camera** in the cover editor to take a photo for a story's cover. The photo stays on your device.

To use your own photo as a cover, Novelist uses iOS's **photo picker** or the **Files** browser, which need no permission: the app receives only the one picture you pick and cannot see the rest of your library or your files.

Novelist does **not** request access to contacts, location, motion data, calendars, or health data.

---

## 4. How we use this data

- **On-device data** gives you fast, offline-friendly access to your library and settings.
- **Your anonymous account and server-side story data** let our backend generate chapters, continue your story across sessions with consistency, apply free-tier and fair-use limits, keep your Pro entitlement in sync, prevent abuse, and monitor operating cost.
- **Content sent to Anthropic** exists solely to generate the chapter, plot redirection, edit, or continuation you asked for, the chapter extras, a novel's plan, and a cover description, and to screen it for safety.
- **The cover description sent to fal.ai** exists solely to generate your story's cover.
- **A shared chapter page** exists only because you chose to share it, and only for as long as you keep sharing it.
- **Dictated audio** is used only to produce the text that appears in the box you are typing into. We never receive or store it.
- **Firebase Analytics** tells us, in aggregate, which features are used and where people get stuck (e.g., at the paywall) so we can decide what to fix or improve. We look at counts, not individuals.

We do **not** sell your personal information, and we do not share it for cross-context behavioural advertising (as those terms are defined under the CCPA/CPRA). We do not build advertising profiles or share data with data brokers.

---

## 5. Who we share data with

- **Google LLC** (and, for EEA/UK/Swiss users, Google Ireland Limited) operates **Firebase** — Authentication, Cloud Functions, **Cloud Firestore** (which stores your story content), App Check, and Analytics — as our service provider, under the [Firebase Data Processing Terms](https://firebase.google.com/terms/data-processing-terms) and [Google Privacy Policy](https://policies.google.com/privacy).
- **Anthropic, PBC** processes the story/character content described in Section 2 through its Claude API to generate and safety-check text, under [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy) and [Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms).
- **Features and Labels, Inc. (fal.ai)** generates cover images from a short scene description (see "Cover images" in Section 2), under [fal.ai's Privacy Policy](https://fal.ai/privacy).
- **Apple Inc.** processes your in-app purchases and, where on-device speech recognition is unavailable for your language, transcribes dictated audio, under the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
- We may also disclose information where required by valid legal process.

No other third-party analytics, advertising, or tracking SDK is bundled in the app. These providers primarily process data on servers in the **United States**; for EEA/UK/Swiss users, international transfers rely on Standard Contractual Clauses incorporated into each provider's terms.

---

## 6. How long we keep it

- **On-device data** — kept on your device until you delete it in the app or uninstall the app.
- **Server-side story content** (setup, premise, characters, outline, chapter text, and story memory in Firestore) — retained on our backend until it is deleted on request. **Important:** deleting a story inside the app removes the copy on your device, but does **not** automatically delete the copy on our backend, and neither does uninstalling the app. There is no automatic expiry. To have your server-side content erased, email us (see Section 7).
- **Cover images** — kept with the story they belong to and erased with it on request.
- **Shared chapter pages** — kept until you stop sharing or delete the story in the app (the page is then switched off) or we remove them; erased on request as above. Report records are kept while the page exists.
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
