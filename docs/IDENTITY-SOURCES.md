# Identity types and integration catalogue

This document records candidate identifier families discussed for ZeroContacts. Inclusion means “consider supporting or displaying this type”, not “implemented” or “verified”. Protocol adapters must be evaluated individually for maintenance, security, UX, and licensing.

## ZeroNet / ZirohNeth

- **ZeroID**: primary identity reference in the ZeroNet ecosystem. Integrate by linking to ZeroID; do not duplicate its identity role.
- **ZeroMe**: social/profile reference associated with a person.
- **CJDNS**: network public key / address reference.
- **Yggdrasil**: public key and peer/network addressing information.
- **iroh**: endpoint/peer identifiers and, where relevant, relay or discovery metadata.
- **IPFS**: Peer ID and content identifiers (CIDs). A CID identifies content, not a person; label it accordingly.
- **libp2p**: Peer ID and multiaddress. A peer ID is a network identity, not automatic proof of a human identity.

## Messaging and social protocols

- **Matrix**: Matrix user IDs and optional server/device context.
- **XMPP**: Jabber IDs (JIDs).
- **Nostr**: public key / npub and relay hints.
- **ActivityPub**: actor/profile URLs, including Fediverse identities.
- **Email**: one or more email addresses.
- **WebFinger**: discovery handle/resource reference; usually a resolver input rather than a standalone proof.
- **OpenPGP**: public-key fingerprint and key distribution references.
- **SSH**: public-key fingerprint, with clear distinction between a key fingerprint and a login endpoint.
- **DID**: decentralized identifier plus method-specific resolution metadata.

## Naming and profile discovery

- **ENS** and other DNS-linked naming systems.
- **DNS names** and optional OpenAlias-style records.
- **Mastodon/Fediverse handles** as user-friendly aliases, with the canonical actor URL retained.
- **Git hosting profiles**: GitHub, GitLab, Codeberg, Gitea, and Forgejo.
- **Developer forge identities**: Mercurial and Pijul hosting references where available.

## Financial and payment identifiers

These are sensitive routing destinations and must be visually separated from messaging and identity claims.

- Bitcoin addresses and Lightning invoices/addresses (with expiry and network context where applicable).
- Ethereum addresses and ENS names.
- Litecoin addresses.
- Monero addresses.
- Zcash addresses.
- Solana addresses.
- TON addresses.
- Gnosis / EVM-compatible addresses and chain identifiers.

A wallet address does not prove that its controller is the named contact. Avoid balance lookups or transaction surveillance as a default contact feature.

## Other peer-to-peer and decentralized systems

Candidate integrations to evaluate:

- Hypercore / Hyperdrive identifiers.
- Holochain agent keys.
- Secure Scuttlebutt (SSB) public identities.
- GNUnet identities.
- Tor onion service addresses.
- I2P destinations, only if a future product decision explicitly includes I2P.

## Identifier metadata

Where applicable, an identifier record may include:

- Canonical value and human-readable alias.
- Protocol and network (mainnet/testnet, server, chain, relay, or namespace).
- Purpose: profile, messaging, peer routing, content, signing, code hosting, or payment.
- Source and date added.
- Verification state and proof method.
- Visibility/sharing policy.
- Last successful resolution/check and expiry.
- Revocation or replacement relationship.

Do not force all identifier types into a single “address” field. Content CIDs, public keys, peer IDs, profile URLs, and payment destinations have different semantics.

## Verification vocabulary

Use explicit, non-overlapping states:

- **Unverified**: stored, but no proof checked.
- **Pending**: a challenge or external check is in progress.
- **Verified**: a defined proof succeeded and its scope is shown.
- **Expired**: proof validity period ended.
- **Revoked**: issuer or owner revoked the claim/key.
- **Unable to check**: no reliable check is currently available.

Verification is scoped. Proving control of one Matrix account does not prove control of an IPFS peer ID or a wallet address.

## Adapter policy

Each adapter should document:

1. Canonical identifier syntax and normalization rules.
2. Whether resolution is local, remote, or peer-to-peer.
3. What data is disclosed to third parties during resolution.
4. What constitutes proof of control.
5. Key rotation and revocation behavior.
6. Failure modes and offline behavior.
7. Whether the protocol is suitable for a “reach contact” action or only display/reference.
