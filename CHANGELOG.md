# Changelog

All notable changes to the Komiku Standard Identifier (KSI) specification will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

---

## [1.1.0] - 2025-07-26

### Added
- Greatly expanded the "Frequently Asked Questions (FAQ)" section with 4 new common questions and answers for authors, developers, and publishers.

### Changed
- Revised and enhanced several sections.

---

## [1.0.0] - 2025-07-25

### Added
- **Initial public release of the Komiku Standard Identifier (KSI) specification.**
- Defined the official KSI string format: `kmi:[format]-[timestamp]-[rand]`.
- Established the core components:
    * `kmi`: The official Komiku namespace.
    * `[format]`: The 2-letter code for the standard (`wn`, `wt`).
    * `[timestamp]`: The 64-bit Unix Timestamp in milliseconds.
    * `[rand]`: The 4-character random suffix for collision prevention.
- Outlined the purpose and function of the central KSI Registry.
- Provided a detailed comparison with the ISBN system to clarify the KSI's role for web-native content.
- Included practical use cases, implementation notes, and an FAQ for developers and creators.