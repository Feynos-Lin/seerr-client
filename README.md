# Feynos Seerr

An Android client for [Seerr](https://github.com/seerr-team/seerr) (also works with Overseerr and Jellyseerr). Dark theme with an indigo/purple accent, built with Kotlin and Jetpack Compose.

## Features

- **Sign in** with a Seerr local account, Jellyfin, Plex (plex.tv device approval) or an API key
- **Discover**: auto-rotating trending hero, plus Popular and Upcoming rows for movies and series, each with a "See all" infinite grid
- **Search** with debounced, infinite-scrolling results
- **Details**: backdrop, rating, runtime, genres, cast, per-season availability, trailer, "More like this", and a **Play** button when the title is in your library
- **Request** movies, or pick specific seasons of a series. Admins and managers (or users with the Advanced Requests permission) can also pick the Radarr/Sonarr server, quality profile, root folder, language profile and tags. These start on Seerr's defaults, and series tagged as anime start on the anime defaults
- **Requests** list with status filters, pull to refresh, and approve / decline / delete if you're an admin or manager
- **Profile**: your request stats, server version, and sign out

## Install

Grab the latest `FeynosSeerr-*.apk` from [Releases](../../releases).

## How it's built

The whole project lives in a single file, `.github/workflows/build.yml`. Every push to `main` writes out the source, builds a signed release APK and publishes it as a GitHub release.

### Signing

With no secrets set, the workflow signs with a key kept in the Actions cache. GitHub drops caches that go unused for 7 days. If that happens, the next build gets a new key and you'll have to uninstall before updating. To make updates permanent, add these repository secrets:

| Secret | Value |
|---|---|
| `KEYSTORE_BASE64` | `base64 -w0 release.jks` |
| `KEYSTORE_PASSWORD` | keystore password |
| `KEY_ALIAS` | key alias |
| `KEY_PASSWORD` | key password (optional, defaults to the keystore password) |
