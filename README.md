<div align="center">
  <img src="/assets/wordmark.png" alt="Komiku Wordmark" width="600"/>
</div>

---

> [\!NOTE]
> **Status:** Version 1.0 - Active & Ready for the Distant Future

## Table of Contents
- [1. Vision & Purpose](#1-vision--purpose)
- [2. The Problem: An Identifier Built for a Bygone Era](#2-the-problem-an-identifier-built-for-a-bygone-era)
- [3. The Solution: KSI vs. ISBN](#3-the-solution-ksi-vs-isbn)
- [4. The KSI Registry](#4-the-ksi-registry)
- [5. Specification](#5-specification)
  - [What a KSI Identifies](#what-a-ksi-identifies)
  - [Format](#format)
  - [Component Breakdown](#component-breakdown)
  - [So, Will We Ever Run Out?](#so-will-we-ever-run-out)
- [6. Versioning the Standard](#6-versioning-the-standard)
- [7. Practical Use Cases & Implementation Notes](#7-practical-use-cases--implementation-notes)
- [8. Frequently Asked Questions (FAQ)](#8-frequently-asked-questions-faq)
- [9. Contributing](#9-contributing)

---

## 1. Vision & Purpose

The **Komiku Standard Identifier (KSI)** is a unified identification system designed by Komiku, born from the specific needs of modern digital creators. It's a declaration that a story born on the web deserves a web-native identity, free from the chaos of inconsistent file names (`final_draft_v3_revised_FINAL_v5_FINAL_FINAL_actually_final_this_time_USE_THIS_ONE_I_SWEAR_v7.docx`) and proprietary platform IDs.

Our vision is to build a universal, open registry for digital creative works. In a fragmented online world where content is king but often gets lost, the KSI acts as a stable anchor point. Its purpose is to ensure every webnovel and webtoon can be reliably tracked, cataloged, and referenced across different platforms, tools, and APIs, giving your work a permanent address on the internet.

---

## 2. The Problem: An Identifier Built for a Bygone Era

For decades, the world of publishing has had a powerful, time-tested system for identification: the ISBN. It revolutionized the physical supply chain for books. However, the very nature of webnovels and webtoons—serialized, constantly updated, living documents—is fundamentally at odds with this traditional model.

* **The "Static Edition" Mindset:** An ISBN identifies a specific, static *edition* of a book. If an author corrects a few typos and re-uploads their work, it's technically a new edition that would require a new ISBN—a situation that gives both authors and platform engineers a nervous twitch.

* **The "Product vs. Work" Distinction:** An ISBN identifies a commercial *product*. A webnovel is an evolving creative *work* long before it becomes a final product. It needs a stable identity from its inception, because "Untitled_Document_12" is not a great permanent identity.

* **The Platform Silo:** In the absence of a universal digital-first identifier, platforms were forced to invent their own. A single story is identified as `ID: 12345` on one platform and `ID: 67890` on another, forcing developers to write mountains of duct-tape code just to figure out they're the same story.

This fundamental gap—the lack of a free, instant, granular, and web-native identifier for evolving digital works—is the specific problem the KSI was created to solve.

---

## 3. The Solution: KSI vs. ISBN

The KSI is not intended to replace the ISBN, but to serve the specific needs of a medium the ISBN was never designed for.

* **Free & Instant vs. Cost & Bureaucracy:** ISBNs must be purchased from national agencies, often involving paperwork. **The KSI is completely free to register, instantly, at any time.** Your wallet can breathe a sigh of relief.

* **Dynamic & Granular vs. Static & Monolithic:** The KSI identifies a living *work*, allowing for continuous updates under a single, stable ID. The ISBN identifies a finished *edition*.

* **Web-Native vs. Print-Adapted:** The KSI is built for URLs, databases, and APIs. ISBNs were created for a physical supply chain and later adapted for a world they weren't born into.

A work can and should have both! A KSI for its life as a webnovel, and an ISBN if it's later compiled and sold as a traditional e-book.

---

## 4. The KSI Registry

To guarantee the uniqueness of every identifier, Komiku maintains a central **KSI Registry**.

* **How it Works:** The registry is our centralized database that serves as the single source of truth. When a KSI is generated via an official tool, a record is logged. This act of registration "mints" the KSI, turning it from a simple string into a globally recognized and verifiable identifier. It's like a digital birth certificate for your story.

* **Free and Unlimited:** Registration in the KSI Registry is and always will be **free for all creators**. There is no limit to how many projects you can register.

* **System Stability:** To ensure the system remains stable and fair for everyone, a fair-use rate limit is in place for generating new identifiers. This is mainly to prevent anyone from trying to generate all 14.7 million possible IDs in a single millisecond (we see you, chaos agents, and we've planned ahead).

---

## 5. Specification

### What a KSI Identifies

A single KSI is used to identify a **single creative work as a whole**.
* For webnovels, it identifies a `.wnb` book file.
* For webtoons, it identifies a `.wtb` series file.

The KSI does **not** identify individual chapters. That's a job for the manifest file.

### Format

`kmi:[format]-[timestamp]-[rand]`

### Component Breakdown
| Component   | Description                                                                                             | Example                   |
|-------------|---------------------------------------------------------------------------------------------------------|---------------------------|
| **`kmi`** | The static **namespace** for the Komiku Standard ecosystem.                                                 | `kmi`                     |
| **`[format]`**| A 2-letter code for the standard: `wn` (WebNovel) or `wt` (WebToon).                                      | `wn`                      |
| **`[timestamp]`** | A **64-bit Unix Timestamp in Milliseconds**. Makes the ID unique in time and sortable.                     | `1753515126000`           |
| **`[rand]`** | A **4-character** case-sensitive, random alphanumeric string for total uniqueness (and to appease the chaos gods of concurrency). | `gH4r` |

### So, Will We Ever Run Out?

No. And we mean that in the most astronomically literal sense.

The KSI system can generate over **14.7 million unique IDs every millisecond**. The 64-bit timestamp itself won't run out of numbers until the year **292,277,026,596**.

To put it another way: you, your children, your great-grandchildren, and their hyper-intelligent, dimension-hopping descendants can all create a new webnovel every second of every day, and you will not exhaust the supply of KSIs.

The format is permanent.

---

## 6. Versioning the Standard

A standard is a living document. To provide predictability for developers, the specification itself is versioned. The current version is stated at the top of this document.

Our versioning policy adheres to the principles of Semantic Versioning (`MAJOR.MINOR.PATCH`):
* **`MAJOR` version (e.g., v2.0):** Reserved for incompatible, breaking changes to the KSI string format. We expect to release `v2.0` around the same time humanity achieves faster-than-light travel, so you can probably build your tools against v1 with confidence.
* **`MINOR` version (e.g., v1.1):** For backward-compatible additions, like defining a new `[format]` code.
* **`PATCH` version (e.g., v1.0.1):** For minor clarifications and typo corrections in this document.

All changes will be documented in a `CHANGELOG.md` file.

---

## 7. Practical Use Cases & Implementation Notes

A KSI isn't just a string; it's a tool. Here’s how it's designed to be used by developers:

* **As a Canonical URL:** A KSI is the perfect slug for a URL, creating a permanent link to a work.
  `https://komiku.moe/works/kmi:wn-1753515126000-gH4r`
* **As a Database Key:** It's the ideal `PRIMARY KEY` for a `works` table. Give your database engineers a gift and use a clean, predictable, and sortable identifier. It should be stored as an indexed `VARCHAR` or `TEXT`.
* **In Metadata for Linking Works:** KSIs can create relationships between works. Finally, a way to officially link your prequel without just hoping people read the author's note.
  `<relatedWork type="sequel_to">kmi:wn-1753506025432-bN4z</relatedWork>`
* **In API Calls:** It provides an unambiguous way to request data for a specific work.
  `GET /api/v1/works/kmi:wn-1753515126000-gH4r`
  (A much prettier sight than `GET /works?id=8675309`, wouldn't you agree?)

---

## 8. Frequently Asked Questions (FAQ)

**Can I generate my own KSI offline?**
Technically, you could create a string that *looks* like a KSI. But for it to be an official, valid identifier, it must be logged in the central KSI Registry. It’s like printing your own money – it might look real, but you can’t spend it at the store.

**Why not just use UUIDs?**
UUIDs are fantastic for generating random, unique IDs. However, KSIs are better for this purpose because they are structured, sortable, and namespaced. In short, KSIs have a personality; UUIDs are just random numbers having an identity crisis.

**What happens if Komiku disappears?**
A fair and important question! The goal of an open standard is for it to outlive its creators. The specification is public and will be permissively licensed. In a hypothetical doomsday scenario, the open nature of the standard would allow the community to establish a new registry to continue its use.

---

## 9. Contributing

This is an open initiative, and we believe the best standards are built by a community. We welcome contributions and encourage discussions about the specification in the "Issues" tab of this repository.

If you want to help shape the future of digital storytelling, please feel free to open an issue or reach out to us directly at **oss@komiku.moe**.