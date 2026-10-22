# Bujua

<p align="center">
  <a href="https://bujua.com">
    <img src="https://raw.githubusercontent.com/narnonymous/bujua/main/brand-kit/banners/banner-github-repo-1280x640.png" alt="Bujua Banner" width="100%" />
  </a>
</p>

<p align="center">
  <strong>Async video messages for teams. Pay for the people who record. Everyone who watches is free.</strong>
</p>

<p align="center">
  <a href="https://bujua.com">Website</a> &bull;
  <a href="https://bujua.com/guides">Guides</a> &bull;
  <a href="https://bujua.com/pricing">Pricing</a> &bull;
  <a href="https://bujua.com/screen-recorder">Free Screen Recorder</a> &bull;
  <a href="https://bujua.com/changelog">Changelog</a>
</p>

---

## What is Bujua?

Bujua replaces status meetings and repetitive explanations with short, asynchronous video messages. 

Most video messaging platforms charge per member regardless of whether they record or only watch. Bujua changes that model: **recording seats are paid, viewers are always free**.

### Key Capabilities

- **Browser recorder with zero install:** Record screen, camera, or both directly inside Chrome, Edge, Firefox, or Safari.
- **Instant share links:** Videos stream via Cloudflare R2 directly as they record, so links are ready the moment you stop.
- **Time-stamped comments:** Viewers leave feedback tied to the exact second, avoiding back-and-forth confusion.
- **Viewer analytics:** See who watched your video, completion rates, and second-by-second retention drop-off.
- **Transcripts and summaries:** Automatic speech-to-text transcription and summaries powered by Cloudflare Workers AI (Whisper).

---

## Product Ecosystem

| Repository / App | Description | Stack |
| :--- | :--- | :--- |
| [**bujua/bujua**](https://github.com/narnonymous/bujua) | Core web application, edge APIs, video processing, and marketing engine | Cloudflare Workers, R2, D1, Preact |
| [**bujua/desktop**](https://github.com/narnonymous/bujua/tree/main/desktop) | Native desktop recorder for Windows and macOS with hardware encoding | Tauri / Electron, Rust, TypeScript |
| [**bujua/extension**](https://github.com/narnonymous/bujua/tree/main/extension) | Chrome extension for one-click tab and screen recording | Manifest V3, WebRTC |

---

## Architecture at the Edge

Bujua is built entirely on Cloudflare's serverless edge infrastructure:

- **Compute:** Cloudflare Workers running close to users with minimal cold start latency.
- **Storage:** Cloudflare R2 object storage with zero egress fees for video chunk uploads and HLS streaming.
- **Database:** Cloudflare D1 serverless SQLite database for workspaces, videos, comments, and analytics.
- **AI:** Cloudflare Workers AI running Whisper models on edge GPUs for transcription.

```
[ Browser / Desktop Recorder ]
               |
               v (Direct multi-part upload)
      [ Cloudflare R2 ] <--------> [ Cloudflare Workers API ]
               |                                  |
               v                                  v
      [ HLS Video Stream ]                 [ Cloudflare D1 ]
               |                                  |
               v                                  v
     [ Free Video Viewers ]            [ Workers AI Whisper ]
```

---

## Free Zero-Install Tools

You can use Bujua's utilities directly in your browser without creating an account:

- [**Free Screen Recorder**](https://bujua.com/screen-recorder): Record your full desktop, application window, or browser tab.
- [**Free Webcam Recorder**](https://bujua.com/webcam-recorder): Record camera messages directly with microphone controls.
- [**Free Voice Recorder**](https://bujua.com/voice-recorder): Record audio memos with browser playback and transcriptions.
- [**Video Messaging Cost Calculator**](https://bujua.com/video-messaging-cost-calculator): Calculate seat tax savings compared to Loom, Vidyard, and Zight.

---

## Community and Contact

- **Website:** [bujua.com](https://bujua.com)
- **X (Twitter):** [@bujuahq](https://x.com/bujuahq)
- **LinkedIn:** [linkedin.com/company/bujua](https://www.linkedin.com/company/bujua)
- **YouTube:** [@bujua](https://www.youtube.com/@bujua)
- **Product Hunt:** [bujua on Product Hunt](https://www.producthunt.com/products/bujua)
- **Email:** [support@bujua.com](mailto:support@bujua.com)
- **Security:** [security@bujua.com](mailto:security@bujua.com)
