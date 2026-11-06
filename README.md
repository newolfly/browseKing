<!-- markdownlint-disable commands-show-output first-line-h1 no-emphasis-as-heading no-inline-html -->

<div align="center">
  <a href="https://browseking.com?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=top-banner" align="center">
    <center align="center">
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="./assets/logo-white.svg" width="600">
        <source media="(prefers-color-scheme: light)" srcset="./assets/logo.svg" width="600">
        <img src="./assets/logo.svg" alt="BrowseKing logo" width="600">
      </picture>
    </center>
  </a>

  <h3>Deploy headless browsers in Docker. Run on our cloud or rule your own infrastructure.</h3>

  <p>
    <a href="https://browseking.com?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=try-on-cloud">
      <img src="https://img.shields.io/badge/🧪_Try_on_Cloud-4A90E2?style=for-the-badge" alt="Try on Cloud" />
    </a>
    &nbsp;&nbsp;
    <a href="#-get-started-in-seconds">
      <img src="https://img.shields.io/badge/📦_Run_Locally-34A853?style=for-the-badge" alt="Run Locally" />
    </a>
    &nbsp;&nbsp;
    <a href="https://docs.browseking.com/?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=dev-docs">
      <img src="https://img.shields.io/badge/📘_Dev_Docs-5C6AC4?style=for-the-badge" alt="Developer Docs" />
    </a>
  </p>

  <p>
    <a href="https://hub.docker.com/r/browseking/chrome">
      <img src="https://img.shields.io/docker/pulls/browseking/chrome?style=flat-square" alt="Docker pulls" />
    </a>
    <a href="https://github.com/browseking/browseking">
      <img src="https://img.shields.io/github/stars/browseking/browseking?style=flat-square" alt="GitHub stars" />
    </a>
    <a href="https://github.com/browseking/browseking/tags">
      <img src="https://img.shields.io/github/package-json/v/browseking/browseking?style=flat-square" alt="Version" />
    </a>
    <a href="https://status.browseking.com/">
      <img src="https://img.shields.io/badge/Status-Operational-success?style=flat-square" alt="Status" />
    </a>
  </p>
</div>

<br>

## 📋 Table of Contents

- [Get Started in Seconds](#-get-started-in-seconds)
- [Features](#-features)
- [Customisable Deployment Options](#-customisable-deployment-options)
- [Why BrowseKing?](#-why-browseking)
- [Licensing](#-licensing)

## 🚀 Get Started in Seconds!

Spin up a production-ready headless browser instance in three simple steps:

### Step 1: Run the Docker image

```bash
docker run -p 3000:3000 ghcr.io/browseking/chromium
```

### Step 2: Open the docs in your browser

Visit http://localhost:3000/docs

**✅ Success!** Your BrowseKing service is live at `ws://localhost:3000`

### Step 3: Connect your script with Puppeteer or Playwright

<details open>
<summary><b>📘 Puppeteer Example</b></summary>

```js
import puppeteer from 'puppeteer-core';

const browser = await puppeteer.connect({
  browserWSEndpoint: 'ws://localhost:3000',
});

const page = await browser.newPage();
await page.goto('[https://example.com](https://example.com)');
console.log(await page.title());
await browser.close();
```

</details>

<details>
<summary><b>🎭 Playwright Example</b></summary>

```js
import pw from 'playwright-core';

const browser = await pw.firefox.connect(
  'ws://localhost:3000/firefox/playwright',
);

const page = await browser.newPage();
await page.goto('[https://example.com](https://example.com)');
console.log(await page.title());
await browser.close();
```

**Note:** Use `ghcr.io/browseking/firefox` or `ghcr.io/browseking/multi` for Firefox and WebKit support.

</details>

</br>

### Output:

```
Example Domain
```

## ✨ Features

### General Features

- **Parallelism and queueing** — Handle concurrent sessions effortlessly with configurable queue limits
- **Live Debug Viewer** — Inspect and debug running browser sessions visually in real time
- **Unforked libraries** — Drop-in compatibility with standard Puppeteer and Playwright
- **Fonts & emoji** — Preloaded with full system font and emoji support out of the box
- **Configurable timeouts** — Automated session timers and health checks keep containers clean and responsive
- **Crash resilient** — Isolated browser processes ensure that if Chrome crashes, BrowseKing stays up
- **ARM64 architecture support** — Native support for ARM64 platforms including Apple Silicon (note: Edge and Chrome have upstream ARM64 limitations)

### Premium Features

Our [Self-Serve Cloud and Enterprise offerings](https://www.browseking.com/pricing/?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features) include all core features plus advanced capabilities:

- **[BrowseQL](https://www.browseking.com/feature/browseql?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for bypassing bot detectors and solving captchas automatically
- **[Hybrid Automations](https://docs.browseking.com/baas/interactive-browser-sessions/hybrid-automation?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for streaming interactive live browser sessions mid-script
- **[Persistent Sessions](https://docs.browseking.com/baas/session-management/persisting-state?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for retaining browser state (cookies, cache, localStorage) across runs with configurable retention up to 90 days
- **[Session Replay](https://docs.browseking.com/baas/interactive-browser-sessions/session-replay?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for recording and auditing sessions with full event capture and video playback
- **[Chrome Extensions Support](https://docs.browseking.com/baas/features/browser-extensions?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for loading custom extensions, ad blockers, and utility plugins
- **[Advanced Captcha & Stealth Routes](https://docs.browseking.com/browseql/bot-detection/overview?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for anti-detection via fingerprint randomization
