> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 6: Sovereignty & Privacy — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 6.1 Rugpull Resistance

**What it measures**: How resistant the product is to unilateral changes by its operator — price increases, feature removal, terms changes, shutdown. Protocol-native products are inherently resistant. Platform-dependent products are inherently vulnerable.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Total rugpull exposure. A single company controls every aspect of the product and can change anything at any time. History of breaking changes: API removals, feature regressions, price hikes, forced migrations. Terms of service include broad unilateral modification clauses. Your continued access is entirely at the operator's discretion. | Twitter/X (API pricing rugpull, feature removal, verification changes), Google products (Reader shutdown, Inbox shutdown, Hangouts shutdown), any "free" product where you're the product |
| 25% | High rugpull risk with some friction. The operator can make unilateral changes but contractual or market constraints provide some protection. Annual pricing locks in cost temporarily. Data export exists but isn't trivial. The product could rugpull tomorrow, but doing so would cost them users (which may or may not matter to them). | ChatGPT/OpenAI (pricing changes, capability regressions, policy shifts), SaaS products with broad ToS modification rights, venture-funded products pre-profitability |
| 50% | Moderate rugpull resistance. Contractual commitments limit sudden changes (enterprise SLA, published pricing guarantee). Open API means alternatives could be built. The product is a platform but a relatively stable one with economic incentives to maintain trust. Rugpull is possible but would be business-damaging. | AWS/GCP services (stable APIs, enterprise contracts), well-established paid SaaS with published pricing commitments |
| 75% | Strong rugpull resistance. Open source with independent community means a fork is always possible. Self-hostable means you can run it regardless of the company's decisions. Published standards or specifications mean the protocol survives the company. The operator could try to rugpull but you have a credible exit path. | Basecamp (public pricing commitment, data export), WordPress (self-hostable, FOSS), Matrix protocol (federated, forkable) |
| 100% | Rugpull-proof by architecture. No single entity can change the rules. Protocol-level operation means the product exists independent of any company. Cryptographic guarantees prevent retroactive modification. Even if every current developer quit, the product continues to function. | Bitcoin (protocol-native, no single point of failure), Nostr (protocol, not platform), IPFS-hosted content, signed git commits |

**Rugpull severity spectrum** (severity of what the user loses in a rugpull event — use to adjust within anchor ranges):
- **Convenience loss** (feature removal, UI changes): base anchor score applies
- **Identity loss** (namespace taken, profile deleted, reputation erased): anchor -15 guidance — losing an identity is hard to rebuild
- **Data loss** (photos, documents, messages, history permanently inaccessible): anchor -10 guidance — data is irreplaceable
- **Financial loss** (funds locked, forced migration costs, sunk subscription): anchor -20 guidance — direct monetary harm is the most severe

These are anchor guidance adjustments, not separate multipliers. A product that scores 50% on structural resistance but exposes users to financial loss on rugpull should be scored closer to 30%.

**Scoring notes**: Evaluate: who controls the product's continued operation? Can a single entity change pricing, remove features, modify terms, or shut down? Has this entity exercised that power before? History of rugpulls (Google product shutdowns, Twitter API changes) is a factual signal, not speculation. Protocol-level products score highest because rugpull resistance is architectural, not contractual. Apply severity spectrum based on what the user stands to lose.

---

## 6.2 Exit Cost Zero

**What it measures**: Whether a user can leave with their data today — standard format export, no vendor lock-in, no data hostage-taking.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Data hostage. No export capability of any kind. Your data exists only inside the product's walled garden. The product's value proposition depends on you not being able to leave. Even screenshots of your own data are watermarked or prevented. You don't own your data — you rent access to it. | Products with no export function, walled-garden social media (no bulk download), proprietary formats with no conversion path |
| 25% | Export exists but is punitive. Data export is partial (text but not media, recent but not historical). Export format is proprietary or requires specialized tools to read. Export is time-delayed ("We'll email you your data in 5-7 business days"). The product makes leaving technically possible and practically miserable. | Products with partial GDPR export, proprietary export formats, products requiring support tickets for data export |
| 50% | Functional export with friction. Full data export available in mostly standard formats (CSV, JSON). Some data types require separate exports. The process takes multiple steps but is self-service. The exported data is usable outside the product with moderate effort. You can leave, but you'll need a Saturday afternoon to set up elsewhere. | Average SaaS with data export, Google Takeout (comprehensive but cumbersome), products with JSON export |
| 75% | Low exit cost. Complete data export in standard, interoperable formats. Export is self-service and fast. Data is organized and documented. Competing products can import the export directly or with minimal transformation. The product makes it easy to leave because it's confident you'll stay by choice. | Basecamp (full export, documented format), Notion (Markdown export), products with API access that enables full extraction |
| 100% | Zero exit cost. Data lives in standard formats from the start (Markdown files, SQLite databases, plain text). No export needed because your data is already in an open format on your machine or accessible via standard protocols. You didn't "import" your data — it was always yours in a format you control. | Obsidian (local Markdown files), Git repositories, Nostr (events on your relay), local-first software, FOSS tools with standard file formats |

**Scoring notes**: Test the actual export: initiate a data export and evaluate completeness, format, and speed. Standard formats: CSV, JSON, Markdown, SQL, ICS (calendar), VCF (contacts). Proprietary formats or PDF-only exports indicate high exit cost. API access counts as an export mechanism (users can extract data programmatically). Local-first products with standard file formats score 100% — no export needed when data is already yours. **Import without matching export** is a named dark pattern: if the product lets you import data easily but has no corresponding export, you're invited in but can't leave with your work — cap at 25% regardless of other factors.

---

## 6.3 Identity Sovereignty

**What it measures**: How much identity control the user retains. Keypair-based identity (user holds keys) is ideal. Government ID required is worst case, always.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Government ID required. The product demands state-issued identification to use it. Phone number verification tied to government identity. Real-name policies enforced. Your legal identity is permanently linked to your product usage, creating an irrevocable surveillance record. "Legally required" is not an excuse — the product chose to build something requiring this. | Products requiring government ID verification, services requiring SSN, platforms with mandatory real-name policies tied to ID verification, Instagram (phone number/ID for new accounts) |
| 25% | Phone-verified identity. Phone number required for account creation. The phone number links to your carrier identity, is subpoena-accessible, and ties your account to a specific physical SIM or eSIM. While less severe than government ID, phone verification creates a strong identity anchor that is reversible only by changing your number. | Signal (phone number required), WhatsApp (phone number required), any service requiring SMS verification as a hard requirement |
| 50% | Email-based identity. Account requires an email address, which is a weaker identity anchor than phone. Disposable email addresses are accepted. Email doesn't tie to government identity directly. The product knows your email but email addresses are changeable and partially pseudonymous. | Most SaaS products (email signup), GitHub (email + username), standard web application accounts |
| 75% | Pseudonymous account. Username or handle is the primary identity. No email required for core function (or email is optional/unverified). No real-name requirement. The product knows you as a persistent pseudonym but has no link to your legal identity. You choose what to reveal. | Hacker News (username, no email verification for reading), products with anonymous account creation, forums with username-only registration |
| 100% | Keypair-based identity. The user generates their own identity via cryptographic keypair. No server-side identity required. No email, no phone, no username — just a public key. Identity is portable across clients and sovereign by construction. The product cannot revoke your identity because it never issued it. | Nostr (nsec/npub keypair identity), Bitcoin wallets (keypair), PGP-based systems, Damus, Primal |

**Scoring notes**: Score based on the minimum identity requirement for core functionality, not optional features. If the product works with email but degrades without phone verification, score based on the degraded experience. Government ID is always 5% (floor) — no exception for "regulatory compliance" because the product chose its domain. Phone number is 25% maximum, including Signal — the phone requirement is a real sovereignty limitation even in a privacy-focused product.

---

## 6.4 Protocol vs Platform

**What it measures**: Whether the product operates as an open protocol (anyone can build clients, no single point of control) or a walled garden (one company controls everything).

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Fully walled garden. Proprietary protocol, no API, no data portability, no third-party clients. The product IS the platform — if the company shuts down or changes direction, everything built on it disappears. Users are captive by design. The product's moat is your inability to leave. | Instagram (no API for core features, no third-party clients), most proprietary social networks, walled-garden messaging apps |
| 25% | Platform with restricted API. An API exists but is throttled, paywalled, or missing critical functionality. Third-party clients are technically possible but practically crippled. The platform tolerates third-party access as a marketing tool, not an architectural commitment. API access can be revoked at any time (and historically has been). | Twitter/X (API pricing makes third-party clients unviable), platforms with "partner-only" API tiers, products that killed their ecosystem (Reddit API pricing) |
| 50% | Platform with open API. Robust API that enables meaningful third-party development. Rate limits are reasonable. Core functionality is accessible programmatically. But the platform still controls the API, sets the rules, and can change them. Third-party clients work today because the platform allows it, not because the architecture guarantees it. | GitHub (comprehensive API, third-party clients), Stripe (API-first), well-designed SaaS with developer APIs |
| 75% | Open protocol with reference implementation. The protocol is documented and open. Multiple clients exist. The reference implementation is one option among many. The protocol can survive the original team's departure. But some centralization remains — maybe the main relay/server is dominant, or the protocol governance is informal. | Matrix (open protocol, multiple clients, federation), ActivityPub/Mastodon (federated, multiple implementations) |
| 100% | Pure protocol, no platform dependency. The product is a client for an open protocol. Any developer can build a compatible client. No single server or company is required for operation. The protocol is cryptographically guaranteed — not just documented but verifiable. Switching clients is seamless because the protocol is the product. | Nostr (protocol, multiple clients — Damus, Primal, Amethyst, etc.), Bitcoin (protocol, thousands of implementations), Email (protocol, hundreds of clients), RSS (protocol, dozens of readers) |

**Scoring notes**: Ask: if the company behind this product disappeared tomorrow, could the product continue to exist? If the answer requires "someone would need to rebuild it" — it's a platform. If the answer is "users would switch to another client" — it's a protocol. API access alone doesn't make a protocol; it makes a platform with a window. The test is whether the architecture guarantees continued operation independent of any single entity.

---

## 6.5 Self-Hostable or Auditable

**What it measures**: Whether a user can run the product themselves, or at minimum verify what the product does. Self-hosting is control. Auditability is trust.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Black box. Closed source, no self-hosting, no audit mechanism, no transparency into what the product does with your data or on your behalf. You interact with an opaque service and trust it completely because you have no alternative. The product could be doing anything behind its API boundary. | Proprietary SaaS with no source access, closed-source cloud services, products that actively prevent reverse engineering (DRM, obfuscation) |
| 25% | Trust-but-verify with limited visibility. Product is closed source but provides some transparency: security audits published, SOC2 certification, privacy certifications. You can't run it yourself or inspect it, but independent third parties have verified some claims. Better than nothing, but you're still trusting intermediaries. | Enterprise SaaS with published security audits, cloud services with compliance certifications, products with third-party penetration test reports |
| 50% | Source-viewable but not self-hostable. Code is available for inspection (source-available license, open-core) but the product can't practically be self-hosted — dependencies on proprietary services, complex infrastructure, or commercial license restrictions. You can audit the code but can't run it independently. | Source-available products (BSL, SSPL), GitLab (open core but complex self-hosting), products with readable source and proprietary dependencies |
| 75% | Self-hostable with effort. Full source code available under a permissive or copyleft license. Self-hosting is documented and supported. Requires technical knowledge but a capable user can run their own instance. The product team may operate the canonical instance, but you're not dependent on them. | Mastodon (self-hostable, well-documented), Nextcloud, Plausible (self-hosted option), Gitea, Ghost |
| 100% | Self-hostable by design. Self-hosting is the default or primary deployment model. The product assumes you're running it yourself. Minimal dependencies, clear documentation, reproducible builds. Or: the product is entirely client-side / local-first with no server dependency to self-host. | Obsidian (local-first, no server), Nostr relays (self-hostable, simple), Pi-hole, Home Assistant, SQLite (embedded, self-hosted by nature) |

**Scoring notes**: Check: is source code available? Under what license? Can you `git clone && docker-compose up` (or equivalent) and have a working instance? Self-hosting that requires 40 hours of configuration is worth less than self-hosting that requires 40 minutes. The gap between 75% and 100% is whether self-hosting is an option the team supports or the product's native operating mode.

---

## 6.6 Privacy-Preserving Payment

**What it measures**: Whether the product accepts payment methods that don't permanently link your real-world identity to your purchase.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Payment requires full legal identity exposure. Credit card only, tied to real name and billing address. KYC verification required before purchase. Your payment is permanently linked to your government identity in a database you don't control. Every purchase is a surveillance data point. | Products requiring KYC for basic purchases, services that demand billing address verification, any product that requires a bank account link |
| 25% | Standard financial identity exposure. Credit card or PayPal only. No alternative payment methods. Your purchase is linked to your financial identity through card network records. While this is "normal," normal is not private — every card transaction creates a permanent record shared across multiple financial institutions and their data partners. | Most commercial web products with credit card only, standard SaaS payment flows, App Store purchases (tied to Apple ID + payment method) |
| 50% | Some payment privacy options. Accepts prepaid cards or privacy card services (Privacy.com) alongside standard credit cards. Or: on-chain cryptocurrency accepted (Bitcoin, Ethereum) — pseudonymous but publicly traceable on the blockchain. Your payment can be partially anonymized with additional effort from you. | Products accepting on-chain Bitcoin/Ethereum, services compatible with Privacy.com or prepaid cards |
| 75% | Strong payment privacy available. Accepts Lightning Network payments — faster, cheaper, and significantly more private than on-chain transactions (no permanent public ledger entry for routine payments). Or: accepts Monero or other privacy-focused cryptocurrencies. The product offers a payment path with meaningful privacy by default. | Products accepting Lightning payments, services accepting Monero, BTCPay Server-powered storefronts |
| 100% | Payment is private by architecture. Primary payment method is Lightning, ecash (Cashu/Fedimint), or equivalent bearer instrument. No identity link by design. The product can't see who paid — only that payment was received. Economic privacy is a feature, not an edge case. | PPQ.AI (Lightning-native), Nostr zaps (Lightning), ecash-based services, products using Cashu or Fedimint mints |

**Scoring notes**: Check the payment page. What methods are accepted? Credit card only = 25%. Lightning or privacy crypto available = 75%. The ranking is: ecash/Lightning (100%) > Monero/privacy coins (75-100%) > Lightning (75%) > on-chain crypto (50%) > privacy cards/prepaid (50%) > credit card (25%) > KYC-required payment (5%). Products that are free or donation-funded score based on their donation payment methods (or 100% if no payment is needed at all).

---

## 6.7 Source Code Availability

**What it measures**: Whether the product's source code is available for inspection, modification, and redistribution.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Fully proprietary with active obfuscation. Closed source, minified/obfuscated client code, legal threats against reverse engineering. The product actively prevents you from understanding what it does. Not just "we don't share source" but "we make sure you can't figure it out." | DRM-protected applications, heavily obfuscated proprietary software, products with aggressive anti-reverse-engineering clauses |
| 25% | Proprietary, closed source. Standard commercial software — source code not available, but no active obfuscation beyond normal minification. You can inspect network requests and client-side behavior. The product doesn't share its source but doesn't actively hide its behavior. | Most commercial SaaS (Figma, Notion, Slack), standard proprietary applications, paid desktop software |
| 50% | Source-viewable with restrictions. Code is readable but under a non-open-source license (BSL, SSPL, Commons Clause). You can audit it, learn from it, and verify security claims. You cannot freely modify, fork, or redistribute. The source is a transparency tool, not a freedom grant. | MongoDB (SSPL), Elastic (SSPL), HashiCorp products (BSL), source-available products with commercial restrictions |
| 75% | Open source with copyleft. Source code available under a copyleft license (GPL, AGPL). You can inspect, modify, fork, and redistribute — with the requirement that derivatives remain open. Active maintenance and community contributions. The code is genuinely open, with conditions that ensure it stays that way. | WordPress (GPL), Linux kernel (GPL), Signal (AGPL), Firefox (MPL), Mastodon (AGPL) |
| 100% | Open source with permissive license and active maintenance. Source available under MIT, Apache 2.0, or BSD. No restrictions on use, modification, or redistribution. Active development, responsive maintainers, community contributions welcomed. The source is a gift to the commons. | SQLite (public domain), Tailwind CSS (MIT), Nostr protocol implementations, curl (MIT), many developer tools |

**Scoring notes**: Check: is source code on GitHub/GitLab/Sourcehut? What license? Is it actively maintained (recent commits)? Is it complete (full product or just a client SDK)? Source-available (BSL/SSPL) is meaningfully different from open source (MIT/GPL) — the former is a transparency tool, the latter is a freedom grant. Abandoned open source (no commits in 12+ months) scores lower than actively maintained open source.

---

## 6.8 Provenance Traceable

**What it measures**: Whether content is signed, timestamped, and attributed in a way that proves its origin and integrity.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | No provenance of any kind. Content has no author attribution, no timestamps, no integrity verification. Content could have been modified, fabricated, or attributed to the wrong person with no way to detect it. Origin is unknowable. | Anonymous content platforms with no attribution, products with editable (and un-versioned) shared content, social media with no content signing |
| 25% | Attributed but unverifiable. Content shows an author name and timestamp but these are platform-controlled and trivially forgeable. The platform could change attribution, modify content, or alter timestamps without detection. You trust the platform to be honest about provenance because there's no verification mechanism. | Standard CMS platforms, social media posts (platform controls displayed metadata), blog posts with mutable timestamps |
| 50% | Platform-verified provenance. Content is attributed to verified accounts with audit trails within the platform. Timestamps are platform-guaranteed. Edit history is visible. Integrity is real within the platform's trust boundary — but requires trusting the platform itself. | GitHub (commit attribution via SSH keys, visible history), Google Docs (edit history), Medium (author profiles with history) |
| 75% | Independently verifiable provenance. Content is signed with keys controlled by the author (not the platform). Timestamps from independent services (RFC 3161 timestamping, blockchain anchoring). A third party can verify provenance without trusting the publishing platform. | Git repositories with GPG-signed commits, PGP-signed email, timestamp-anchored content |
| 100% | Cryptographic provenance by architecture. Every piece of content is a signed event tied to the author's keypair. Timestamps are protocol-level. Content integrity is verifiable by anyone with the public key. Provenance is not a feature the platform adds — it's inherent to how the content is created and distributed. | Nostr events (cryptographically signed, timestamped, verifiable), signed Git tags, blockchain-anchored documents, OpenTimestamps-verified content |

**Scoring notes**: This check applies only to content-publishing products (`[if:content]`). Check: can you verify who created a piece of content? Can you prove it hasn't been modified since creation? Can you verify this without trusting the platform? Cryptographic signing (keypair-based) is the gold standard. Platform-verified accounts are better than nothing but require trusting the platform's honesty about its own data.

---

## 6.9 Distribution Independence

**What it measures**: Whether a mobile app can be obtained and installed without app store gatekeepers.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Single app store dependency, no alternatives. Available only through Apple App Store or Google Play. No sideloading, no alternative distribution. A single corporate gatekeeper controls whether you can install the app. If they remove it, you lose access. | iOS-only apps with no web fallback, apps removed from stores with no alternative (Parler incident), apps exclusively on one store |
| 25% | Multiple stores but no sideloading. Available on both Apple and Google stores (or multiple Android stores). Removal from one store still leaves an alternative. But no direct distribution — you're choosing between gatekeepers, not escaping them. | Most mainstream mobile apps (available on both stores but nowhere else), apps with Amazon Appstore as a third option |
| 50% | App store primary with sideloading possible. Available on standard stores plus APK available for direct download on Android. iOS users still dependent on App Store. Sideloading works but isn't officially supported or documented. Distribution partially independent. | Apps with APK download on their website alongside Play Store listing, Android apps available via Obtainium |
| 75% | F-Droid or equivalent plus sideloading. Available on F-Droid (reproducible builds, open source verification), direct APK download, and optionally on Play Store. Multiple independent distribution channels. The app doesn't depend on any single distributor. iOS limitation remains (Apple's walled garden). | Signal (APK available, F-Droid community build), Firefox (F-Droid), K-9 Mail / Thunderbird Mobile |
| 100% | Fully independent distribution. Sideloadable APK with reproducible builds, available on F-Droid, works on de-Googled phones. Or: the product is a progressive web app / web-first product with no app store dependency at all. Distribution is entirely in the user's and developer's control. No gatekeeper can prevent installation. | PWAs (no store needed), Nostr clients with APK + F-Droid + PWA, fully web-based products, CLI tools installed via package managers |

**Scoring notes**: This check applies only to mobile/desktop apps (`[if:mobile]`). Web-only products are N/A. Check: is the app on F-Droid? Is a direct APK download available? Are builds reproducible? Does it work on de-Googled Android (GrapheneOS, CalyxOS)? iOS distribution is inherently limited by Apple's ecosystem — a product cannot score 100% on iOS distribution alone, but a web fallback compensates.

---

## 6.10 No Google Play Services Dependency

**What it measures**: Whether a mobile app functions on de-Googled Android (GrapheneOS, CalyxOS, LineageOS) without Google Play Services.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Completely dependent on Google Play Services. The app crashes or refuses to launch without Play Services. Google APIs are deeply embedded in core functionality (authentication via Google Sign-In only, maps via Google Maps API only, push via FCM only with no fallback). The app is a Google Play Services client that happens to have other features. | Apps that force Google Sign-In as the only auth method, apps that crash without Play Services, games dependent on Play Games for core functionality |
| 25% | Heavy Play Services dependency with degraded function. The app launches without Play Services but core features are broken or missing. Push notifications don't work. Maps are blank. Authentication options are limited. The app technically runs but is substantially crippled. | Apps with FCM-only push (no notifications on de-Googled phones), apps using Google Maps with no fallback, products with Google Sign-In as the primary auth method |
| 50% | Moderate dependency with workarounds. The app works for core functionality without Play Services but some features require them. Push notifications work via alternative mechanism (WebSocket, polling) but with trade-offs (battery, latency). Most users won't notice the dependency, but power users on de-Googled phones will. | Apps with UnifiedPush support alongside FCM, products using OSM with Google Maps as fallback |
| 75% | Minimal or no Play Services dependency. Core and secondary features work fully without Play Services. Push notifications use alternative delivery (UnifiedPush, WebSocket). Maps use OpenStreetMap. Authentication is email/password or keypair. The app was designed to work outside Google's ecosystem. Minor cosmetic differences on de-Googled phones. | Signal (works on GrapheneOS with workarounds), well-designed FOSS Android apps, apps with UnifiedPush as primary push mechanism |
| 100% | Zero Google dependency by design. No Google Play Services, Google APIs, or Google libraries in the build. Runs identically on stock Android, GrapheneOS, CalyxOS, and LineageOS. Push via UnifiedPush or WebSocket natively. Maps via OSM. Auth via email, keypair, or username. The app treats Google's ecosystem as optional, not required. | F-Droid-native apps (no Google dependencies by policy), FOSS messaging apps (Element, Briar), Nostr Android clients |

**Scoring notes**: This check applies only to mobile apps (`[if:mobile]`). Web-only products are N/A. The definitive test: install on GrapheneOS without microG. Does the app launch? Do push notifications work? Do maps render? Does authentication work? Any "No" to the first question is 25% or below. Testing on CalyxOS (with microG) is a secondary test — microG compatibility is better than nothing but not true independence.

---

## 6.11 Key Management Sovereignty

**What it measures**: Whether the user controls their own cryptographic keys or whether the product holds keys on their behalf (custodial key management).

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | No user keys at all. Authentication is password-based with server-side session management. The product holds everything — your identity, your access, your encryption keys (if any). Account recovery goes through the company. The product can impersonate you, read your data, and revoke your access at will because they hold all the keys. | Standard password-only web applications, most SaaS products, social media accounts |
| 25% | Custodial key management with no export. The product generates and holds cryptographic keys on your behalf. You benefit from cryptographic operations (E2E encryption, signing) but cannot access the raw keys. If the product disappears, your keys disappear with it. You have cryptographic identity, but you don't own it. | Custodial Bitcoin wallets (e.g., Cash App Bitcoin), messaging apps with E2E encryption but no key export, products with server-side key storage |
| 50% | Custodial with export option. The product holds your keys but you can export them (seed phrase backup, key file download). Recovery is possible outside the product but requires manual action. The keys exist on the product's servers AND optionally on your device. Sovereignty is available but not the default. | Bitcoin wallets with seed phrase backup (not enforced), messaging apps with key backup/export, products that let you download your keys |
| 75% | Client-side key generation with product backup. Keys are generated on your device. The product may hold an encrypted backup (for account recovery) but the raw keys live on your hardware. Key operations happen client-side. The product can't sign on your behalf. Meaningfully sovereign with a convenience backup you can opt out of. | Hardware wallet setups with cloud backup, key-based auth apps with optional sync, Keybase (client-side keys with server backup) |
| 100% | Full key sovereignty. NIP-07 browser extension signing, NIP-46 remote signing, hardware wallet signing. Keys never touch the product's servers. All cryptographic operations happen on user-controlled hardware. Key management is entirely the user's responsibility and entirely under their control. | Nostr with nos2x/Alby (NIP-07 signing), Bitcoin with hardware wallet (Coldcard, Trezor), PGP with local keyring, SSH key authentication |

**Scoring notes**: This check applies when the product manages user identity (`[if:identity]`). Products without user accounts or cryptographic identity are N/A. Ask: where are the keys? If on the server: custodial. If on the client with server backup: semi-sovereign. If on the client only: sovereign. NIP-07 (browser extension signing) and NIP-46 (remote signing) represent the gold standard — the product never sees the private key.

---

## 6.12 Relay/Node Independence

**What it measures**: Whether a messaging/social product works with any compatible relay or node, or requires specific infrastructure controlled by the product operator.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Single server dependency. All communication goes through the product's servers exclusively. No federation, no relay choice, no alternative routing. If their server goes down, all communication stops. The product IS the server — there is no protocol, only a service. | WhatsApp (Meta's servers only), iMessage (Apple's servers only), Telegram (their servers only), most proprietary messaging apps |
| 25% | Specific relays/nodes required. The product nominally supports a protocol but requires connection to specific relays or nodes controlled by the operator. You can't add your own relay. The "protocol support" is theoretical — in practice, you're using their infrastructure or nothing. | Products that implement a federated protocol but hard-code relay lists, messaging apps with "preferred server" that's actually required |
| 50% | Recommended relays with alternatives possible. The product suggests specific relays/nodes but allows adding custom ones. Default experience uses the operator's infrastructure. Advanced users can configure alternatives. The freedom exists but the default is centralized. | Mastodon instances (you choose an instance but inter-instance communication varies in quality), federated products with strong home-server preference |
| 75% | Multi-relay by default. The product connects to multiple relays/nodes out of the box. Adding and removing relays is a user-facing feature, not a hidden config. The product is designed for relay diversity. If the operator's relays go down, the product continues to function via alternative relays. | Nostr clients with configurable relay lists (Primal, Damus), Matrix clients with easy server switching, Bitcoin full node software |
| 100% | Relay-agnostic by architecture. The product treats relays/nodes as interchangeable infrastructure. Works with any compatible relay, including self-hosted ones. No preference for any particular relay operator. Relay management is a first-class feature. The product is a protocol client, not a service client. | Nostr clients with full relay management (add/remove/prioritize), Bitcoin nodes (any peer), IRC clients (any server), email clients (any SMTP/IMAP) |

**Scoring notes**: This check applies to messaging and social products (`[if:messaging/social]`). Products without network communication features are N/A. Test: can you add a custom relay/server? Can you remove the default one? Does the product still function if the operator's infrastructure goes down? The distinction between 50% and 75% is whether relay choice is a power-user feature or a default experience.

---

## 6.13 Custodial vs Non-Custodial

**What it measures**: Whether a payment-handling product gives users control of their funds or holds funds on users' behalf (custodial).

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Fully custodial with withdrawal restrictions. The product holds your funds and limits when, where, and how much you can withdraw. Daily limits, minimum balances, withdrawal fees, mandatory holding periods. Your money is in their system and they set the rules for when you can have it back. They can freeze your account at any time. | Exchanges with withdrawal limits and holds (some centralized exchanges), payment processors with rolling reserves, products that hold funds with unclear release conditions |
| 25% | Fully custodial with easy withdrawal. The product holds your funds but withdrawal is straightforward — no artificial limits, reasonable processing time. The product can still freeze, seize, or lose your funds (they hold the keys), but under normal operation, you can get your money out. Custodial risk remains: they could be hacked, go bankrupt, or comply with a seizure order. | Custodial Bitcoin wallets (Cash App, Strike), PayPal balance, centralized exchanges with reliable withdrawal (Kraken, Coinbase under normal operation) |
| 50% | Hybrid custody. The product uses multi-signature or threshold schemes where neither party alone controls the funds. Spending requires cooperation (2-of-3 multisig where you hold 2 keys). The product can't unilaterally seize funds, but you also can't move them without some interaction with the product's infrastructure. A meaningful middle ground. | Multi-sig Bitcoin wallets (Unchained, Casa), Lightning channels with watchtowers, escrow services with multi-party signing |
| 75% | Non-custodial with product infrastructure. Your keys, your funds. The product provides infrastructure (relay, node, watchtower) but never holds your private keys. You can move funds without the product's permission. If the product disappears, you retain your funds — but may need to use a different tool to access them. | Non-custodial Lightning wallets (Phoenix, Breez), non-custodial Bitcoin wallets (BlueWallet), DeFi wallets |
| 100% | Fully non-custodial and self-sovereign. You hold all keys. No product infrastructure required to access or move your funds. Self-hostable node support. The product is a user interface for your own financial infrastructure — it never touches your money. Funds are accessible with standard tools even if the product ceases to exist. | Bitcoin Core (full node, your keys), Sparrow Wallet, Coldcard hardware wallet, ecash bearer tokens (Cashu — you hold the token) |

**Scoring notes**: This check applies to products that handle money (`[if:payments]`). Products without payment features are N/A. Ask: who holds the private keys? If the product: custodial. If the user: non-custodial. If shared: hybrid. Custodial risk is real and ongoing — "we've never had an incident" doesn't change the architectural risk that they could. Non-custodial means the product physically cannot take your money, not that it has chosen not to.

---
