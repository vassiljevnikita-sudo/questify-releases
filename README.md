# Questify

A plain to-do list gives you no reason to open it again tomorrow. Questify turns tasks into quests that earn XP, levels and a place in weekly and monthly leagues against your friends.

<p>
  <img src="docs/screenshots/01-start.png" alt="Start screen with level, season progress and the next quests" width="200">
  <img src="docs/screenshots/02-new-quest.png" alt="Editor for a new quest: type, schedule, project" width="200">
  <img src="docs/screenshots/03-season-pass.png" alt="Season pass with reward tiers" width="200">
  <img src="docs/screenshots/04-leaderboard.png" alt="Monthly leaderboard among friends" width="200">
</p>

Screenshots: the public landing page, mobile viewport, taken with Playwright on 30 Oct 2026. The phone screens show the app's built-in demo account (Mira and her friends are seed data, not real users).

## Try it

- Web: https://mastertasker.expo.app/ (sign up with email and password)
- Android: [questify.apk, latest release](https://github.com/vassiljevnikita-sudo/questify-releases/releases/latest/download/questify.apk) (version 1.1.0, about 102 MB)
- Landing page: https://mastertasker.expo.app/willkommen/

## My role

Nikita Vassiljev ([GitHub](https://github.com/vassiljevnikita-sudo)), solo developer: concept, app code, design and releases. I built it with AI coding agents (Claude and OpenAI Codex). In the private source repository, 362 of the 383 commits on `main` come from my account and 21 from Codex agent accounts; 354 commits name an AI agent as co-author.

## Tech stack

- TypeScript 6.0.3 (type-checked with tsc-rs 0.2.0); two small native Android modules in Kotlin (launcher icon per look, haptic patterns)
- React Native 0.86.3 with React 19.2.3, Expo SDK 57 (`expo` 57.0.30), Expo Router 57.0.28, React Native Web 0.21.4 for the web build
- TanStack Query 5.104.4 for server state, Reanimated 4.5.1 for animation
- Supabase (Postgres, Auth) through `@supabase/supabase-js` 2.118.0
- Tests and tooling: Vitest 3.2.7, Playwright 1.62.1, pnpm 10.17.1, Node 26.7 or newer
- Hosting: web on EAS Hosting (`*.expo.app`), Android APK on GitHub Releases

The full dependency list with versions is in [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Limitations

- The source code is private. This repository holds the Android builds, the screenshots and the stack list.
- Android only as an APK outside Google Play, so Android asks you to allow the install. There is no iOS app.
- The interface is German only.
- You need an account. The web app has no guest or demo mode; the demo data above exists only in the screenshots.
- Solo project: no external security audit, no uptime guarantee.

## Install on Android

1. Open the [APK link](https://github.com/vassiljevnikita-sudo/questify-releases/releases/latest/download/questify.apk) on your Android phone.
2. Open the downloaded `questify.apk`. Android asks whether the browser (or file manager) may install apps. Allow it for this install.
3. Tap Install, open Questify and sign in or create an account.

To update, install the newer APK over the old one. Your quests and progress are stored on the server, so nothing is lost.

Each release also has a `SHA256SUMS` file. To check a download on a computer:

```bash
sha256sum questify.apk   # compare with the line in SHA256SUMS on the release page
```

## Releases

| Version | Date | Notes |
| --- | --- | --- |
| [1.1.0](https://github.com/vassiljevnikita-sudo/questify-releases/releases/tag/v1.1.0) | 19 Oct 2026 | Expo SDK 57, four looks, collection and cosmetics, reusable friend invites |
| [1.0.0](https://github.com/vassiljevnikita-sudo/questify-releases/releases/tag/v1.0.0) | 19 Oct 2026 | First public Android build |

## More screens

<p>
  <img src="docs/screenshots/05-looks.png" alt="The four looks: Arena, Bonbon, Sternenstaub, Classic" width="300">
  <img src="docs/screenshots/06-web-sign-in.png" alt="Sign-in page of the web app" width="200">
</p>

Left: the same start screen in the four looks (Arena, Bonbon, Sternenstaub, Classic). Right: the web app's sign-in page.

## Contact

vassiljev.nikita@gmail.com · [Impressum](https://mastertasker.expo.app/website/5/impressum.html) · [Datenschutz](https://mastertasker.expo.app/website/5/datenschutz.html)
