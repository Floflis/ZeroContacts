# ZeroContacts roadmap

This roadmap separates product direction from delivered functionality. A checkbox should be marked complete only after the feature exists, is tested, and is documented.

## Phase 0 · Foundation and design

- [x] Establish the people-first product boundary: ZeroContacts consumes ZeroID; it does not replace it.
- [x] Add initial static responsive interface concept.
- [x] Document core entities, user journeys, privacy principles, and terminology.
- [x] Catalogue candidate identifier families and integration considerations.
- [ ] Review visual direction and accessibility with maintainers.
- [ ] Agree on supported runtime, framework, and persistence strategy.

## Phase 1 · Contact book core

- [ ] Define versioned contact and identifier schemas.
- [ ] Implement create, read, update, archive, and delete for local contacts.
- [ ] Support person and organization contact kinds.
- [ ] Support multiple identifiers of the same protocol per contact.
- [ ] Add search, tags, favorites, and sorting.
- [ ] Add import/export with preview, conflict handling, and privacy warnings.
- [ ] Add backup and restore tests.

## Phase 2 · ZeroNet identity integration

- [ ] Define the ZeroID reference contract and compatibility expectations.
- [ ] Link existing ZeroID identities to local contacts.
- [ ] Display ZeroMe/profile references where available.
- [ ] Handle missing, unavailable, changed, and revoked identity references.
- [ ] Document trust boundaries and avoid implying that a linked external address is verified.

## Phase 3 · Peer and content identifiers

- [ ] Evaluate CJDNS and Yggdrasil identifiers.
- [ ] Evaluate iroh endpoint/peer references.
- [ ] Evaluate IPFS Peer IDs and CIDs, distinguishing peers from content.
- [ ] Evaluate libp2p Peer IDs and multiaddresses.
- [ ] Define adapter interfaces, resolution timeouts, offline behavior, and privacy controls.

## Phase 4 · Messaging, social, and developer identities

- [ ] Evaluate Matrix and XMPP.
- [ ] Evaluate Nostr and ActivityPub/Fediverse identities.
- [ ] Add email and OpenPGP fingerprint support.
- [ ] Evaluate SSH fingerprints and DID/WebFinger resolution.
- [ ] Add GitHub/GitLab/Codeberg/Gitea/Forgejo profile references.
- [ ] Evaluate Mercurial and Pijul forge references.

## Phase 5 · Verification and trust

- [ ] Define a protocol-neutral proof record with protocol-specific evidence.
- [ ] Implement signed challenge/response where supported.
- [ ] Display Unverified, Pending, Verified, Expired, Revoked, and Unable to check states.
- [ ] Add key rotation and revocation workflows.
- [ ] Make proof scope explicit and prevent cross-protocol trust assumptions.

## Phase 6 · Financial identifiers and advanced privacy

- [ ] Evaluate Bitcoin, Lightning, Ethereum/EVM, Litecoin, Monero, Zcash, Solana, TON, and Gnosis identifiers.
- [ ] Separate payment destinations from identity and messaging identifiers.
- [ ] Add per-identifier visibility and sharing policies.
- [ ] Add privacy review for resolver traffic and address-book export.
- [ ] Perform security review before handling any signing or key-store integration.

## Release gates

A phase is not complete merely because an identifier can be typed into a text field. Each adapter needs normalization, validation, tests, documentation, privacy review, and clearly stated verification semantics. No roadmap item should be described as shipped until its implementation is present.
