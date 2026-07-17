# Midnight Signal GitHub Profile Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the current template-heavy GitHub profile with a distinctive Midnight Signal identity and publish it directly to `Marshall3572/Marshall3572` on `main`.

**Architecture:** The profile remains a single GitHub-rendered `README.md` backed by one repository-owned banner image. Native Markdown and GitHub-safe HTML carry all important content; third-party statistics are optional and collapsed below the primary story.

**Tech Stack:** GitHub Flavored Markdown, GitHub-safe HTML, PNG, Shields.io, Skill Icons, GitHub Profile Summary Cards, local `git` over SSH.

## Global Constraints

- Use a near-black base with cyan and magenta signal accents.
- The banner must combine a Dubai skyline, an audio waveform, and a restrained code grid without a portrait or generated person.
- Important identity text must remain native Markdown/HTML rather than being baked into the artwork.
- Only `Marshall3572/Marshall3572` may be modified.
- The README must remain useful if external statistic images fail.
- No JavaScript, embedded scripts, unsupported CSS, or new runtime dependencies.

---

### Task 1: Create The Midnight Signal Banner

**Files:**
- Create: `assets/midnight-signal-banner.png`

**Interfaces:**
- Consumes: the visual direction in `docs/superpowers/specs/2026-07-17-midnight-signal-profile-design.md`
- Produces: a 1280x360 PNG referenced by `README.md` as `./assets/midnight-signal-banner.png`

- [x] **Step 1: Generate the banner asset**

Use the image generation tool with this exact prompt:

```text
Create a cinematic 1280x360 panoramic banner for a senior frontend engineer's GitHub profile. Midnight-black background, precise cyan and hot-magenta signal lines, a recognizable but minimal Dubai skyline silhouette including the Burj Khalifa, a horizontal audio waveform that transforms into clean code-grid geometry, subtle glass reflections, premium album-cover energy, high contrast, generous negative space, crisp technical detail. No people, no portraits, no logos, no brand marks, no words, no letters, no numbers, no UI mockups, no gradients that dominate the image. Keep the skyline and waveform readable when the image is reduced to mobile width.
```

Save the resulting image as `assets/midnight-signal-banner.png`.

- [x] **Step 2: Verify the asset**

Run:

```bash
file assets/midnight-signal-banner.png
sips -g pixelWidth -g pixelHeight assets/midnight-signal-banner.png
```

Expected: a valid PNG with width `1280` and height `360`. If the generator returns a different aspect ratio, crop it to 1280x360 while preserving the central skyline and waveform.

### Task 2: Rewrite The Profile README

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: `assets/midnight-signal-banner.png` from Task 1
- Produces: a GitHub-renderable profile with the sections `Current Signal`, `Selected Work`, `Toolkit`, and a collapsed `GitHub Signal`

- [x] **Step 1: Replace the existing README**

Set `README.md` to the following content:

````markdown
<div align="center">

<img width="100%" src="./assets/midnight-signal-banner.png" alt="Midnight Signal artwork with the Dubai skyline, an audio waveform, and a cyan-magenta code grid" />

<h1>MARSHALL Z</h1>

<p><strong>Frontend Engineer @ TikTok</strong></p>

<p>Dubai, UAE | Building interfaces with rhythm.</p>

<a href="https://github.com/Marshall3572?tab=followers"><img src="https://img.shields.io/github/followers/Marshall3572?label=FOLLOWERS&style=flat-square&logo=github&color=00e5ff&labelColor=09090b" alt="GitHub followers" /></a>
<a href="https://juejin.cn/user/2920721089567463"><img src="https://img.shields.io/badge/JUEJIN-1E80FF?style=flat-square&logo=juejin&logoColor=white" alt="Juejin profile" /></a>
<a href="https://www.jianshu.com/u/a10896bf618e"><img src="https://img.shields.io/badge/JIANSHU-EA6F5A?style=flat-square&logo=readme&logoColor=white" alt="Jianshu profile" /></a>

</div>

## Current Signal

- `ROLE` Frontend Engineer @ TikTok
- `BASE` Dubai, UAE
- `FOCUS` Product UI | Design Systems | Developer Experience
- `MODE` React | Vue | TypeScript | Go
- `ENERGY` Clean interfaces with hip-hop rhythm

I build product interfaces that stay sharp under real-world complexity: clear interaction, durable component boundaries, and tooling that keeps teams moving.

## Selected Work

### 01 / [DATA VISUALIZATION](https://github.com/Marshall3572/Data-visualization)

A large-screen data dashboard exploring dense, high-impact information design with React and ECharts.

`React` `ECharts` `Vite` `Sass`

### 02 / [MARSHALL DESIGN](https://github.com/Marshall3572/MarshallDesign)

A Vue component-library experiment focused on reusable UI, documentation, and a lightweight build workflow.

`Vue` `Vite` `Rollup` `Prism`

## Toolkit

<p align="center">
  <img src="https://skillicons.dev/icons?i=ts,js,react,vue,nextjs,nodejs,go,html,css,sass,vite,git&perline=12" alt="TypeScript, JavaScript, React, Vue, Next.js, Node.js, Go, HTML, CSS, Sass, Vite, and Git" />
</p>

<details>
  <summary><strong>GitHub Signal</strong></summary>
  <br />
  <p align="center">
    <img width="49%" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=Marshall3572&theme=github_dark" alt="Marshall's GitHub statistics" />
    <img width="49%" src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=Marshall3572&theme=github_dark" alt="Marshall's repositories by language" />
  </p>
</details>

---

<p align="center">
  <strong>Make it useful. Make it clear. Give it rhythm.</strong><br />
  <a href="https://github.com/Marshall3572">GitHub</a> |
  <a href="https://juejin.cn/user/2920721089567463">Juejin</a> |
  <a href="https://www.jianshu.com/u/a10896bf618e">Jianshu</a>
</p>
````

- [x] **Step 2: Verify required and removed content**

Run:

```bash
rg -n 'MARSHALL Z|Current Signal|Selected Work|DATA VISUALIZATION|MARSHALL DESIGN|Toolkit|GitHub Signal' README.md
rg -n 'readme-typing-svg|What I Like Building|tally_book|/epic|capsule-render' README.md
git diff --check
```

Expected: the first search finds every required section, the second search returns no matches, and `git diff --check` exits successfully.

### Task 3: Validate Assets, Links, And Rendering

**Files:**
- Verify: `README.md`
- Verify: `assets/midnight-signal-banner.png`

**Interfaces:**
- Consumes: the finished README and banner
- Produces: evidence that local content and externally referenced assets render successfully

- [x] **Step 1: Check local asset and external endpoints**

Run `test -s assets/midnight-signal-banner.png`, then request each unique external URL used by the README with `curl -L -s -o /dev/null -w '%{http_code}'`.

Expected: the local asset is non-empty; profile, project, social, badge, skill-icon, and statistic URLs return HTTP `200` or a successful `3xx` redirect.

- [ ] **Step 2: Inspect the banner at desktop and mobile crops**

Open `assets/midnight-signal-banner.png` at its original size, then create a temporary narrow preview that scales the full image to 390 pixels wide without changing its aspect ratio.

Expected: the skyline and waveform remain recognizable at both widths, the image contains no unintended text or people, and the focal content is not clipped.

### Task 4: Commit, Push, And Verify Remote State

**Files:**
- Commit: `README.md`
- Commit: `assets/midnight-signal-banner.png`
- Commit: `docs/superpowers/plans/2026-07-17-midnight-signal-profile.md`

**Interfaces:**
- Consumes: verified repository changes
- Produces: the published `main` branch of `Marshall3572/Marshall3572`

- [x] **Step 1: Verify the final diff**

Run:

```bash
git status --short --branch
git diff --check
git diff --stat origin/main...HEAD
git diff -- README.md
```

Expected: only the design document, implementation plan, banner, and README are changed; no whitespace errors are reported.

- [ ] **Step 2: Commit the implementation**

Run:

```bash
git add README.md assets/midnight-signal-banner.png docs/superpowers/plans/2026-07-17-midnight-signal-profile.md
git commit -m "Refresh profile with Midnight Signal design"
```

Expected: one implementation commit containing the banner, README, and implementation plan.

- [ ] **Step 3: Push directly to main**

Run:

```bash
git push origin main
```

Expected: `main` advances on `github.com:Marshall3572/Marshall3572.git`.

- [ ] **Step 4: Verify the remote result**

Fetch the remote `README.md` through the connected GitHub app, compare `git rev-parse HEAD` with `git ls-remote origin refs/heads/main`, and inspect `https://github.com/Marshall3572` at approximately 1440x900 and 390x844.

Expected: the remote README contains `MARSHALL Z`, `Current Signal`, and the local banner path; the remote branch SHA equals local `HEAD`; the banner is visible, text does not overlap or clip, the project panels scale coherently, and the statistics remain collapsed by default.
