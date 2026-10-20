# Nexus Multi-Streamer

**by RMU Nexus**

Nexus Multi-Streamer lets you go live on Twitch, YouTube, Kick, TikTok and any other RTMP/SRT service at the same time — from a single OBS stream — with no re-encoding, no monthly fees, and no complicated setup. It can also save a full recording of every stream to your PC and show Twitch and YouTube chat in one place.

This guide covers buying, installing, and using the app.

---

## What you need

- **Windows 10 or 11 (64-bit)**
- **OBS Studio** (free — [obsproject.com](https://obsproject.com))
- An internet connection
- Accounts on the platforms you want to stream to
- About **350 MB** of free disk space for the app, plus room for recordings (roughly 1–2 GB per hour of stream, depending on your OBS settings)

> Streaming to several platforms at once uses upload bandwidth. As a rule of thumb, allow about **6 Mbps of upload per destination** on top of what your OBS bitrate already uses.

---

## 1. Purchase

Buy a license from the official store page:

**https://rmu.nexus/programs/multistreamer**

After checkout you'll receive a license key by email. Keys look like this:

```
NXMS-XXXX-XXXX-XXXX
```

Your key can be activated on **up to three computers**. Reinstalling on a PC you've already activated doesn't use an extra slot. Keep the email — you'll need the key the first time you open the app, and if you ever need to free up a slot, contact support.

---

## 2. Download and install

1. Download the installer — either from the store page or directly from the [Releases page](https://github.com/xbohiti/nexusMultiStreamer/releases/latest). The file is named **`NexusMulti-Streamer_Setup-<version>.exe`** (for example `NexusMulti-Streamer_Setup-1.3.10.exe`).
2. Double-click the installer.
3. Choose **Install for me only** (recommended) or install for all users, and pick a folder if you like. The default is fine.
4. Follow the prompts. Setup adds shortcuts to your **Desktop** and **Start menu**.

> **Downloading is free.** The app asks for your license key the first time you open it (section 3), so you can install now and enter the key whenever you're ready.

> **Windows may show "Windows protected your PC."** This appears because the installer isn't code-signed yet. Click **More info → Run anyway** to continue. The app is safe — you downloaded it from the official RMU Nexus site or repository.

---

## 3. First launch and activation

Open **Nexus Multi-Streamer** from your Desktop or Start menu.

1. The welcome screen asks for your license key.
2. Paste the key from your purchase email (it is not case-sensitive) and click **Activate**.
3. That's it — the app is activated on this PC.

The app checks your license online about once a day. If you're offline, it keeps working normally. You only need internet for activation and for automatic updates.

---

## 4. Connect your streaming accounts

On the main screen you'll see a card for each platform. Click **Connect** on the ones you want to use:

| Platform | What to do |
|---|---|
| **Twitch** | Click **Connect Twitch**, sign in in your browser, and approve access |
| **YouTube** | Click **Connect YouTube**, choose your Google account, and approve access |
| **Kick** | Click **Connect Kick**, sign in in your browser, and approve access |
| **TikTok** | No sign-in. Paste a **Server URL** and **Stream Key** generated with the [StreamLabs TikTok Stream Key Generator](https://github.com/Loukious/StreamLabsTikTokStreamKeyGenerator) before each stream (see below) |
| **Custom (Facebook, Rumble, etc.)** | Click **＋ Add RTMP / SRT stream**, then paste the server URL and stream key from that platform |

> **YouTube note:** Google's verification for the built-in YouTube connection is still pending, so YouTube may ask you to reconnect about once a week. This goes away once Google finishes reviewing the app. You'll never need a developer account or API keys.

### TikTok: applying for LIVE access and getting your stream key

TikTok doesn't hand out a permanent stream key through Nexus, so you'll need **LIVE access** on your account and a **fresh key for each stream**. Here's the full process:

1. **Apply for LIVE access.** Log in at [livecenter.tiktok.com/live_monitor](https://livecenter.tiktok.com/live_monitor) with your TikTok account, then click **View LIVE Access**. That takes you to the application page — fill it in and submit it.
   - Approval is not strictly tied to follower count: accounts with only a few followers are sometimes approved, so it's always worth applying.
2. **Wait for approval.** TikTok will notify you when your account has LIVE access.
3. **Generate your stream key and URL.** Use the free [StreamLabs TikTok Stream Key Generator](https://github.com/Loukious/StreamLabsTikTokStreamKeyGenerator) — follow the instructions on its page. It produces a **Server URL** and a **Stream Key** for your account.
4. **Connect it in Nexus.** Paste the generated Server URL and Stream Key into the TikTok card, then click **Go Live**.
5. **Repeat step 3 before every stream.** TikTok keys are single-session, so generate a new one each time you go live.

> The StreamLabs TikTok Stream Key Generator is a free, open-source tool made by a third party — it is not part of Nexus Multi-Streamer or RMU Nexus. Review its instructions before use.

Your logins are stored **encrypted on your own PC only**. Nothing is sent to RMU Nexus.

---

## 5. Set up OBS (one time)

In **OBS Studio**, open **Settings → Stream**:

- **Service:** `Custom…`
- **Server:** `rtmp://127.0.0.1:1935`
- **Stream Key:** `stream`

Leave those settings in place from now on. When you stream, OBS sends your video to Nexus Multi-Streamer, which forwards it to every platform you've enabled.

> You can change the stream key in the app's OBS Setup panel if you prefer something private — just update OBS to match. The server address stays the same.

---

## 6. Go live

1. Press **Start Streaming** in OBS. The header badge will change to **● OBS connected**.
2. In Nexus, click **Go Live** on a platform card — or **Go Live (All)** to start every enabled platform at once.
3. A card shows **LIVE** when that platform is receiving your stream.

To stop: click **Stop** on a card or **Stop All** in the header. Stop streaming in OBS as well when you're finished.

**Per-platform extras before you go live:**

- **Twitch & Kick:** pick a **Category** by searching — start typing and choose the real match from the list.
- **YouTube:** choose **Privacy** (Public, Unlisted, or Private) and optionally pick one of your **scheduled streams**.
- **All platforms:** set a **Title**, or leave it blank to keep the title from your account.
- The **Dest.** button arms a platform for **Go Live (All)** — it reads **Arm** when off and **Armed ✓** when on.

---

## 7. Record to your PC

Click **● Record** in the header at any time — it works whether or not platforms are live.

- The first time, choose a folder for your recordings (default is your Videos folder). Change it later in **Settings → Local recordings**.
- Files are saved as `Nexus Recording <date> <time>.flv` — a lossless copy of exactly what you sent to your platforms.
- Click **■ Stop Recording** to stop and save. Recording is independent of the platform streams, so you can start or stop either one without affecting the other.
- Because recording writes a copy directly to disk, it uses almost no extra CPU and the file stays playable even if the app or PC shuts down unexpectedly.

`.flv` files play in **VLC** and most media players. If your video editor won't open FLV, convert it to MP4 with any free converter — you can remux it without losing quality.

---

## 8. Unified chat

Click **Chat** in the header to see **Twitch and YouTube** chat together in one feed.

- **Pop out** opens a separate always-on-top chat window you can keep visible while playing.
- That window is designed to be draggable and can be made **click-through**, so it never gets in the way of your game.
- **Kick and TikTok chat isn't shown.** Neither platform gives desktop apps a way to read their chat live — Kick only sends chat to a web server, and TikTok has no chat API at all. Your streams to both still work normally.
- If you connected Twitch before this update, **click Connect on Twitch once more** to grant chat access (nothing else changes).

---

## 9. Stream Tools

Open a platform's card and expand **Stream Tools** at the bottom of it — everything that platform lets apps do for free, so you rarely need to open their websites mid-stream. Each card holds only its own platform's tools.

**Twitch**
- **Channel status** — live/offline, viewers, current title, category and tags.
- **Update title & tags** — edit your stream title, tags and language. (Category is set on the Twitch card.)
- **Content labels** — tick Twitch's official content labels (Mature, Gambling, etc.) so viewers see the right warnings.
- **Live actions** — add a stream marker, create a clip, toggle **Shield Mode**, check your ad schedule, snooze the next ad, and raid another channel.
- **Polls & predictions** — start a chat poll or a channel-points prediction.
- **Stream schedule** — add your next stream (or a weekly recurring one) to your Twitch channel page, and remove segments.

**YouTube**
- **Broadcast status** — live/offline, viewers, privacy, and stream health (with a plain-English note if something's wrong).
- **Category** — pick your YouTube category from the official list. You can set it **before** you go live (it's applied when the broadcast is created) or **while you're live** — changing it mid-stream updates the live broadcast immediately, no need to restart your stream.

**Kick**
- **Channel status** — live/offline, viewers, title, category and tags.
- **Update title & tags** — edit your Kick stream title and set up to 10 tags. (Category is set on the Kick card.)
- Kick has **no scheduling API**, so scheduling stays on Kick's website.

**TikTok**
- TikTok publishes **no public API** for stream metadata, categories or scheduling, so there are no live tools here. Instead, the TikTok card's **Stream Tools** section walks through the full process for getting a key — applying for LIVE access, then generating a fresh key each stream — with links to TikTok's LIVE Center and the free [StreamLabs TikTok Stream Key Generator](https://github.com/Loukious/StreamLabsTikTokStreamKeyGenerator). Your stream to TikTok still works normally.

> Tools only appear for platforms you've connected. A tool that needs a permission your account doesn't have (for example Twitch ads, which are for Affiliates/Partners) simply says so instead of failing silently.

---

## 10. Settings

Open **Settings** from the header:

- **Local recordings** — where recordings are saved, and a button to open that folder.
- **OAuth Apps** — normally you can ignore this. It's only for advanced users who want to connect through their own developer apps instead of the built-in connections.
- **Keyboard shortcuts** — also listed here in Settings:

  | Shortcut | Action |
  | --- | --- |
  | **Ctrl + Shift + G** | Go Live (All) |
  | **Ctrl + Shift + X** | Stop all streams |
  | **Ctrl + Shift + D** | Start / stop recording |
  | **Ctrl + Shift + C** | Show / hide chat |
  | **Ctrl + Shift + L** | Show / hide the log panel |

  Shortcuts are ignored while you're typing in a text field.

---

## 11. Updates

Nexus checks for new versions automatically (once per day while the app is open). When an update is ready, it downloads in the background and installs the next time you close the app. No action needed.

---

## Troubleshooting

**The badge says "Ingest: waiting for OBS".**
OBS isn't sending to the app. In OBS, check **Settings → Stream** uses server `rtmp://127.0.0.1:1935` and the key shown in the app, then press **Start Streaming**.

**"OBS never connected" when clicking Go Live.**
Same cause — start streaming in OBS first, then click **Go Live** again.

**A platform says "Not connected".**
Click **Connect** on its card and finish the sign-in in your browser. If it still fails, disconnect and connect again.

**YouTube asks you to reconnect often.**
Expected for now (about once a week) until Google finishes verifying the app — see the YouTube note above.

**TikTok won't go live.**
You need LIVE access on your TikTok account. Apply at [livecenter.tiktok.com/live_monitor](https://livecenter.tiktok.com/live_monitor) — click **View LIVE Access** (see section 4; approval is sometimes granted even to accounts with few followers). Once approved, generate a fresh Server URL and Stream Key with the [StreamLabs TikTok Stream Key Generator](https://github.com/Loukious/StreamLabsTikTokStreamKeyGenerator) and paste both into the TikTok card. Keys are single-session, so generate a new one before each stream.

**A platform shows "OFFLINE — retrying".**
The app retries automatically. If it keeps failing, stop that destination, check the account is still connected, and start it again.

**The app won't install, or Windows blocks it.**
See the SmartScreen note in section 2. If antivirus blocks it, allow the app and try again.

**The Logs panel shows `Negative cts`, `Invalid timestamps`, or `Invalid DTS … replacing by guess`.**
These are harmless and need no action. They appear when OBS uses **B-frames**, which reorder video timestamps; when the app attaches to your stream, the first frame or two can be off by about a millisecond, so ffmpeg notes it and then corrects it automatically before sending to TikTok, Twitch, YouTube, Kick and any other destination. Your live stream and your recording are unaffected — you can ignore these lines, and they are not specific to TikTok.

If you'd like them to stop appearing entirely, set the x264 encoder's **B-Frames** to **0** in OBS (slightly lower compression efficiency at the same quality). If these lines keep repeating throughout the stream instead of only at the start, please contact support.

**Something else is wrong.**
Open the **Logs** panel at the bottom of the app, copy the last few lines, and email them to support — they never contain your stream keys.

---

## Uninstalling

Windows **Settings → Apps → Installed apps → Nexus Multi-Streamer → Uninstall**.

Your recordings are **not** deleted — they stay in the folder you chose. If you plan to reinstall later, your key will reactivate on the same PC without using another slot.

---

## Support

- **Email:** contact@rmunexus.xyz
- **Store page:** https://rmu.nexus/programs/multistreamer
- **Lost your license key?** Email support from the address you purchased with.

Please include your app version (shown in Windows **Settings → Apps → Installed apps**) and any relevant log lines when contacting support.
