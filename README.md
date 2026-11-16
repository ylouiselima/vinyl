# Vinyl

A Spotify player that looks like a record spinning on your screen. It's made for an iPad on a stand, and it also works mirrored on a TV.

The whole app is one file, `index.html`. There is nothing to build or install, and no server.

## What it does

- Plays Spotify music on the page. The page shows up in Spotify as a speaker called **Vinyl Player**.
- Shows the album cover as the record's label. The record spins while music plays and slows to a stop when you pause.
- Tints a slowly moving background with colors from the album cover.
- Has play/pause, previous, next, and a seekable progress bar. Tapping the record also plays or pauses.
- Works in landscape (record on the right, player card bottom-left) and portrait (record on top, player card across the bottom).
- Keeps the screen awake while music plays.

You pick the music in the normal Spotify app on your phone or computer. This page is where it plays and where you watch it.

## What you need

- A **Spotify Premium** account. Premium plans that are mobile-only don't work for playing in a browser.
- A free **Spotify developer app** (steps below). Its owner needs Premium, and Spotify's development mode allows up to 5 users per app.
- A browser that supports the Spotify Web Playback SDK. Safari on iPad works, with some limits on iOS (see Notes).

## Setup

**1. Host the page.** The page has to run from a web address, not from a file on your device. On GitHub:

1. Put `index.html` in a repository.
2. Go to **Settings, then Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick your branch and the `/ (root)` folder, and save.
4. After a minute, your address appears, like `https://your-username.github.io/vinyl/`. Leave the Custom domain field empty.

**2. Create the Spotify app.**

1. Open the [Spotify developer dashboard](https://developer.spotify.com/dashboard) and create an app.
2. Open your page address in a browser. The setup screen shows a **Redirect URI**. Copy it with the Copy button.
3. In the app's settings, paste that address as the Redirect URI. It has to match exactly, including `https://` and the `/` at the end.
4. Tick **Web API** and **Web Playback SDK**, then save.
5. If login is refused, add your Spotify email under **User Management** in the same app.

**3. Connect.** Paste the app's **Client ID** into the setup screen and log in with Spotify. Never paste the Client Secret anywhere. This app doesn't use it.

**4. Install on the iPad (optional).** In Safari, tap Share, then **Add to Home Screen**. It opens fullscreen like an app.

## Using it

1. Open the page. Tap anywhere once to turn the sound on. iOS requires this before a page can play audio.
2. In the Spotify app on your phone, start a song and open the device list. Choose **Vinyl Player**.
3. The sound comes from the iPad and the record starts spinning.

Two shortcuts:

- If music is playing on another device, tap **Play here** on the player card to move it to the page.
- If nothing is playing, the big play button starts playback on the page.

To TV: mirror the iPad to an Apple TV with AirPlay screen mirroring.

## Notes and limits

- **No secrets in the code.** Login uses Spotify's PKCE flow, so only the Client ID is needed. Your login is stored in your browser and never leaves your device.
- **Log in again twice a year.** Spotify's refresh tokens expire six months after you first log in.
- **Volume on iOS.** A web page can't set volume on iOS. Use the iPad's volume buttons.
- **Playback is state-driven.** Spotify doesn't let pages read the raw audio, so the visuals follow play, pause, and track changes, not the beat.
- **The page must stay open.** "Vinyl Player" only appears in Spotify's device list while the page is open and connected. Locking the screen may stop playback on iOS.
- **Development mode.** Spotify limits new apps to 5 users and a reduced set of Web API features.

## Troubleshooting

| What you see | What to do |
| --- | --- |
| "This content is blocked" | The page is open inside a preview that blocks Spotify login. Open it from your own address. |
| Spotify says the redirect URI is invalid | Copy it again from the setup screen and paste it into the dashboard exactly as shown, then save. |
| "Spotify did not allow playback" | In the app's settings on the dashboard, tick Web Playback SDK, save, then log in again. |
| "Vinyl Player" isn't in the device list | Keep the page open, tap it once, and reopen the device list in Spotify. |
| No sound | Tap the page once. If it still fails, check that the iPad isn't muted. |
| "Nothing is playing yet" | Start a song in Spotify and choose Vinyl Player, or tap Play here. |
| Playing needs Premium | The account must have a Premium plan that includes more than mobile. |

## Versions

- **Version 1** only showed and controlled music playing on other Spotify devices.
- **Version 2** plays the audio on the page itself.

## Credits

Fonts: Bodoni Moda, Familjen Grotesk and Inter, loaded from Google Fonts.

This is an independent project. It isn't made by or affiliated with Spotify. Spotify is a trademark of Spotify AB.

## License

MIT. See [LICENSE](LICENSE).
