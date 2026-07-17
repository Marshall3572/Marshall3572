# Midnight Signal GitHub Profile Design

## Goal

Turn the existing GitHub profile README into a recognizable personal identity for Marshall Z. The page should feel like a focused frontend engineer's profile, not a collection of common README widgets.

## Visual Direction

Use a "Midnight Signal" visual language:

- near-black base with cyan and magenta signal accents
- a custom panoramic banner combining a Dubai skyline, an audio waveform, and a restrained code grid
- no portrait or generated person
- no important text baked into the generated artwork; identity text remains native Markdown/HTML for sharp rendering and accessibility
- compact spacing and a clear reading order on desktop and mobile

## Information Architecture

1. Custom banner.
2. Identity block: `MARSHALL Z`, `Frontend Engineer @ TikTok`, and `Dubai - Building interfaces with rhythm`.
3. Minimal social badges for GitHub, Juejin, and Jianshu.
4. `Current Signal`: current role, engineering focus, primary tools, and personal creative influence.
5. `Selected Work`: feature only `Data-visualization` and `MarshallDesign`, each with an accurate one-sentence description and direct repository link.
6. `Toolkit`: a compact icon row rather than a large inventory.
7. Collapsible GitHub activity section so third-party statistics stay secondary.
8. A short closing line with direct contact links.

## Content Changes

- Remove the animated typing block; the banner and identity block provide the first-screen signal.
- Remove the generic four-cell `What I Like Building` table.
- Remove `tally_book` and `epic` from featured work because their current repository pages do not communicate the profile's strongest story.
- Replace four Open Graph repository images with two concise project panels.
- Keep dynamic statistics out of the main reading path and reduce reliance on third-party image services.
- Remove the decorative wave footer and duplicated navigation.

## Asset Strategy

Create one repository-owned 1280x360 PNG banner at `assets/midnight-signal-banner.png`. It should retain useful composition when scaled down and contain no small text. All remaining external images must have descriptive alt text and use stable HTTPS endpoints.

## Compatibility And Failure Handling

- The README must remain useful if external statistic images fail.
- Banner and layout widths use responsive HTML attributes supported by GitHub Markdown.
- No JavaScript, embedded scripts, or unsupported CSS.
- Repository links and social links must be checked before publishing.

## Verification

- Confirm the README structure and links locally.
- Confirm every referenced image returns a successful HTTP response.
- Inspect the rendered GitHub profile at desktop width and a narrow viewport.
- Push to `main`, then fetch the remote README and compare the published commit with local `HEAD`.

## Scope

Only `Marshall3572/Marshall3572` changes in this iteration. Featured project repositories are read-only inputs and will not be modified.
