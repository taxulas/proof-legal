# Proof — legal and App Store launch-readiness packet

Prepared: 2026-09-16  
Scope: preparation only; no merge, publication, App Store Connect write, submission, purchase or build.

This document is intentionally safe for a public pull request. It contains no private account value,
financial value, secret, personal address or phone number. Apple-account values remain marked for an
authenticated read and must not be copied into this repository without explicit publication approval.

## Locked baselines and publication boundary

- `proof-ios/main`: `d42b49f8c8f632957ea032fc9e467ae6d50f1970`.
- Build 12 product source: `e447975d27724278736fee95929ea8828642c592` (later `main` commits are documentation-only).
- `proof-legal/main`: `bb8aff04dc12898ba362eae4fe24d344c76cb549`.
- GitHub Pages uses the repository root of `main` with the legacy builder.
- This branch and its pull request are public. They do not change the live site until merged.
- Build 12 remains the product candidate. No build, device, Xcode Cloud, RevenueCat or Store action is
  authorized by this packet.

## Shipping-code truth matrix

| Fact | Source | Date checked | Applicability | Owner decision |
|---|---|---|---|---|
| Photos and app state are stored in Proof's private local storage; image analysis runs on-device. | Build 12 source: storage and Vision services | 2026-09-16 | Privacy, review notes, App Privacy | Use this factual claim. |
| Face masking is enabled by default. The original is preserved and the masked image is a separate derivative; masked presentation fails closed if the derivative is unavailable. | Build 12 state defaults and media presentation paths | 2026-09-16 | Privacy and screenshots | Use “masking on by default”; never claim that originals are destroyed. |
| Data Export makes a local ZIP containing byte-identical unmasked originals, an inventory and a README. It is not a one-click restore archive. | Build 12 export controller and native exporter | 2026-09-16 | Privacy, Support, review notes | Warn that exports contain unmasked originals and require safe storage. |
| Delete My Data removes Proof-owned local state, private photos, reminder and owned Replay/export caches. It clears the prior analytics queue and identifier, then may record a new local deletion event. | Build 12 deletion and analytics services | 2026-09-16 | Privacy and Support | Do not claim deletion of exports, backups or provider purchase records. |
| The weekly reminder is a local iOS notification requested only when enabled; Proof has no push server. | Build 12 notification service | 2026-09-16 | Privacy and App Privacy | Declare no push-notification collection. |
| RevenueCat is active when the distributed app contains the public Store SDK configuration. It manages offerings, receipts, `proof_pro`, restore and subscription analytics; no custom identity/login call exists in shipping source. | Build 12 billing services and dependency graph | 2026-09-16 | App Privacy | Purchase History; App Functionality + Analytics; not used for tracking; linked-to-identity = No based on anonymous app-user IDs, subject to live/build verification. |
| A limited local product-event queue always exists. PostHog receives it only if both PostHog build credentials are present. Repository source alone cannot prove whether Build 12 contains them. | Build 12 analytics service and repository scan | 2026-09-16 | App Privacy | `UNKNOWN — NEEDS PROVIDER/OWNER CONFIRMATION` until authenticated build/config evidence is available. |
| Proof has no user account. iOS uses the system photo picker, and camera permission is requested only when the user chooses the camera. | Build 12 import and camera paths | 2026-09-16 | Privacy, Support, review notes | Avoid instructions that require full Photos-library permission. |

## French launch conclusions

### Individual business registration timing

**FACT** — A French sole proprietor can normally file the business-creation form from one month
before the declared start of activity and, at the latest, within 15 days after that start. This is a
filing window, not a recommendation to launch before the legal and Store disclosures are ready.  
**SOURCE** — [Service-Public — Formalités de création d'une entreprise individuelle](https://entreprendre.service-public.fr/vosdroits/F36763)  
**DATE CHECKED** — 2026-09-16  
**APPLICABILITY** — Relevant only if/when commercial activity is carried on in France as a sole
proprietor.  
**OWNER DECISION** — No start date is needed for this preparation packet. Decide timing only when a
specific filing or commercial-opening decision is actually made.

### Required professional-site information

**FACT** — The French government lists mandatory identity and contact notices for a professional
website operated by an individual, including first/last name, address, email and telephone, plus
hosting information and additional registration/VAT/activity details when applicable.  
**SOURCE** — [Ministère de l’Économie — Mentions obligatoires sur un site internet](https://www.economie.gouv.fr/entreprises/developper-son-entreprise/innover-et-numeriser-son-entreprise/mentions-sur-votre-site-internet-les-obligations-respecter)  
**DATE CHECKED** — 2026-09-16  
**APPLICABILITY** — Applies to a professional public site; the exact set depends on the operator's
actual registration and activity. GitHub's public privacy notice does not supply a usable hosting
support telephone number, so the host-notice implementation is not yet safely complete.  
**OWNER DECISION** — Do not insert personal coordinates or invented registration data. Preserve the
current live controller/contact section and add the complete notice only after existing Apple values
have been read and publication of each value has been expressly approved.

### Sole proprietor, micro regime and company

**FACT** — A micro-entrepreneur is an individual entrepreneur using a simplified tax/social regime;
it is not a separate company. A sole proprietorship and a company are legally distinct structures.  
**SOURCE** — [Ministère de l’Économie — Devenir micro-entrepreneur](https://www.economie.gouv.fr/particuliers/vie-en-entreprise/comment-devenir-micro-entrepreneur-auto-entrepreneur?page=1), [Service-Public — Entreprise individuelle ou société](https://entreprendre.service-public.fr/vosdroits/F37396)  
**DATE CHECKED** — 2026-09-16  
**APPLICABILITY** — Relevant to future French registration and Apple account strategy.  
**OWNER DECISION** — This packet selects no legal, tax or social regime and invents no company.

### Business address

**FACT** — A sole proprietor must choose a business address; available domiciliation routes and
conditions depend on the real situation.  
**SOURCE** — [Service-Public — Domicilier une entreprise individuelle](https://entreprendre.service-public.fr/vosdroits/F2160?quest0=0)  
**DATE CHECKED** — 2026-09-16  
**APPLICABILITY** — Relevant before completing mandatory public notices or trader coordinates.  
**OWNER DECISION** — Do not publish any address from Apple merely because it is readable there;
separate factual verification from authorization to republish.

### Privacy-controller transparency

**FACT** — GDPR Article 13 requires transparent controller identity/contact and other processing
information when personal data is collected. CNIL's mobile-app guidance emphasizes mobile-specific,
accessible information and permission minimisation.  
**SOURCE** — [CNIL — RGPD, chapitre III](https://www.cnil.fr/fr/reglement-europeen-protection-donnees/chapitre3), [CNIL — Recommandation applications mobiles](https://www.cnil.fr/sites/cnil/files/2024-09/recommandation-applications-mobiles.pdf)  
**DATE CHECKED** — 2026-09-16  
**APPLICABILITY** — RevenueCat processing is active; PostHog is conditional. Local-only photos are
not received by the publisher.  
**OWNER DECISION** — Privacy is `NEEDS OWNER INPUT` until authenticated Apple facts are compared and
the legally necessary publication values are personally validated.

## Apple seller, account and DSA matrix

| Topic | Current | Recommended | Reason | Confidence | Can write later | Owner decision |
|---|---|---|---|---|---|---|
| Account type and legal identity | PENDING AUTHENTICATED READ | Read Apple Developer membership details; do not copy private values here. | Individual seller name is the account holder's legal name. | High | No write planned | Validate only if Apple does not already establish it. |
| Public developer/seller name | PENDING AUTHENTICATED READ | Keep the live Apple value unless a supported account conversion is later completed. | Apple states that an individual developer name is the legal name. | High | Not in this lot | No invented trading/company name. |
| DSA trader status | PENDING AUTHENTICATED READ | Read the existing self-assessment and verification state; make no attestation. | Trader status is self-assessed and has public-display consequences in the EU. | High | Yes, in a separately authorized action | Personal legal validation may be required only if Apple has no final choice. |
| Trader address/PO box, phone, email | PENDING AUTHENTICATED READ | Read status and values; redact them from public evidence. | Apple displays verified trader contact data on EU product pages. | High | Yes, in a separately authorized action | Explicit approval required before any web republication. |
| Individual → Organization | Future scenario only | Consider only after a real eligible legal entity exists. | Apple requires organization eligibility, founder/cofounder authority, D‑U‑N‑S and supporting documents. | High | No | No conversion now. |
| D‑U‑N‑S | Not required for an individual account | Obtain only for a future eligible organization. | Apple says individuals do not need a D‑U‑N‑S number; sole proprietors enroll as individuals. | High | No | Do not apply in this lot. |

Sources checked 2026-09-16:

- [Apple — Set your developer name](https://developer.apple.com/help/app-store-connect/create-an-app-record/set-your-developer-name)
- [Apple — EU Digital Services Act trader requirements](https://developer.apple.com/help/app-store-connect/manage-compliance-information/manage-european-union-digital-services-act-trader-requirements)
- [Apple — Updating account information](https://developer.apple.com/help/account/membership/updating-your-account-information)
- [Apple — D‑U‑N‑S](https://developer.apple.com/help/account/membership/D-U-N-S)

## Legal-page changes

- Privacy EN/FR/DE now matches the shipping implementation: local originals, default face mask,
  RevenueCat, conditional PostHog, local notification, unmasked ZIP export, deletion limits and
  restore-access limits.
- Support EN/FR/DE now reflects the iOS system picker, 2–100 historical selection, camera recovery,
  comparability guidance, Pro restore limits, unmasked export, deletion scope and privacy-safe bug
  reporting.
- Terms EN/FR/DE receives only the material delta: restore does not restore photos/timeline/settings,
  and local deletion does not erase external exports/backups/provider purchase records or cancel a
  subscription.
- The controller/contact paragraph remains live rather than receiving a deployable placeholder.
  Future insertion point: immediately under **Who is responsible / Responsable / Verantwortliche
  Stelle**, after authenticated facts and explicit publication approval.

## App Store metadata — final prepared copy

Limits checked against Apple documentation on 2026-09-16: app name 30 characters, subtitle 30,
promotional text 170, description 4,000 and keywords 100 bytes. Counts below are Unicode characters
except keywords, which are UTF‑8 bytes.

### English (U.S.)

**Name — 5/30**  
`Proof`

**Subtitle — 29/30**  
`Private before & after photos`

**Promotional text — 134/170**  
`Turn old progress photos into an immediate Reveal. Compare privately with consistent framing, then keep the full story with Proof Pro.`

**Description — 1,081/4,000**

Turn the progress photos already on your iPhone into a clear, private visual story.

Start with historical photos for an immediate Reveal, or begin today and use guided capture to make
future comparisons more consistent. Proof checks framing, pose, visibility and lighting on your
device, then shows what can—and cannot—be compared honestly.

With Proof you can:

- import 2–100 historical photos or start with one photo today;
- compare before and after with Reveal controls;
- keep photos and analysis in the app's private local storage;
- mask faces by default while preserving your originals;
- view your timeline and add optional waist measurements;
- share a static comparison when you choose;
- export your local data or delete it from Proof.

Proof Pro unlocks the complete timeline, comparisons across dates, ongoing guided check-ins and the
full dated Replay with local HD export. Available subscription options and prices are always shown
by the App Store before purchase.

Proof is a visual progress tool, not a medical device or medical, nutritional or fitness advice.

**Keywords — 97/100 bytes**  
`progress photos,before after,transformation,fitness,comparison,timeline,private,replay,body photo`

### French (France)

**Name — 5/30**  
`Proof`

**Subtitle — 26/30**  
`Photos avant/après privées`

**Promotional text — 147/170**  
`Transforme tes anciennes photos en Reveal immédiat. Compare-les en privé avec un cadrage cohérent, puis conserve toute ton histoire avec Proof Pro.`

**Description — 1,321/4,000**

Transforme les photos de progression déjà présentes sur ton iPhone en une histoire visuelle claire
et privée.

Commence avec d’anciennes photos pour obtenir un Reveal immédiat, ou démarre aujourd’hui et utilise
la prise de vue guidée pour rendre les prochaines comparaisons plus cohérentes. Proof vérifie sur ton
appareil le cadrage, la pose, la visibilité et l’éclairage, puis indique ce qui peut — ou ne peut pas
— être comparé honnêtement.

Avec Proof, tu peux :

- importer 2 à 100 photos historiques ou commencer aujourd’hui avec une photo ;
- comparer avant et après avec les contrôles Reveal ;
- conserver les photos et l’analyse dans le stockage local privé de l’application ;
- masquer les visages par défaut tout en conservant les originaux ;
- parcourir la chronologie et ajouter des tours de taille facultatifs ;
- partager une comparaison statique lorsque tu le décides ;
- exporter tes données locales ou les supprimer de Proof.

Proof Pro déverrouille la chronologie complète, les comparaisons entre dates, les prises de vue
guidées continues et le Replay daté complet avec export HD local. Les abonnements et prix disponibles
sont toujours affichés par l’App Store avant l’achat.

Proof est un outil visuel de suivi de progression, pas un dispositif médical ni un conseil médical,
nutritionnel ou sportif.

**Keywords — 95/100 bytes**  
`photos progrès,avant après,transformation,fitness,comparaison,chronologie,privé,replay,corps`

### German (Germany)

**Name — 5/30**  
`Proof`

**Subtitle — 28/30**  
`Private Vorher-Nachher-Fotos`

**Promotional text — 149/170**  
`Mach aus alten Fortschrittsfotos sofort ein Reveal. Vergleiche privat mit konsistentem Bildausschnitt und behalte mit Proof Pro die ganze Geschichte.`

**Description — 1,185/4,000**

Mach aus den Fortschrittsfotos auf deinem iPhone eine klare, private visuelle Geschichte.

Beginne mit älteren Fotos für ein sofortiges Reveal oder starte heute und nutze die geführte Aufnahme
für besser vergleichbare zukünftige Bilder. Proof prüft Bildausschnitt, Pose, Sichtbarkeit und Licht
auf deinem Gerät und zeigt anschließend, was sich ehrlich vergleichen lässt — und was nicht.

Mit Proof kannst du:

- 2–100 ältere Fotos importieren oder heute mit einem Foto starten;
- Vorher und Nachher mit den Reveal-Reglern vergleichen;
- Fotos und Analyse im privaten lokalen App-Speicher behalten;
- Gesichter standardmäßig maskieren und Originale bewahren;
- deinen Verlauf ansehen und optional Taillenumfänge ergänzen;
- bei Bedarf einen statischen Vergleich teilen;
- lokale Daten exportieren oder aus Proof löschen.

Proof Pro schaltet den vollständigen Verlauf, Vergleiche zwischen Daten, fortlaufende geführte
Check-ins und das vollständige datierte Replay mit lokalem HD-Export frei. Verfügbare Abos und Preise
zeigt immer der App Store vor dem Kauf an.

Proof ist ein visuelles Fortschrittswerkzeug, kein Medizinprodukt und keine medizinische,
Ernährungs- oder Fitnessberatung.

**Keywords — 99/100 bytes**  
`Fortschrittsfotos,vorher nachher,Transformation,Fitness,Vergleich,Verlauf,privat,Replay,Körperfoto`

Apple limit sources: [app information](https://developer.apple.com/help/app-store-connect/reference/app-information/app-information),
[platform version information](https://developer.apple.com/help/app-store-connect/reference/app-information/platform-version-information).

## Categories

| Field | Current | Recommended | Reason | Confidence | Can write later | Owner decision |
|---|---|---|---|---|---|---|
| Primary category | PENDING AUTHENTICATED READ | Health & Fitness | Core use is private visual fitness/body-progress tracking. | High | Yes | Confirm after live declarative consequences are visible. |
| Secondary category | PENDING AUTHENTICATED READ | Photo & Video | Capture, import, comparison, masking and Replay are meaningful secondary functions. | High | Yes | Confirm after live declarative consequences are visible. |

## 2026 age-rating questionnaire — prepared answers

These answers describe Build 12 rather than targeting a desired rating.

| Content/capability | Prepared answer | Reason | Confidence |
|---|---|---|---|
| Parental controls | No | No parental-control feature. | High |
| Age assurance | No | No age-verification mechanism. | High |
| Unrestricted web access | No | No embedded unrestricted browser. | High |
| User-generated content | No | Private user photos are not distributed to a broad audience in Proof. | High |
| Messaging and chat | No | No messaging. | High |
| Advertising | No | No advertising. | High |
| Profanity or crude humor | None | No such content supplied by Proof. | High |
| Horror/fear themes | None | No such content supplied by Proof. | High |
| Alcohol, tobacco or drugs | None | No such content supplied by Proof. | High |
| Sexual content or nudity | None | Proof supplies none; user-selected private photos are not published by Proof. | High |
| Violence | None for every violence category | No violent content. | High |
| Medical or treatment information | None | Proof expressly does not diagnose or advise. | High |
| Health or wellness topics | Frequent | The product consistently concerns visual fitness/body-progress tracking. | Medium |
| Gambling, simulated gambling, contests and loot boxes | None/No | No such mechanic. | High |
| Calculated-rating override | Not Applicable | No basis to override the questionnaire. | High |

Expected result from the prepared answers: likely **9+**, subject to the exact live 2026 questionnaire
and Apple's calculation. Do not weaken factual answers to force 4+.

Sources checked 2026-09-16: [age-rating definitions](https://developer.apple.com/help/app-store-connect/reference/app-information/age-ratings-values-and-definitions),
[set an app age rating](https://developer.apple.com/help/app-store-connect/manage-app-information/set-an-app-age-rating).

## App Privacy — prepared disclosure

| Data type / field | Current | Recommended | Reason | Confidence | Can write later | Owner decision |
|---|---|---|---|---|---|---|
| Photos | PENDING AUTHENTICATED READ | Not collected | Photos remain on-device and are not transmitted to Proof or providers by the normal product flow. | High | Yes | Keep unless live evidence contradicts. |
| Purchase History | PENDING AUTHENTICATED READ | Collected; App Functionality + Analytics; not used for tracking | RevenueCat processes receipt/subscription information to operate Pro and subscription analytics. | High | Yes | Confirm live provider configuration. |
| Purchase History linked to identity | PENDING AUTHENTICATED READ | No | Shipping code uses RevenueCat's anonymous app-user ID and has no account/custom identity call. | Medium-high | Yes | Change only if live/provider evidence shows identity mapping. |
| Product Interaction (Usage Data) | PENDING AUTHENTICATED READ | Declare only if PostHog is present in Build 12; Analytics; not linked; not tracking | Local-only events are not “collected”; network collection is conditional on distributed-build credentials. | Medium | Yes | `UNKNOWN — NEEDS PROVIDER/OWNER CONFIRMATION`. |
| Tracking | PENDING AUTHENTICATED READ | No | Neither RevenueCat nor conditional PostHog is used to track users across other companies' apps/sites. | High | Yes | Confirm live SDK configuration. |

RevenueCat source checked 2026-09-16: [Apple App Privacy guidance](https://www.revenuecat.com/docs/platform-resources/apple-platform-resources/apple-app-privacy).
Apple source checked 2026-09-16: [Manage app privacy](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-app-privacy).

## App Review information — prepared copy

**Review notes**

Proof is a local-first visual progress app. No account is required. To test the free path, choose
Historical and select 2–100 rights-safe photos, or choose Start Today and select/capture one photo.
The app performs framing, pose, visibility and lighting analysis on-device. Face masking is enabled
by default; originals remain in private app storage.

The first historical Reveal is permanently available. Proof Pro unlocks the complete timeline,
cross-date comparisons, ongoing guided check-ins and full dated Replay/HD export. Use the review
sandbox Apple account for Annual or Monthly and Restore Purchases. Restore reinstates entitlement
only; it does not restore local photos or history.

Data Export is in You and creates a local ZIP containing unmasked originals; it is not a restore
archive. Delete My Data is also in You, affects local Proof-owned data and does not cancel an App
Store subscription. Proof is not a medical device and does not provide diagnostic, medical,
nutritional or fitness advice.

**Review contact, sign-in and attachments** — PENDING AUTHENTICATED READ. No demo account is needed.
Do not add personal contact values or attachments to public evidence.

## Subscription checklist

| Field | Current | Recommended | Reason | Confidence | Can write later | Owner decision |
|---|---|---|---|---|---|---|
| Subscription group | PENDING AUTHENTICATED READ | One group containing Annual and Monthly | Shipping product contract uses one `proof_pro` entitlement. | High | Yes | Verify names/status live. |
| Annual product | PENDING AUTHENTICATED READ | Present, localized EN/FR/DE, review-ready if all fields complete | Annual is the primary presentation in the product contract; no fixed price claim in metadata. | High | Yes | No price change in this lot. |
| Monthly product | PENDING AUTHENTICATED READ | Present, localized EN/FR/DE, review-ready if all fields complete | Monthly is the alternative launch product. | High | Yes | No price change in this lot. |
| Free trial / introductory offer | PENDING AUTHENTICATED READ | Make no trial claim | No trial is confirmed in the product contract. | High | Yes | Do not create an offer in this lot. |
| Review screenshots | PENDING AUTHENTICATED READ | Verify a rights-safe purchase-screen screenshot for each product as Apple requires | Subscription review assets are separate from storefront screenshots. | High | Yes | Do not upload in this lot. |
| First subscription submission | Not submitted in this lot | Submit with the app version when later authorized | Apple requires the first auto-renewable subscription to accompany a new app version. | High | Yes | Separate future authorization. |

Apple source checked 2026-09-16: [Submit an in-app purchase](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-an-in-app-purchase).

## Future storefront screenshot shot list

Prepare later from the real Build 12 UI with rights-safe, non-personal source photos. Do not depict a
fabricated body result, a directional body claim, AI transformation, future feature, unconfirmed
price or free trial.

1. **Historical → Reveal immediately** — historical import entry and a rights-safe neutral example.
2. **Reveal comparison controls** — before/after slider or overlay, with honest comparability language.
3. **Private by design** — face mask enabled and a concise on-device/local-storage caption.
4. **Consistent future capture** — guided framing/capture screen without claiming perfect results.
5. **Timeline** — dated visual history, using neutral licensed/synthetic app-test imagery that does not
   imply a real person's transformation.
6. **Proof Pro Replay** — dated Replay/player and local HD export, without price or trial text.

Apple currently permits 1–10 screenshots per supported device display. Verify live device slots and
use Apple's listed pixel dimensions before production: [screenshot specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications).

## Authenticated read-only inventory still required

Every line below is read-only and must be completed from Apple before any human fact request:

| Field | Current | Recommended | Reason | Confidence | Can write later | Owner decision |
|---|---|---|---|---|---|---|
| Membership identity, entity type, seller/developer name | PENDING AUTHENTICATED READ | Compare to Apple rules above | Establishes the actual publisher facts. | High | No write in this lot | Ask only if Apple is incomplete. |
| DSA trader choice, verification, public contact values | PENDING AUTHENTICATED READ | Compare to launch obligations; redact evidence | Determines EU availability/display readiness. | High | No write in this lot | Personal validation only if legally required. |
| Agreements, tax and banking status | PENDING AUTHENTICATED READ | Record statuses only, not sensitive financial values | Paid apps/subscriptions depend on active agreements. | High | No write in this lot | Ask only about unresolved actions. |
| Territories, availability, prices and platforms | PENDING AUTHENTICATED READ | Preserve live commercial values; no change | Needed for accurate readiness and metadata claims. | High | No write in this lot | No start date by default. |
| Version metadata/localizations/review information | PENDING AUTHENTICATED READ | Diff against this packet | Avoids overwriting good existing values. | High | No write in this lot | Approve later write set separately. |
| Categories, age rating, compliance and App Privacy | PENDING AUTHENTICATED READ | Diff against prepared answers | Ensures declarations match Build 12. | High | No write in this lot | Validate irreducible attestations only. |
| Annual, Monthly, group, localizations and review captures | PENDING AUTHENTICATED READ | Diff against subscription checklist | Needed for first subscription readiness. | High | No write in this lot | No price/offer action. |
| Build 12 processing state and selectable version | PENDING AUTHENTICATED READ | Confirm candidate availability only | Establishes submission readiness without selecting it. | High | No write in this lot | No selection or submission. |

## Readiness state before the authenticated read

- Privacy: **NEEDS OWNER INPUT** — not because values should be retyped, but because authenticated
  Apple facts, PostHog-in-Build-12 status and any legally indispensable publication consent remain to
  be resolved.
- Terms: **READY** as a factual product document, subject to normal legal review.
- Support: **READY** as factual product guidance.
- Metadata: **PREPARED**; live values and form consequences remain to be compared read-only.
- App Privacy: **BLOCKED** from final declaration until PostHog Build 12 status and existing Apple
  selections are read.

No legal/tax/social regime has been selected. No Apple value has been changed or attested. No
publication, merge or submission is authorized by this packet.
