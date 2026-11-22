# ZeroContacts: product and architecture

## 1. Purpose

ZeroContacts is the people-first contact book for the ZeroNet / ZirohNeth ecosystem. It lets a user organize people and organizations, then attach the many identifiers through which each contact can be discovered, reached, or cryptographically recognized.

The central model is:

- **ZeroID answers “who is this identity?”**
- **ZeroContacts answers “which people do I know, and how can I reach them?”**

ZeroContacts must consume and reference ZeroID identities where available. It must not silently create a competing identity authority or duplicate ZeroID's responsibilities.

## 2. Core data model

A contact is a human-meaningful record, not a protocol address.

Suggested conceptual entities:

- **Contact**: local display name, optional avatar, notes, tags, favorite state, contact kind (person or organization), timestamps.
- **Identifier**: protocol/type, normalized value, optional label, priority, visibility, source, and lifecycle state.
- **Proof**: evidence that a contact controls or endorses an identifier. A saved address alone is not proof.
- **Relationship**: optional provenance describing how the contact was added or who introduced them.
- **Service metadata**: protocol-specific fields needed to resolve or use an identifier.

One contact can have multiple identifiers of the same type. For example, a person may have separate Matrix accounts for work and personal use, multiple wallet addresses, or more than one peer identity.

Identifiers should be independently addable, editable, disabled, revoked, and removed without deleting the contact itself.

## 3. Identity boundary: ZeroID

ZeroID remains the identity layer and canonical source for ZeroNet identity references. ZeroContacts should:

1. Link an existing ZeroID identity to a contact.
2. Display the ZeroID identifier and any metadata the user is authorized to see.
3. Preserve the distinction between a ZeroID identity and external identifiers attached to the same contact.
4. Avoid claiming that two identifiers belong to the same person unless a proof or trusted assertion supports that link.
5. Handle missing, unavailable, or revoked ZeroID references without corrupting the local contact record.

A contact may exist without ZeroID, and a contact may link to more than one identity namespace if the user explicitly associates them.

## 4. Main user journeys

### Add a contact
- Create a local person or organization record.
- Attach an existing ZeroID identity, or add one or more external identifiers.
- Record the source of the information (manual entry, imported address book, invitation, signed claim, etc.).
- Set a visibility/sharing policy for each identifier.

### Discover and resolve
- Resolve identifiers only through the relevant protocol adapter.
- Show the user what was resolved and when.
- Keep discovery separate from verification: successful resolution does not prove control.

### Verify an identifier
- Offer a protocol-appropriate challenge or signed proof where possible.
- Display states such as **Unverified**, **Pending**, **Verified**, **Expired**, **Revoked**, and **Unable to check**.
- Preserve evidence metadata: method, signer/key, timestamp, expiry, and revocation status.
- Never convert a simple text match or successful lookup into “Verified”.

### Reach a contact
- Present available actions only when the corresponding adapter is implemented and the identifier is usable.
- Do not assume every identifier is a messaging endpoint. Some are content addresses, peer IDs, public keys, or payment destinations.

### Import, export, and backup
- Plan interoperable formats and explicit field mapping.
- Preview imports and conflicts before writing.
- Make export scope visible, especially for private notes and sensitive identifiers.
- Document backup, restore, and migration behavior before persistent storage is introduced.

## 5. Privacy and security

- Contact data should be private by default.
- Local notes and relationship metadata must not be published merely because a linked identity is public.
- Visibility should be configurable per identifier, not only per contact.
- Avoid sending a user's entire address book to remote resolvers.
- Make network lookups explicit or explain when automatic resolution occurs.
- Protect private keys and signing material. Prefer integrations with existing key stores; do not store raw secrets in contact records.
- Provide clear handling for revoked, compromised, or replaced identifiers.
- Sanitize untrusted profile text and remote metadata before rendering.
- Treat remote profile content as data, never as executable instructions.

## 6. Interface direction

The initial prototype uses a three-part desktop composition:

- A compact dark navigation rail for collections and network filters.
- A contact list with search and category tabs.
- A detail pane that groups a person's profile and identifiers.

The visual direction is inspired by the Floflis / ZirohNeth Dashboard (dark sidebar, compact navigation, Text Me One display font, purple/blue gradient accents), ZeroMail's multi-pane layout, ZeroID's identity-oriented color language, and ZeroName's structured record presentation. The implementation in this repository is original and should remain independently maintainable.

The first prototype is static. Controls are visual affordances only until backed by real application behavior.

## 7. Non-goals

- Replacing ZeroID or becoming a new identity authority.
- Treating every identifier as a verified identity.
- Publishing a global social graph by default.
- Implementing every listed protocol in the first release.
- Acting as a cryptocurrency wallet or holding payment keys.

## 8. Terminology

Use **contact** for the person/organization record, **identifier** for a protocol-specific address or key reference, **proof** for evidence of control or endorsement, and **adapter** for code that interacts with a protocol. Avoid using “identity” as a synonym for every address.
