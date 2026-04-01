> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 5: Product Conduct — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 5.1 No Access Gates

**What it measures**: Whether the product gates content or functionality behind forced signups, login walls, or paywalls that block what should be accessible.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Content visible for 1-2 seconds then obscured by a full-screen login wall. Public content (user profiles, posts, images) requires authentication to view. The URL works but the product holds the content hostage until you create an account. The "fuck-you" login wall: you can see it exists but you can't have it unless you hand over your identity. | Instagram (public profiles gated behind login wall), Quora (answers blurred behind signup), LinkedIn (profile gating) |
| 25% | Partial access with aggressive gating. You can see some content but hit a wall quickly — "Read more" requires signup, search results require login to click through, features locked behind mandatory accounts for basic use. The product lets you taste it then slams the door. | Medium (read limit then paywall), Twitter/X (browse limit then login required), Pinterest (boards gated after first few pins) |
| 50% | Reasonable gating with clear value exchange. Free content is genuinely accessible. Paid features are clearly separated from free ones. Signup required for personalized features (saving, preferences) but not for consuming public content. The gate exists but it's in a sensible place. | Freemium SaaS with generous free tiers, news sites with metered paywalls (10 articles/month) |
| 75% | Minimal gating. Almost all content and core features accessible without an account. Signup adds personalization or collaboration features, not access to what's already there. No login walls on public content. The product trusts you to decide if it's worth creating an account. | Hacker News (everything visible, account for voting/commenting), DuckDuckGo, most well-designed open source documentation |
| 100% | Zero access gates. Everything the product does is accessible without signup, login, or payment. Identity is optional and additive (saves preferences, enables sync) not required for core value. The product demonstrates its worth before asking for anything. | Pinboard (full functionality visible before purchase), Wikipedia, Craig Mod's free essays, PPQ.AI (pay per query, no account required) |

**Scoring notes**: Visit the product in a private/incognito browser. How much of the advertised functionality can you access without creating an account? A login wall on public content (Instagram pattern) is 0%. A paywall on premium features with a genuine free tier is 50%. Score based on the ratio of accessible value to gated value, weighted by what a first-time visitor came for.

---

## 5.2 No Manufactured Urgency

**What it measures**: Absence of artificial scarcity, countdown timers, and pressure tactics designed to prevent the user from thinking before acting.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product is a pressure machine. Countdown timers on every offer. "Only 2 left!" on items with infinite digital supply. "Someone just bought this!" notifications manufacturing social proof. Flash sales that refresh endlessly. Every interaction is engineered to make you act before you think. The product weaponizes anxiety. | Booking.com ("Only 1 room left!", "23 people looking at this"), dark-pattern e-commerce with fake countdown timers, drop-shipping sites with manufactured scarcity |
| 25% | Regular urgency tactics in key conversion flows. "Limited time offer" on the pricing page. "Your trial expires in X days" banner shown daily. "This price won't last" on a pricing tier that hasn't changed in years. The urgency is fake but not constant — it concentrates around moments the product wants you to pay. | SaaS products with aggressive trial expiration banners, e-commerce with periodic "flash sale" messaging, products with persistent "upgrade now" urgency |
| 50% | Occasional mild urgency that reflects real constraints. Early-bird pricing that genuinely ends (and you can verify this). Limited beta slots that are actually limited. The urgency exists but it's honest — the constraint is real, not manufactured. Crosses the line occasionally with phrases like "Don't miss out." | Products with genuine limited-time launch pricing, legitimate waitlists with real capacity constraints |
| 75% | No urgency tactics in the product itself. Pricing is stable and visible. No countdown timers, no scarcity signals, no "act now" pressure. The product might send a trial-ending reminder (functional, not manipulative) but never manufactures urgency to drive conversion. | Basecamp (stable pricing, no urgency), Signal (no pricing at all), most well-designed developer tools |
| 100% | The product actively respects your decision-making time. No urgency of any kind. Pricing is permanent and transparent. If there's a trial, it ends quietly without pressure. The product trusts that its value is sufficient to convert users without manipulation. Take a week to decide — nothing changes. | PPQ.AI (pay per use, no subscription pressure), Pinboard (one-time pricing, take or leave it), open source tools |

**Scoring notes**: Look for: countdown timers (especially on digital goods), "only X left" on unlimited inventory, "someone just bought this" notifications, "limited time" on permanent offers, aggressive trial expiration messaging. Real scarcity (physical goods with actual inventory limits) is not penalized. The test is: would the offer actually disappear if the timer runs out?

---

## 5.3 No Nag/Re-engagement

**What it measures**: Whether the product respects your attention when you're not using it — absence of notification spam, "we miss you" campaigns, badge-count manipulation, and push notification abuse.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product stalks you when you leave. Daily "we miss you" emails. Push notifications for things you never asked about. Badge counts that increment for marketing messages, not real activity. Notification preferences are a maze designed to prevent you from actually turning things off. The product treats your absence as a problem to solve aggressively. | Products that send daily re-engagement emails, mobile apps with undismissable badge counts for promotional content, services that email you about other users' activity you don't care about |
| 25% | Regular nagging that erodes trust. Weekly "digest" emails you didn't request. Push notifications for "suggested" content. "Complete your profile" reminders that never stop. Notification settings exist but default to everything-on and require granular per-type disabling. The product is needy. | Twitter/X (notifications for "you might like" content), social media with "trending" push notifications, SaaS with persistent "setup incomplete" banners |
| 50% | Moderate notifications with adequate controls. Some unsolicited emails but they're infrequent and relevant. Push notifications exist but are mostly for things you care about. Notification settings are accessible and reasonably organized. The product nudges you but doesn't nag. Unsubscribe works on first attempt. | Average SaaS with weekly update emails, products with reasonable default notification settings |
| 75% | Notifications are minimal and user-controlled. Only notifications you explicitly opted into. No "we miss you" campaigns. No badge-count manipulation. Email frequency is low and relevant. One-click unsubscribe that actually works. The product is confident enough to let you come back on your own terms. | Basecamp (notification controls as core feature), Pinboard (zero re-engagement), Linear (notifications for assigned work only) |
| 100% | The product never contacts you unsolicited. Zero marketing emails, zero push notifications unless explicitly requested for specific events. No re-engagement campaigns of any kind. No badge manipulation. The product has no opinion about how often you should use it. Your attention is yours. | Signal (notifications only for incoming messages), RSS readers (inherently pull-based), CLI tools, self-hosted software |

**Scoring notes**: Create an account, use the product once, then stop for a week. Count emails received. Check push notification defaults (how many categories are pre-enabled?). Test unsubscribe — does it work immediately or require logging in? Does the product distinguish between transactional notifications (your stuff changed) and marketing notifications (come back and look at things)? Products that conflate the two score lower.

---

## 5.4 No Attention Harvesting

**What it measures**: Whether the product provides natural stopping points or whether it's engineered to maximize time-on-site through infinite scroll, autoplay, dopamine loops, and streak mechanics.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product is an attention trap. Infinite scroll with no end marker. Autoplay next queued before current content finishes. Streak mechanics that punish missing a day. Dopamine-variable reward loops (pull to refresh with different content each time). Gamification (points, badges, levels) designed to create obligation. The product is engineered to make leaving feel like losing. | Instagram (infinite scroll, algorithmic feed, like dopamine), TikTok (autoplay infinite feed, variable reward), Duolingo (streak guilt), Snapchat (streak mechanics) |
| 25% | Significant attention-harvesting patterns present. Infinite scroll is the primary navigation pattern. Autoplay exists but can be disabled. Some gamification (achievement badges, usage stats presented as scores). The product has natural content endpoints somewhere but the default experience buries them. | Twitter/X (infinite timeline, engagement notifications), YouTube (autoplay next, recommendation sidebar), Reddit (infinite scroll on home feed) |
| 50% | Mixed patterns. Content has endpoints but the product suggests more aggressively. "Recommended for you" sections at every bottom. Pagination exists but "load more" is the default. No streak mechanics or gamification. The product is mildly sticky but you can find the edges. | News aggregators with "more stories" at bottom, e-commerce with aggressive recommendation engines, email clients with "suggested" filters |
| 75% | Clear natural endpoints with minimal suggestion. Content has a defined end. "You're all caught up" or equivalent signals. No autoplay, no infinite scroll. Recommendations exist but are in a dedicated section, not injected into the content flow. The product is designed for sessions with a beginning and an end. | Basecamp (work is finite, inbox reaches zero), Pinboard (bookmarks have an end), email clients with "inbox zero" as achievable state |
| 100% | The product has a built-in stopping point. When you're done, you know you're done. No algorithmic feed, no infinite scroll, no autoplay, no gamification, no streak mechanics. Content is chronological or user-curated, not algorithmically maximized for engagement. The product respects the natural rhythm of use-then-leave. | RSS readers (you read your feeds, you're done), Signal (conversations end naturally), CLI tools (run, get output, done), Hacker News (finite front page, no infinite scroll) |

**Scoring notes**: Use the product for 10 minutes. How hard is it to stop? Does it signal "you're done" anywhere? Check for: infinite scroll (scroll to bottom — does it end?), autoplay (does the next thing start automatically?), streak/gamification mechanics (does it track consecutive days, award badges, show scores?), variable reward (does pull-to-refresh show different content each time?). A product that uses infinite scroll as its primary navigation pattern is 25% maximum, regardless of other qualities.

---

## 5.5 Privacy & Tracking Composite

> 5.5 composite score = geometric mean of applicable sub-check scores. For web-only products, sub-checks 5.5f, 5.5g, 5.5h are N/A and excluded. The composite score uses the 5% floor (minimum score is 5, not 0) to prevent a single privacy failure from zeroing the entire category.

---

### 5.5a Cookie Count

**What it measures**: Number and type of cookies set on visit. Zero is ideal. First-party session cookies are acceptable. Third-party cookies penalize.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Cookie infestation. 30+ cookies on first visit, majority third-party. Tracking cookies from ad networks, analytics suites, and data brokers set before any user interaction. The product uses your browser as a tracking beacon before you've done anything. | Ad-heavy news sites (50+ cookies), free mobile games with ad SDKs, products with multiple ad network integrations |
| 25% | Heavy cookie use. 10-30 cookies including multiple third-party tracking cookies. Ad network cookies present. Analytics cookies from multiple providers. First-party cookies include persistent identifiers beyond session management. | Most commercial web applications, e-commerce sites with retargeting, social media platforms |
| 50% | Moderate cookies with some third-party presence. 5-10 cookies total. One or two third-party analytics cookies (Google Analytics). First-party session cookies plus a few persistent cookies for preferences. No ad network cookies. | Average SaaS products using Google Analytics, standard business websites |
| 75% | Minimal cookies, first-party only. 1-3 cookies, all first-party. Session cookie for authentication, maybe a preference cookie. Zero third-party cookies. No persistent tracking identifiers. The product stores what it needs for function and nothing more. | Basecamp, well-designed indie SaaS, products using privacy-respecting analytics |
| 100% | Zero cookies or strictly functional session-only. No persistent cookies. No tracking of any kind. If authentication is needed, session cookie only, destroyed on browser close. The product proves cookies aren't necessary for a functioning web experience. | Static sites, Pinboard (minimal session cookie), DuckDuckGo search, PPQ.AI |

**Scoring notes**: Check cookies in DevTools (Application > Cookies) on first visit in incognito. Count total, count third-party (domain differs from site domain), count persistent (expiry > session). Third-party cookies weigh more heavily than first-party. A single Google Analytics cookie is roughly 50%. Multiple ad-network cookies is 25% or below regardless of total count.

---

### 5.5b Third-Party Tracker Count

**What it measures**: Number of third-party network requests to tracking/analytics domains. Zero is ideal. Each tracker penalizes.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Tracker-infested. 15+ third-party tracking domains contacted on page load. Ad networks, analytics suites, fingerprinting services, data brokers, social media pixels all firing before the page renders. The product is a data collection platform that incidentally provides a service. | Ad-heavy media sites, free tier products monetizing through data, products with Facebook Pixel + Google Analytics + Hotjar + 10 more |
| 25% | Heavy tracking presence. 5-15 third-party tracker domains. Multiple analytics services, social media pixels (Facebook, Twitter), maybe a heatmap tool. Each tracker is individually "small" but together they create a comprehensive profile. | Most commercial web apps, e-commerce sites with retargeting stack, media companies |
| 50% | Moderate tracking. 2-4 third-party domains. Typically Google Analytics plus one or two others (Intercom, Segment, Mixpanel). The tracking stack is limited but still sends data to external services. | Average SaaS products, startups with standard analytics stack |
| 75% | Minimal external tracking. Zero or one third-party tracker. If analytics exist, they're self-hosted (Plausible, Umami) or a single privacy-respecting service. No social media pixels, no ad trackers, no heatmaps. | Products using self-hosted Plausible/Umami, Basecamp, indie products with minimal analytics |
| 100% | Zero third-party requests to tracking domains. All analytics (if any) are self-hosted. No pixels, no beacons, no fingerprinting. Network inspector shows only first-party requests and CDN/asset requests. | Signal web, Pinboard, static documentation sites, self-hosted products |

**Scoring notes**: Open DevTools Network tab in incognito, load the page, filter by third-party domains. Classify each external request: CDN/asset (not a tracker), analytics (tracker), ad network (tracker), social pixel (tracker). Count tracker domains, not requests — multiple requests to Google Analytics is one tracker. Known tracker lists (EasyList, Disconnect) help classify ambiguous domains.

---

### 5.5c Analytics Philosophy

**What it measures**: The approach to user analytics — from none (best) through privacy-respecting to surveillance-grade.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Full surveillance analytics stack. Google Analytics 4 (with enhanced measurement) plus multiple supplementary trackers (Hotjar session recording, FullStory, Mixpanel with user identification). Individual user journeys reconstructable. Data flows to multiple third parties who build cross-site profiles. The analytics know more about user behavior than the user does. | Products with GA4 + Hotjar + Facebook Pixel + Segment, enterprise SaaS with full-stack analytics |
| 25% | Standard surveillance-grade analytics. Google Analytics as primary with some supplementary tools. User sessions tracked with identifiers. Data sent to Google's ecosystem where it's combined with broader profile data. Standard in the industry but hostile to user privacy by design. | Most commercial web applications using Google Analytics with standard configuration |
| 50% | Hosted privacy-respecting analytics. Third-party service designed for privacy (Fathom, Simple Analytics). No cross-site tracking, no individual user identification, aggregate data only. But data still leaves the product's infrastructure — you're trusting a third party to be honest about their privacy claims. | Products using Fathom Analytics, Simple Analytics |
| 75% | Self-hosted privacy-respecting analytics. Plausible or Umami self-hosted — aggregate data that never leaves the product's infrastructure. No individual user tracking. No data shared with third parties. The product knows how many people visited, not who they are. | Products running self-hosted Plausible, self-hosted Umami, custom minimal analytics |
| 100% | No analytics at all, or server-side request logs only (access logs analyzed without client-side tracking). The product genuinely doesn't track user behavior beyond what the web server naturally records. No JavaScript analytics of any kind. | Signal, Pinboard, static sites, most CLI tools, open-source projects with no analytics |

**Tracking quality taxonomy** (score ranges by tracking category):
- **No tracking / server logs only**: 90-100%
- **Self-hosted privacy-respecting** (Plausible, Umami self-hosted): 75-90%
- **First-party analytics** (custom, no third-party data sharing): 70-85%
- **Privacy-respecting third-party** (Fathom, Simple Analytics hosted): 50-65%
- **Standard surveillance** (GA4, Mixpanel without user ID): 20-35%
- **Advertising/profiling** (GA4 + Facebook Pixel, session recording): 5-20%
- **Data brokering** (selling behavioral data to third parties): 5%

**Scoring notes**: Check page source and network requests for analytics scripts. Use the taxonomy above to classify. If multiple analytics tools are present, score based on the most invasive one. Self-hosted vs hosted matters because self-hosted means data stays on their infrastructure.

---

### 5.5d Cookie Consent Quality

**What it measures**: How the product handles cookie consent — from not needing it (best) to weaponizing consent against the user (worst).

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Consent as weapon. Content blocked until cookies accepted. No reject option, or reject button is hidden, grayed out, or requires navigating through 47 categories. "Accept All" is a large colorful button; "Manage Preferences" is a tiny gray link that leads to an unusable interface. Pre-checked boxes for all tracking categories. Consent is demanded, not requested. | News sites blocking content behind cookie walls, EU-hostile implementations with dark-pattern consent flows |
| 25% | Dark-pattern consent. Both Accept and Reject are technically available but visually manipulated — Accept is prominent and colored, Reject is destyled text. Rejecting requires more clicks than accepting. Pre-checked categories that must be individually unchecked. The implementation technically complies with regulation while violating its spirit. | Most enterprise websites, commercial SaaS with standard CMP (Consent Management Platform) default configurations |
| 50% | Honest consent with equal prominence. Accept All and Reject All are visually equal — same size, same styling, same number of clicks. No pre-checked categories. No content blocking. The banner is visible but not obstructive. Standard implementation that respects the user's choice without making it easy. | Well-implemented cookie banners with equal Accept/Reject buttons, products that took consent seriously |
| 75% | Minimal banner with reject-first design. Reject All is the prominent option. Accept requires explicit choice. Banner is small, non-blocking, appears once and remembers the choice forever. Or: the product sets no tracking cookies and shows a brief informational notice about functional cookies only. | Products with "We only use essential cookies" notices, minimal consent implementations |
| 100% | No banner needed. The product sets no cookies requiring consent — no tracking, no analytics, no third-party cookies. If only functional cookies are used (session auth), a brief notice may appear but no consent is required because there's nothing to consent to. The best cookie consent UX is no cookie consent UX. | Signal, Pinboard, static sites, products with zero tracking cookies |

**Scoring notes**: Visit in incognito from an EU IP (or add a GDPR test parameter if the product geo-targets consent). Score based on: banner presence and necessity, visual prominence of reject vs accept, number of clicks to reject all, pre-checked categories, content blocking until consent. A product that needs no banner because it has no tracking cookies scores 100% — not having the problem is better than solving it well.

---

### 5.5e DNT Respect

**What it measures**: Whether the product honors the Do-Not-Track browser header by modifying its tracking behavior.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | DNT actively disrespected. Tracking behavior identical regardless of DNT header. The product may even fingerprint users who set DNT (using the header itself as a tracking signal). No acknowledgment that DNT exists. | Most commercial web platforms, ad-supported services, products that treat DNT as irrelevant (which is most of the web) |
| 25% | DNT acknowledged in privacy policy but not honored in practice. The policy mentions DNT but tracking behavior is unchanged when the header is present. Lip service without implementation. **Note**: Acknowledging DNT and explicitly dismissing it ("We do not respond to DNT signals") is worse than silent ignorance — it demonstrates awareness of the user's preference and conscious choice to override it. Score 15-20% for explicit dismissal. | Products with "we acknowledge DNT" in legal text but no technical implementation, "We do not respond to DNT signals" in privacy policy |
| 50% | DNT partially honored. Some tracking disabled when DNT is set (e.g., analytics reduced to aggregate-only) but not all. Third-party trackers may still fire. The product makes an effort but doesn't follow through completely. | Products that disable their own analytics on DNT but don't control third-party scripts |
| 75% | DNT fully honored for first-party tracking. When DNT is set, no analytics, no tracking cookies, no behavioral data collection from first-party systems. Third-party resources (CDN, fonts) may still make requests but no tracker scripts load. Clear documentation of DNT behavior. | Products with documented DNT respect, privacy-focused services that disable analytics on DNT |
| 100% | DNT is moot because there's nothing to track. The product has no tracking to disable. DNT header makes no difference because the baseline behavior is already zero-tracking. Alternatively: the product explicitly documents that it honors DNT and verifiably does so. | Signal, products with zero analytics, privacy-first tools where DNT is the default behavior |

**Scoring notes**: Set DNT header in browser (or use a privacy-configured browser like Firefox with tracking protection). Compare network requests with and without DNT. If identical — the product ignores DNT. Note: most of the web ignores DNT, so a score of 0% here is common and expected. Products that genuinely honor it are rare and should be recognized. Products with no tracking score 100% by default because there's nothing to disable.

---

### 5.5f Minimal Permissions (Mobile)

**What it measures**: Whether a mobile app requests only permissions necessary for its core function, or hoards permissions for data collection.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Permission hoarding. Flashlight app requesting contacts, camera, microphone, location, and storage. Permissions unrelated to any visible feature. The app is a data collection operation disguised as a utility. | Notorious permission-hoarding free apps, games requesting contacts and location, utility apps with surveillance-grade permissions |
| 25% | Excessive permissions with weak justification. The app requests permissions for features that exist but aren't core (a notes app requesting camera "for document scanning" that 90% of users never use). Permissions requested on install, not on first use of the relevant feature. | Social media apps requesting all permissions upfront, productivity apps with bloated permission requests |
| 50% | Reasonable permissions with some excess. Core function permissions are justified. One or two additional permissions for secondary features. Permissions requested at time of use, not upfront. The app could function with fewer permissions but the extras aren't alarming. | Average well-designed apps with mostly justified permissions |
| 75% | Minimal permissions matching core function. Only permissions directly required for the primary use case. Secondary features degrade gracefully without optional permissions. Permissions requested contextually with clear explanation. A privacy-conscious user wouldn't be surprised by anything in the list. | Signal (contacts for finding other users, camera for photos — both core), well-designed single-purpose apps |
| 100% | Zero permissions or absolute minimum. The app functions without requesting any permissions beyond what the OS requires. If permissions are needed (camera for a camera app), it's exactly and only what the core function demands. No optional "nice to have" permission requests. | Simple calculator apps, offline-first tools, CLI tools with no system access |

**Scoring notes**: This check applies only to products with a mobile app (`[if:mobile]`). Web-only products exclude this from the 5.5 composite. Review the app's permission manifest (Android: Play Store listing or APK manifest; iOS: App Store privacy nutrition label). Count permissions, classify as core-function vs. nice-to-have vs. unjustified. Each unjustified permission is a significant penalty.

---

### 5.5g Telemetry Opt-In (Mobile)

**What it measures**: Whether telemetry and crash reporting default to off (user opts in) or on (user must opt out) — and whether there's any control at all.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Telemetry with no user control. The app collects usage data, crash reports, and behavioral analytics with no setting to disable it. No mention in onboarding, no toggle in settings. The user doesn't know it's happening and can't stop it. | Apps with hardcoded analytics SDKs and no opt-out, many free mobile games, apps with no privacy settings |
| 25% | Telemetry defaults ON with buried opt-out. The app collects data by default. An opt-out toggle exists but is buried in Settings > Privacy > Analytics > Advanced. Onboarding doesn't mention data collection. Most users will never find the toggle. | Most mainstream mobile apps, social media apps with deeply buried analytics toggles |
| 50% | Telemetry defaults ON with visible opt-out. The app collects data by default but the toggle is in an obvious location (top-level Settings > Privacy). Onboarding may mention analytics briefly. A user who cares about privacy can find and disable it within a minute. | iOS apps that surface Apple's analytics prompt, apps with clear privacy settings sections |
| 75% | Telemetry defaults OFF with opt-in request. On first launch, the app asks if you'd like to share crash reports and usage data. Default is off. The request is honest about what's collected and why. No nagging if you decline. | Firefox mobile (telemetry opt-in), privacy-conscious apps with honest onboarding prompts |
| 100% | No telemetry, or fully transparent opt-in with zero defaults. The app collects no telemetry by default. If crash reporting exists, it's triggered manually ("Send report?") with visible contents. The user is in complete control of every byte that leaves their device. | Signal (minimal, transparent), open-source apps with no analytics, apps that show you exactly what data would be sent before you approve |

**Scoring notes**: This check applies only to mobile/desktop apps (`[if:mobile]`). Web-only products exclude this from the 5.5 composite. Check: does the app have a telemetry/analytics toggle in settings? What is the default state? Was opt-in/opt-out mentioned during onboarding? Default-ON with easy opt-out (50%) is fundamentally different from default-OFF with opt-in (75%) — the default is what 90% of users experience.

---

### 5.5h No Background Data Collection (Mobile)

**What it measures**: Whether the app collects data when not in active use — background location tracking, silent network requests, background analytics pings.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The app is a background surveillance tool. Continuous location tracking when the app isn't open. Regular network requests to analytics/ad servers from background processes. Battery drain from background data collection. The app is working harder when you're not using it than when you are. | Apps with persistent background location access, ad-SDK-heavy apps with background beacons, social media apps with continuous background syncing |
| 25% | Significant background activity beyond functional needs. Background refresh sends behavioral data, not just content updates. Location accessed in background "for features" that don't need real-time location. Network requests to analytics domains visible in background activity. | Social media apps with aggressive background refresh, fitness apps that over-collect location data |
| 50% | Some background activity, mostly functional. Background refresh pulls new content (legitimate for messaging, email). Occasional analytics ping in background but not continuous. Location used in background only when actively navigating. The background activity is mostly justifiable but includes some tracking. | Messaging apps with push notification infrastructure, email apps with background fetch |
| 75% | Minimal background activity, fully functional. Background activity limited to push notification receipt and content sync. Zero analytics or tracking in background. No background location access. The app is effectively dormant when not in foreground except for necessary communication infrastructure. | Signal (background activity limited to message receipt), well-designed messaging apps with minimal background footprint |
| 100% | Zero background activity. The app does nothing when not in foreground. No background refresh, no background location, no background network requests. Push notifications arrive via OS-level infrastructure (APNs/FCM), not app-level polling. The app respects that "closed" means "not running." | Simple utility apps, offline-first tools, apps with no background processing |

**Scoring notes**: This check applies only to mobile/desktop apps (`[if:mobile]`). Web-only products exclude this from the 5.5 composite. On iOS: check Settings > General > Background App Refresh. On Android: check battery usage details for background activity. Monitor network requests while the app is in background (use a network proxy like Charles or mitmproxy). Any analytics-domain requests from background processes are a strong signal of 25% or below.

---

## 5.6 RSS or Equivalent

**What it measures**: Whether a content-publishing product provides a machine-readable feed (RSS, Atom, JSON Feed) that lets users consume content without the product's interface.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Content is deliberately walled off from machine consumption. No RSS feed despite publishing regular content. API exists but excludes content endpoints. Content only accessible through the product's interface, ensuring you must visit the site (and see the ads/tracking/engagement loops) to read it. The product holds your attention hostage. | Twitter/X (removed RSS), Facebook (no RSS for pages), Instagram (no feed export), products that deliberately killed their RSS feeds |
| 25% | Feed exists but is crippled. RSS feed provides titles and excerpts only — you must click through to the site for full content. Feed is not discoverable (no `<link>` tag, not in page source, not documented). Or: feed exists but is broken/stale (hasn't updated in months despite new content). A token gesture toward openness. | Blogs with excerpt-only RSS feeds, products with undiscoverable or broken feeds |
| 50% | Functional feed with limitations. Full-content RSS feed exists and works. Discoverable via standard methods (`<link rel="alternate">`). But: limited to recent items, no category/tag feeds, no customization. The feed works but it's the minimum viable implementation. | Average blogs and news sites with basic RSS support |
| 75% | Well-implemented feed infrastructure. Full-content RSS/Atom feed with proper metadata. Category/tag-specific feeds available. Feed is discoverable and documented. Enclosures for media content (podcasts). The feed is a first-class distribution channel, not an afterthought. | Basecamp's blog (full RSS), well-maintained tech blogs, podcast feeds with full metadata |
| 100% | Feed is the product's native output format. JSON Feed, RSS, or Atom treated as primary distribution. Content is designed to be consumed anywhere, not just on the product's site. Multiple feed formats available. The product embraces the open web's syndication infrastructure. | Hacker News (RSS/API as primary access method), well-designed podcast platforms, Nostr-based content (protocol-native distribution) |

**Scoring notes**: This check applies only to content-publishing products (`[if:content]`). Static tools, protocols, CLI apps without content feeds are N/A. Check: does `<link rel="alternate" type="application/rss+xml">` exist in page source? Does `/feed`, `/rss`, or `/atom.xml` resolve? Is the feed full-content or excerpt-only? Is it current? Excerpt-only RSS in 2026 is a deliberate choice to withhold content from open consumption — score 25%.

---

## 5.7 Cancel/Leave in One Click

**What it measures**: How easy it is to cancel a subscription, delete an account, or remove your data — one step versus a dark-pattern obstacle course.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Leaving is a hostage negotiation. Account deletion requires contacting support via email, waiting for a response, confirming multiple times, and waiting a "processing period." Unsubscribe requires calling a phone number during business hours. Cancel buttons don't exist — you must navigate to a hidden settings page, confirm 3 times, endure a guilt-trip retention flow, and still might find you're charged next month. The product treats your departure as an error to be corrected. | Cable TV cancellation flows, gym memberships requiring certified mail, enterprise SaaS requiring sales calls to cancel |
| 25% | Cancellation exists but is deliberately difficult. The cancel button is real but buried (Settings > Account > Billing > Subscription > Manage > Cancel). A retention flow presents 4-5 screens of offers, guilt trips, and "Are you sure?" prompts before the final cancel. Data export is partial or requires a support request. Unsubscribe from emails leads to a "preferences page" instead of actually unsubscribing. | Amazon Prime cancellation flow (multiple retention screens), products with multi-step guilt-trip cancellation |
| 50% | Cancellation is possible in a reasonable number of steps. Cancel button is findable within 2-3 clicks. One confirmation screen (acceptable). Brief retention offer (one screen, one "No thanks" click). Data export available but requires manual request and processing time. The process works but isn't designed to be easy. | Average SaaS cancellation with a single retention offer, products with export-via-request |
| 75% | Cancellation is straightforward. Cancel or delete account available in Settings within 1-2 clicks. One confirmation prompt, no retention flow, no guilt. Data export is self-service and immediate (or within hours). Unsubscribe from emails is one click, immediate, no login required. The product lets you leave with dignity. | Basecamp (cancel anytime, export your data), well-designed SaaS with honest cancellation, Stripe (account closure is clear) |
| 100% | Leaving is as easy as arriving. One-click cancel with immediate effect. Self-service data export in standard formats (JSON, CSV). Account deletion is permanent and verifiable. No retention flow, no guilt, no delay. The product assumes you've already decided and respects that decision. Or: no account to cancel because the product is pay-per-use or open. | PPQ.AI (no subscription to cancel), Signal (delete account in settings, immediate), Pinboard (archive export, cancel anytime) |

**Scoring notes**: Test the full cancellation/deletion flow. Count clicks from logged-in homepage to confirmed cancellation. Count retention screens. Check: is data export self-service? Is unsubscribe one-click? Does cancel take effect immediately or after a "processing period"? Each additional step beyond confirmation is a penalty. A product with no account (pay-per-use, no login required) scores 100% by default.

---

## 5.8 No Double-Dipping

**What it measures**: Whether a paid product also monetizes user attention through ads, sponsored content, or data selling. You pay OR they monetize your attention, not both.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Full double-dip. The product charges a subscription AND shows ads AND sells user data. Premium tiers still include ads. The product extracts value from every direction simultaneously — your wallet, your attention, and your data are all revenue streams. | Cable TV (subscription + ads), products with paid tiers that still show ads and sell data, Hulu's original ad-supported paid tier |
| 25% | Paid product with significant attention monetization. Subscription exists but the experience includes sponsored content, partner promotions, or "recommended" items that are paid placements. Not traditional display ads, but commercial influence in the content you're paying for. | Streaming services with product placement, paid apps with "featured" (sponsored) content, subscription news with native advertising |
| 50% | Paid product with minor monetization overlap. The premium tier is ad-free but the free tier has ads (acceptable — you're choosing which value exchange). Or: the paid product includes occasional first-party promotions for upgrades (annoying but not third-party monetization). The double-dip is mild and internal. | Freemium products with ad-free paid tiers, SaaS with upsell banners in free tier |
| 75% | Clean value exchange. Paid means paid — no ads, no sponsored content, no data monetization. Free tier may exist with a different value exchange (feature-limited, not ad-supported). The product picks one business model and commits to it. Minor exceptions: affiliate links in content that are disclosed. | Basecamp (paid, no ads, no free tier), most honest SaaS subscriptions, Pinboard |
| 100% | Pure value exchange with zero attention or data monetization. You pay for the service. The service works for you. No ads anywhere in any tier. No data sold. No sponsored content. No affiliate links. No partner integrations that benefit the product instead of the user. Revenue comes from one source: users paying for value. | Signal (donation-funded, zero monetization), PPQ.AI (pay per query, nothing else), one-time-purchase software with no telemetry |

**Scoring notes**: Check: does the paid product show ads? Does it include sponsored/promoted/featured content that users didn't ask for? Does the privacy policy mention data sharing with partners "to improve your experience"? A free tier with ads alongside a paid ad-free tier is 50% (acceptable trade-off). A paid tier that still includes ads is 25% or below. Disclosed affiliate links in content are a minor penalty (75% ceiling, not lower).

---

## 5.9 No Product Coercion

**What it measures**: Whether the product pushes users toward a specific platform, app, or browser through nagging, degraded experience, or forced redirects.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Active platform coercion. Mobile web redirects to app store with no way to continue in browser. "This experience is better in our app" overlay that can't be dismissed. Desktop site says "works best in Chrome" and degrades in other browsers. The product refuses to serve you unless you use it on their preferred platform. | Instagram mobile web (forces app for many features), products that redirect mobile browsers to app store, sites that block Firefox/Safari |
| 25% | Persistent coercion nagging. "Download our app" banner on every mobile page visit, re-appearing after dismissal. "Better in Chrome" banners. Features artificially withheld from web to force app installation. The product works in your browser but makes sure you know it doesn't want you there. | Reddit mobile web (persistent app banner, degraded experience), products with sticky "get the app" banners that return every session |
| 50% | Occasional platform suggestions without degradation. "Get our app" prompt on first mobile visit, dismissible, doesn't return for 30+ days. All features available on all platforms. Browser compatibility covers major browsers. The suggestion exists but it's a suggestion, not a demand. | Average SaaS with first-visit app promotion, products with "install PWA" prompts |
| 75% | No platform coercion. The product works equally well on all supported platforms. No "download our app" prompts. No browser-specific messaging. If a mobile app exists, the mobile web experience is fully functional. The product meets you where you are. | Basecamp (full web experience, app is optional), products that treat web and app as equal citizens |
| 100% | Platform-agnostic by design. Works in any browser, on any device, with no preference expressed or implied. No app-store dependency. Mobile web is a first-class experience. The product adapts to your platform choice without comment or complaint. Or: the product is inherently platform-agnostic (protocol, API, CLI). | Hacker News (works everywhere), Signal (works on all platforms without nagging), web-first products with optional native apps, Nostr clients |

**Scoring notes**: Visit the product on mobile web (not in-app browser). Count "download our app" prompts. Check if they persist after dismissal. Compare feature availability between mobile web and native app — if features are withheld from mobile web to force app adoption, score 25% or below. Test in Firefox, Safari, and Chrome — if any major browser gets a degraded experience with a "switch to Chrome" message, score 25% or below.

---

## 5.10 No Dark Patterns

**What it measures**: Absence of deceptive UX patterns — confirmshaming, hidden costs, trick questions, roach motels, bait-and-switch, and forced continuity.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product is a dark pattern anthology. Confirmshaming on decline buttons ("No thanks, I don't want to save money"). Hidden costs that appear at checkout. Pre-checked boxes for newsletter signup and terms changes. Bait-and-switch (free trial becomes paid without clear warning). Roach motel (easy to sign up, impossible to leave). Trick questions with double negatives. The product is designed to manipulate every decision you make. | Notorious dark-pattern e-commerce, subscription traps, products featured on darkpatterns.org |
| 25% | Multiple dark patterns present in key flows. Confirmshaming on at least one decline button. Pricing page hides the monthly cost (shows annual-divided-by-12 prominently). Pre-checked opt-ins for marketing. Cancellation flow uses visual tricks (bright "Keep subscription" vs. muted "Cancel"). Not comprehensive manipulation but deliberate at critical conversion points. | Products with confirmshaming CTAs, SaaS with hidden monthly pricing, subscription services with misdirecting cancellation flows |
| 50% | Occasional borderline patterns. One instance of a suspect UI choice — maybe the "No" button is less prominent than "Yes" in one modal. Pricing is mostly transparent but the cheapest plan is hidden or deemphasized. No confirmshaming, no hidden costs, no trick questions. The product isn't manipulative but it's not above a nudge. | Average SaaS with mildly biased UI choices, products with "recommended" plan pre-selected |
| 75% | No dark patterns detected. All choices presented equally. Pricing is transparent and all tiers are visible. Decline buttons are neutral ("No thanks" or "Cancel"). No pre-checked boxes. No hidden costs. The product respects your autonomy in every interaction. Rare edge case: a mildly leading question in an optional survey. | Basecamp (transparent pricing, no dark patterns), Stripe (clear flows), well-designed indie products |
| 100% | Anti-dark-pattern design. The product actively ensures informed decisions. Pricing includes comparison tools. Decline is as easy as accept. Warnings before irreversible actions. Plain language everywhere — no double negatives, no legal-speak in consent flows. The UX is designed as if the user's lawyer is watching. | PPQ.AI (pay per use, no tricks), Signal (zero manipulation), products with "user-first" as a demonstrable design principle |

**Scoring notes**: Walk through every conversion flow: signup, upgrade, cancel, decline-offer, unsubscribe. Check for: confirmshaming (emotional language on decline buttons), hidden costs (fees appearing at checkout), pre-checked boxes, visual manipulation (bright accept vs muted decline), forced continuity (trial-to-paid without clear warning), trick questions (double negatives), roach motels (easy in, hard out), **import without matching export** (the product lets you import data easily but has no export — you're invited in but can't leave with your work). Score on the worst pattern found, not the average — one dark pattern in a critical flow (checkout, cancellation) is enough to cap at 50%.

---
