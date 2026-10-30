# Questify architecture and stack

The Questify source repository is private. This file is the public record of what the app is built with. The tables are generated from the `package.json` files and `pnpm-lock.yaml` of the private repository (branch `main`, 21 Oct 2026, app version 1.1.1). Between the published APK 1.1.0 and that state only the app version number changed; the dependencies are the same.

"Declared" is the range in `package.json`. "Resolved" is the exact version in `pnpm-lock.yaml`.

## How the pieces fit

- One Expo app (`apps/mobile`) builds both targets: the Android APK and the web app. The web build uses React Native Web.
- Screens use Expo Router for navigation and TanStack Query for data from the server.
- The backend is Supabase: Postgres for data, Supabase Auth for email and password sign-in. The database schema and the game rules (XP, rewards, anti-cheat) live in a separate private repository.
- For tests and previews the app has a fixture backend: an in-memory copy of the backend contract with seed data (the demo account "Mira" in the screenshots). Production builds refuse it.
- Two local Expo modules are written in Kotlin: `questify-app-icon` switches the Android launcher icon per look, `questify-haptics` defines named vibration patterns.
- Hosting: the web build runs on EAS Hosting at [mastertasker.expo.app](https://mastertasker.expo.app/). Android APKs are published in this repository's [Releases](https://github.com/vassiljevnikita-sudo/questify-releases/releases).

## Toolchain

| Item | Version |
| --- | --- |
| Language | TypeScript 6.0.3 (with a local patch), type check with `tsc-rs` 0.2.0 |
| Package manager | pnpm 10.17.1 (`packageManager` field) |
| Node | `>=26.7.0` (`engines` field) |
| Source files on `main` | 372 `.ts`, 131 `.tsx`, 2 Kotlin modules |

## App dependencies (`apps/mobile/package.json`, `dependencies`)

| Package | Declared | Resolved |
| --- | --- | --- |
| `@expo-google-fonts/anton` | `^0.4.2` | 0.4.2 |
| `@expo-google-fonts/barlow` | `^0.4.1` | 0.4.1 |
| `@expo-google-fonts/fredoka` | `^0.4.1` | 0.4.1 |
| `@expo-google-fonts/marcellus` | `^0.4.1` | 0.4.1 |
| `@expo-google-fonts/nunito` | `^0.4.2` | 0.4.2 |
| `@expo-google-fonts/outfit` | `^0.4.3` | 0.4.3 |
| `@expo/metro-runtime` | `~57.0.17` | 57.0.17 |
| `@expo/vector-icons` | `^15.0.2` | 15.1.1 |
| `@react-native-async-storage/async-storage` | `2.2.0` | 2.2.0 |
| `@react-native-community/netinfo` | `12.0.1` | 12.0.1 |
| `@supabase/supabase-js` | `~2.118.0` | 2.118.0 |
| `@tanstack/react-query` | `5.104.4` | 5.104.4 |
| `expo` | `~57.0.30` | 57.0.30 |
| `expo-build-properties` | `~57.0.22` | 57.0.22 |
| `expo-clipboard` | `~57.0.2` | 57.0.2 |
| `expo-constants` | `~57.0.22` | 57.0.22 |
| `expo-font` | `~57.0.4` | 57.0.4 |
| `expo-haptics` | `~57.0.3` | 57.0.3 |
| `expo-linear-gradient` | `~57.0.2` | 57.0.2 |
| `expo-linking` | `~57.0.13` | 57.0.13 |
| `expo-router` | `~57.0.28` | 57.0.28 |
| `expo-splash-screen` | `~57.0.10` | 57.0.10 |
| `expo-status-bar` | `~57.0.1` | 57.0.1 |
| `expo-system-ui` | `~57.0.4` | 57.0.4 |
| `expo-updates` | `~57.0.26` | 57.0.26 |
| `react` | `19.2.3` | 19.2.3 |
| `react-dom` | `19.2.3` | 19.2.3 |
| `react-native` | `0.86.3` | 0.86.3 |
| `react-native-gesture-handler` | `~2.32.0` | 2.32.0 |
| `react-native-pager-view` | `8.0.2` | 8.0.2 |
| `react-native-reanimated` | `4.5.1` | 4.5.1 |
| `react-native-safe-area-context` | `~5.7.0` | 5.7.0 |
| `react-native-screens` | `~4.26.0` | 4.26.2 |
| `react-native-svg` | `15.15.4` | 15.15.4 |
| `react-native-web` | `~0.21.0` | 0.21.4 |
| `react-native-worklets` | `0.10.1` | 0.10.1 |

## App dev dependencies (`apps/mobile/package.json`, `devDependencies`)

| Package | Declared | Resolved |
| --- | --- | --- |
| `@expo/env` | `~2.4.3` | 2.4.3 |
| `@resvg/resvg-js` | `2.6.2` | 2.6.2 |
| `@types/react` | `~19.2.4` | 19.2.18 |
| `expo-doctor` | `1.21.5` | 1.21.5 |
| `tsc-rs` | `0.2.0` | 0.2.0 |
| `typescript` | `6.0.3` | 6.0.3 |

## Workspace dev dependencies (root `package.json`, `devDependencies`)

| Package | Declared | Resolved |
| --- | --- | --- |
| `@playwright/test` | `1.62.1` | 1.62.1 |
| `@types/node` | `^24.10.0` | 24.19.2 |
| `esbuild` | `0.28.2` | 0.28.2 |
| `tsc-rs` | `0.2.0` | 0.2.0 |
| `typescript` | `6.0.3` | 6.0.3 |
| `vitest` | `3.2.7` | 3.2.7 |

## What is not published

No source code, no database schema, no environment files and no keys. The web app's Supabase URL and anon key are part of every client build by design; access is controlled by row-level security and server-side rules in the private backend.
