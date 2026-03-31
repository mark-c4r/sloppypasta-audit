# Sovereignty Verification Reference

Self-contained reference for testing product sovereignty and privacy.
Used by checks: 5.5 (privacy composite), 6.1-6.13 (all sovereignty checks)

## Rugpull Resistance (6.1)

Test: Can the operator unilaterally...
- Lock you out of your account?
- Change terms of service retroactively?
- Seize or freeze your assets/data?
- Shut down the service with no migration path?

Method: Read ToS. Check for "we may terminate at any time" clauses. Check for asset custody model.

Protocol = inherently resistant (no single operator). Platform = vulnerable by design.

## Exit Cost (6.2)

Test: Can you leave with everything?
- Is there an export function?
- What formats does it export? (Standard = JSON, CSV, markdown. Proprietary = bad.)
- Can you export your social graph?
- How long does export take? (Instant = good. "Request and wait 30 days" = bad.)

Method: Actually try to export. Time it. Check formats.

## Identity Sovereignty (6.3)

Scale (score directly from this):
- 100%: Keypair-based identity (Nostr nsec/npub, Bitcoin keys)
- 75%: Minimal account (username only, no email required)
- 50%: Email required, no verification
- 35%: Email + verification required
- 20%: Phone number required
- 5%: Government ID required (always lowest -- never higher regardless of other factors)

Method: Go through signup flow. Note every piece of identity information required.

## Protocol vs Platform (6.4)

Test: What happens if this company disappears tomorrow?
- 100%: Open protocol -- any client can connect (Nostr, Bitcoin, email, RSS)
- 75%: Open-source with federated instances (Mastodon, Matrix)
- 50%: Open-source but single-instance dominance
- 25%: Proprietary with documented API
- 5%: Proprietary, closed, single point of failure

Method: Check architecture docs. Is there a protocol spec? Multiple clients?

## Self-Hostable or Auditable (6.5)

Test: Can you run it yourself? Can you verify what it does?
- Check: Docker/install instructions available?
- Check: License allows self-hosting?
- Check: Documentation for self-hosting exists and is maintained?
- Fallback: Is source code at least readable/auditable?

## Privacy-Preserving Payment (6.6)

Test: Can you pay without revealing identity?
- 100%: Lightning/ecash/Monero accepted -- no identity linkage
- 75%: Bitcoin on-chain accepted (pseudonymous but traceable)
- 50%: Crypto accepted but requires account with email
- 25%: Credit card only but no unnecessary data collection
- 5%: Credit card + full identity verification + data sharing with third parties

## Source Code Availability (6.7)

Scale:
- 100%: FOSS with active development (commits, issues, PRs)
- 75%: Source-available with restrictive license (BSL, SSPL)
- 50%: Partial source (core open, proprietary additions)
- 25%: Proprietary but free to use
- 5%: Proprietary, paid, closed

## Provenance Traceable (6.8) [if:content]

Test: Is content signed, timestamped, attributed?
- 100%: Cryptographic provenance (Nostr events, signed commits)
- 75%: Verifiable attribution (author + date + edit history)
- 50%: Attribution present but not verifiable
- 25%: Minimal attribution (author name only)
- 5%: No attribution, no timestamps, no provenance chain

## Conditional Sovereignty Checks

### Distribution Independence (6.9) [if:mobile]
- 100%: Sideloadable APK + F-Droid
- 75%: App Store + sideload option
- 50%: App Store only but no lock-in features
- 5%: App Store only, uses platform-locked APIs

### No Google Play Services Dependency (6.10) [if:mobile]
- 100%: Works fully on GrapheneOS/CalyxOS
- 50%: Core features work, push notifications don't
- 5%: Requires Google Play Services, won't launch without

### Key Management Sovereignty (6.11) [if:identity]
- 100%: NIP-07/NIP-46 external signing (keys never touch the app)
- 75%: App holds key with export/backup option
- 50%: App holds key, no export
- 5%: Custodial (platform holds your keys)

### Relay/Node Independence (6.12) [if:messaging/social]
- 100%: Works with any relay/node, user chooses
- 75%: Recommended set but user can add/remove
- 50%: Specific relays required but multiple available
- 5%: Single centralized server, no relay choice

### Custodial vs Non-Custodial (6.13) [if:payments]
- 100%: Non-custodial (you hold keys, you sign transactions)
- 50%: Custodial with withdrawal (like an exchange)
- 5%: Fully custodial, no withdrawal to self-custody

## Privacy Composite Sub-Checks (5.5)

These 8 sub-checks compute the 5.5 composite score via geometric mean:

### 5.5a Cookie Count (Universal)
- 0 cookies = ideal
- First-party session cookie only = acceptable
- Each third-party cookie penalizes

### 5.5b Third-Party Tracker Count (Universal)
- Check network inspector
- 0 trackers = ideal
- Each tracker penalizes proportionally

### 5.5c Analytics Philosophy (Universal)
- None (best) > self-hosted privacy-respecting (Plausible/Umami) > hosted privacy (Fathom) > Google Analytics > GA + multi-tracker (worst)

### 5.5d Cookie Consent Quality (Universal)
- No banner needed (best) > reject-all prominent > accept-all prominent > accept-all dark pattern > content-blocked-until-accept (worst)

### 5.5e DNT Respect (Universal)
- Honors Do-Not-Track header > ignores it > no mechanism at all

### 5.5f Minimal Permissions ([if:mobile])
- Requests only what's needed for core function
- Each unnecessary permission penalizes

### 5.5g Telemetry Opt-In ([if:mobile])
- Defaults OFF, user opts in (best) > defaults ON, user can opt out > no control (worst)

### 5.5h No Background Data Collection ([if:mobile])
- No data collection when app is not in active use

Mobile sub-checks (5.5f-h) are N/A for web-only products -- excluded from composite geomean.

## How to Use This Reference

1. For each applicable sovereignty check, follow the test procedure
2. Score using the scales provided (they map directly to scale anchors)
3. For conditional checks, first determine if the condition applies
4. If condition does not apply, mark N/A (excluded from geomean)
5. If condition applies and check scores poorly, it penalizes the score
