# ZeroContacts

Manage people and their reachable identities across ZeroNet and ZirohNeth.

ZeroContacts is the contact-book layer: it organizes people, their identity references, and the ways you can reach or verify them. It consumes identity information from **ZeroID** rather than replacing it.

## Project status

This pull request establishes the initial visual direction, product documentation, and roadmap. The interface is a static design prototype; persistence, discovery, protocol adapters, and cryptographic verification are planned work, not implemented features.

## Design direction

The visual language takes inspiration from:

- **Floflis / ZirohNeth Dashboard** for its compact dark navigation, Text Me One display typography, and purple-blue gradient accents.
- **ZeroMail** for its multi-pane information architecture.
- **ZeroID** for the identity-oriented visual vocabulary.
- **ZeroName** for structured, readable identifier and record presentation.

The implementation uses its own markup, styles, and logo artwork rather than depending on another project's runtime.

## Documentation

- [Product and architecture overview](docs/ZEROCONTACTS.md)
- [Identity types and integrations](docs/IDENTITY-SOURCES.md)
- [Roadmap](ROADMAP.md)

## Guiding principles

1. A person is the contact; identifiers are ways to identify, address, or verify that person.
2. One contact may have many identifiers, including multiple identifiers of the same protocol.
3. ZeroID remains the identity authority. ZeroContacts is its address book.
4. Verification status must be explicit. An identifier being saved is not proof of ownership.
5. Privacy and user-controlled disclosure are first-class requirements.
6. Planned integrations must not be presented as implemented until they actually work.

## Development

Open `index.html` in a browser to inspect the static prototype. No build system or JavaScript framework is required for this first design/documentation milestone.
