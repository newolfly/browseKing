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
    <a href="https://hub.docker.com">
      <img src="https://img.shields.io/badge/docker_pulls-100M+-blue?style=flat-square" alt="Docker pulls" />
    </a>
    <a href="https://github.com/newolfly">
      <img src="https://img.shields.io/badge/edition-Enterprise_%26_OSS-informational?style=flat-square" alt="Edition" />
    </a>
    <a href="https://github.com/newolfly">
      <img src="https://img.shields.io/badge/version-v2.24.0-blue?style=flat-square" alt="Version" />
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
- **[Advanced Captcha & Stealth Routes](https://docs.browseking.com/browseql/bot-detection/overview?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for anti-detection via fingerprint randomization, automated captcha solving, and residential proxy rotation
- **[REST APIs](https://www.browseking.com/feature/rest-apis?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for instant HTML extraction, PDF generation, and screenshots without managing WebSockets
- **[Built-in Residential Proxies](https://www.browseking.com/blog/residential-proxying/?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for automatic IP rotation and precise geo-targeting
- **[/smart-scrape API](https://docs.browseking.com/rest-apis/smart-scrape?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for intelligent URL scraping using cascading strategies (HTTP fetch, proxy, headless browser, captcha bypass)
- **[/crawl API](https://docs.browseking.com/rest-apis/crawl?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for asynchronously crawling entire domains and converting pages into structured, LLM-ready data
- **[/map API](https://docs.browseking.com/rest-apis/map?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for rapid URL discovery via sitemaps and link extraction with relevance ranking
- **[/search API](https://docs.browseking.com/rest-apis/search?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for querying the web and scraping results directly into Markdown, HTML, links, or screenshots
- **[MCP Server](https://docs.browseking.com/mcp/browseking-mcp-server?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for connecting AI agents (Claude Desktop, Cursor, VS Code, Windsurf) directly to BrowseKing automation
- **[Webhook Integrations](https://docs.browseking.com/enterprise/docker/webhooks?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=features)** for real-time alerts on queues, rejections, timeouts, errors, and health checks

## 🚢 Customisable Deployment Options

Select the deployment model that best fits your stack:

<table>
<tr>
<td width="50%" valign="top">

### 🔓 Open Source (Self-Hosted)

Free, self-hosted container with core browser automation capabilities.

**Best for:** Local testing, development, and hobby projects

[↓ Quickstart above](#-get-started-in-seconds)

</td>
<td width="50%" valign="top">

### 🏢 Enterprise Docker (Self-Hosted)

Full Enterprise feature set inside a self-hosted container.

**Best for:** Production workloads requiring strict data sovereignty

[→ Learn More](https://www.browseking.com/pricing?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=enterprise-docker)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ☁️ Cloud (Self-Serve)

Fully managed, pay-as-you-go platform with instant autoscaling.

**Best for:** Fast launches, scraping pipelines, and rapid prototyping

[→ Start Free](https://browseking.com/?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=cloud-self-serve)

</td>
<td width="50%" valign="top">

### 🔒 Private Deployment

Dedicated Enterprise clusters deployed across major cloud providers.

**Best for:** High-volume, mission-critical enterprise workloads

[→ Contact Sales](https://www.browseking.com/contact?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=private-deployment)

</td>
</tr>
</table>

> **Want to dive deeper?** Check out our [detailed guide](./LEARN_MORE.md) for advanced Docker configuration, cloud hosting providers, SDK extensions, and performance tuning.

## 💡 Why BrowseKing?

**Running headless Chrome in the cloud or CI is a headache.**

Missing fonts. Zombie processes. Dependency hell. Serverless size limits. You know the drill.

**BrowseKing solves this** by treating headless browsers as a battle-tested, managed service — whether running locally in Docker or scaled on our cloud — so you can focus on writing scripts, not babysitting infrastructure. We handle the OS packages, font libraries, security patches, scaling logic, and CVEs out of the box.

You own your scripts. You control your code. BrowseKing makes sure the browser runs like royalty, every single time.

## 📜 Licensing

SPDX-License-Identifier: SSPL-1.0 OR BrowseKing Commercial License.

To use BrowseKing in commercial applications, proprietary SaaS products, or closed-source CI/CD pipelines, you will need a commercial license. This lets you keep your codebase proprietary while leveraging BrowseKing in production. [Purchase a commercial license here](https://www.browseking.com/contact?utm_source=github&utm_medium=referral&utm_campaign=oss-readme&utm_content=licensing). A commercial license includes:

- Priority engineering support for issues and feature requests.
- Rights to deploy on-premise or across public cloud providers for proprietary commercial and CI workloads.
- Permission to fork and modify the source code for internal use.
- Access to the dedicated BrowseKing Admin UI.

Your commercial license directly funds ongoing maintenance, security updates, and new open-source capabilities.

If you are building an open-source application under a license compatible with the Server Side Public License 1.0 (SSPL-1.0), you may use BrowseKing free of charge under those terms.

<div align="center">

**Happy hacking!**

Need help? Reach out to us at **support@browseking.com**

</div>
