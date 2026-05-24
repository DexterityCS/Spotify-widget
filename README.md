# 🎵 Spotify Widget

A clean, customizable "Now Playing" overlay for Twitch streams. Displays the current Spotify track with album art, song title, artist, and an animated progress bar — all in a browser source you drop straight into OBS or Streamlabs.

**Live:** [`dexteritycs.github.io/Spotify-widget/`](https://dexteritycs.github.io/Spotify-widget/)

---

## Features

- Real-time Spotify track display via OAuth (no server required)
- Album art, song title, artist name, and animated progress bar
- Multiple color presets: Light, Dark, Midnight — plus full custom color picker
- SLOBS-compatible backtick (`` ` ``) interact menu for on-the-fly color changes and logout
- Credentials persist in URL hash — no re-login between OBS sessions
- Session expiry banner with one-click reconnect

---

## Setup

### 1. Create a Spotify App

1. Go to [developer.spotify.com/dashboard](https://developer.spotify.com/dashboard)
2. Click **Create App**
3. Set the Redirect URI to: `https://dexteritycs.github.io/Spotify-widget/`
4. Copy your **Client ID**

### 2. Add to OBS / Streamlabs

1. Add a **Browser Source** to your scene
2. URL: `https://dexteritycs.github.io/Spotify-widget/`
3. Width: `400` | Height: `120` (adjust to taste)
4. Check **Refresh browser when scene becomes active**

### 3. Authenticate

1. Open the URL in a regular browser tab
2. Paste your **Client ID** when prompted
3. Click **Connect with Spotify** and authorize
4. Close the tab — OBS will pick up the token automatically

---

## Color Customization

Press the backtick key (`` ` ``) while the browser source is focused to open the interact menu. Choose from presets or set custom hex colors for background, text, and the progress bar accent. Changes persist across reloads.

---

## Tech

- Vanilla HTML/CSS/JS — zero dependencies, zero server
- Spotify Web API — `user-read-currently-playing`, `user-read-playback-state` scopes
- PKCE OAuth flow (token stored in URL hash for SLOBS compatibility)
- Polls every 5 seconds for track updates
