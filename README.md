![Whispr Journal — A quiet place for your thoughts.](assets/hero.svg)

<p align="center">
  <a href="https://apps.apple.com/us/app/whispr-journal-voice-diary/id6806876874"><strong>View on the App Store ↗</strong></a> &nbsp; · &nbsp;
  <a href="docs/ENGINEERING.md">Engineering notes</a> &nbsp; · &nbsp;
  <a href="https://github.com/Zodomik">More by Oğuz Tonyalı</a>
</p>

## Whispr Journal

A personal journal that lets you write or dictate, then revisit your entries in a book-style reader. Dawn and night themes give everyday reflection a calm visual setting.

Built and published by **[Oğuz Tonyalı](https://github.com/Zodomik)**. This repository is a public product and engineering showcase; the application source is maintained privately.

## A look inside

<p align="center">
  <img src="assets/screen-01.jpg" width="30%" alt="Whispr Journal official App Store preview 1" />
  <img src="assets/screen-02.jpg" width="30%" alt="Whispr Journal official App Store preview 2" />
  <img src="assets/screen-03.jpg" width="30%" alt="Whispr Journal official App Store preview 3" />
</p>

*Official product previews from the [App Store listing](https://apps.apple.com/us/app/whispr-journal-voice-diary/id6806876874).*

## What you can do

- Text entries and editable voice dictation in six languages.
- Scrollable and paged book-style reading.
- Search, calendar browsing, moods, tags and favorites.
- Premium text export and Journal Lock with device authentication.

## Technology

| Area | Technologies | Role in the product |
| --- | --- | --- |
| Interface | Swift, SwiftUI | Composition, journal browsing, themes and book-style reading. |
| Persistence | SwiftData | Structured journal entries and local data storage. |
| Dictation | Speech, AVFoundation | Speech recognition, microphone capture and recording-session lifecycle. |
| Journal Lock | LocalAuthentication | Device authentication before opening protected journal content. |
| Purchases | RevenueCat, StoreKit | Subscription/lifetime access and purchase restoration. |

## Implementation notes

SwiftUI app; local SwiftData journal; Apple Speech Recognition; device-owner authentication; no custom journal backend.

- Session UUIDs reject stale speech callbacks after stop/restart.
- Partial transcription is joined to a stable editable draft prefix.
- Local entry filtering and lightweight word-preserving book pages.

| Read more | What is covered |
| --- | --- |
| [Architecture and frameworks](docs/ENGINEERING.md) | Runtime components, backend structure and framework responsibilities |
| [Database and local data](docs/DATA_MODEL.md) | Entities, relationships, constraints and persistence choices |
| [Algorithms and implementation choices](docs/ALGORITHMS.md) | Calculations, example flows and the limits of each approach |

## Try the product

**[Open Whispr Journal on the App Store](https://apps.apple.com/us/app/whispr-journal-voice-diary/id6806876874)** · Requires iOS 17.0 or later.

Availability and purchase options are shown in the store. For product support, use the developer links on the App Store listing.

---

[All published apps](https://apps.apple.com/us/developer/oguz-tonyali/id1880078720) · [Developer profile](https://github.com/Zodomik) · [Media credits](assets/SOURCES.md)
