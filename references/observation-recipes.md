# Observation Recipes

Read only the recipe that matches the page and question.

## Static Page or News Article

- Capture the initial viewport for visual hierarchy.
- Capture the full page only when placement across the article matters.
- Inspect headline, byline, publication time, captions, and visible labels through DOM or accessibility data.
- Distinguish editorial content, navigation, related stories, and promotional modules.
- Do not treat an image caption as proof of what the image visibly contains; inspect both.

## Product or Commerce Page

- Capture the hero area, selected product media, price and purchase controls, and visible offer language.
- Record the currently selected variant. Do not combine images or prices from unselected variants.
- Inspect badges such as sponsored, promoted, limited offer, and affiliate disclosure.
- Sample reviews or comments only from visibly loaded items. State the sample size before summarizing sentiment.
- Treat urgency timers and scarcity messages as page claims, not independently verified facts.

## Video or Livestream

- Verify that the player contains rendered frames rather than a poster, loading state, or black screen.
- Start muted if playback is required. Inspect subtitles or captions when available.
- Capture at least three stable player-region frames before describing an event or product change.
- Use a focused player crop for visual content and a wider viewport for surrounding title, product, and chat context.
- Report whether the stream appears live based on visible live markers or changing frames; do not infer live status from the player component alone.
- Audio claims require actual audio or subtitles. Never infer speech from mouth movement.

## Chat, Comments, or Social Feed

- Capture the visible region before scrolling.
- Prefer DOM text for exact wording and screenshots for placement, density, reactions, and visible emphasis.
- Observe two screenfuls at most by default. State that conclusions describe the visible sample, not the entire audience.
- Separate author content, pinned or moderator messages, platform notices, ads, and ordinary user messages.
- Do not identify people or infer sensitive traits from avatars or images.

## Dashboard, Chart, or Market Page

- Capture the whole dashboard for layout, then each relevant chart or KPI at readable scale.
- Use DOM, accessible labels, tooltips, or page data for exact numbers; do not estimate precise values from pixels when structured values exist.
- Keep filters, time range, units, timezone, and selected tab visible in the evidence.
- Use multiple frames only when the question concerns updates or movement.
- Describe apparent trends from the selected range, not causation.

## Advertising and Recommendation Modules

Classify with the strongest available evidence:

1. **Confirmed:** visibly labeled Ad, Sponsored, Promoted, or equivalent.
2. **Strongly indicated:** separate commercial card with advertiser identity or purchase CTA.
3. **Likely:** placement and visual treatment resemble a promotional module but lack an explicit label.
4. **Unknown:** insufficient evidence.

Do not classify solely from a CSS class name or network endpoint.

## Access Gates and CAPTCHA Handoff

Capture the obstruction first because it is part of the rendered experience. Then classify it:

1. **Soft gate:** A consent, newsletter, age-neutral notice, or optional login prompt has a visible close or cancel control.
2. **Partial obstruction:** The gate covers part of the page, but visible screenshots and rendered text still support the answer.
3. **Hard gate:** A CAPTCHA, paywall, mandatory login, OTP, or access-control screen blocks required evidence.

For a soft gate:

- Prefer the parent dialog's visible close or cancel control over controls inside a nested verification widget.
- Follow one grounded dismissal path, then take a fresh screenshot or DOM snapshot.
- Stop dismissing if the gate reappears. Do not loop or escalate to DOM/CSS removal.

For a partial obstruction:

- Continue only with evidence that is genuinely visible or exposed as rendered text.
- Label claims as observed behind an overlay and state what remained blocked.
- Do not claim continuous motion when the obstruction prevented stable frame sampling.

For a hard gate:

1. Try one already-available browser with the user's existing signed-in session when the user did not require a specific browser. Do not inspect or export cookies, storage, passwords, or tokens.
2. If still blocked, keep and show the exact tab when the host supports user handoff.
3. Ask the user to complete the CAPTCHA, login, or OTP manually and tell the agent when finished. The user must enter all credentials and sensitive codes.
4. After confirmation, reclaim the same tab without reloading. Capture a fresh viewport and verify that the gate is gone before continuing.
5. If the gate returns once, stop and report that the site is rejecting the automated session.

Never drag a puzzle, recognize a challenge answer, use an automated solver, modify browser fingerprints, remove blur or overlays through code, bypass a paywall, or obtain challenge cookies through an alternate request path.

State which observations came from the blocked first view and which came after a permitted dismissal or user handoff.

## Region Selection

Use visible geometry or element bounds to keep crops reproducible. Add a small margin around the target so labels and surrounding context remain visible. Avoid enlarging a tiny crop until artifacts could be mistaken for real detail.

## Dynamic Change Log

Keep the log compact:

```text
T+0s   Player shows a presenter holding a dark rectangular device.
T+4s   The device remains visible; a price card appears beside the player.
T+9s   The presenter rotates the device; chat density visibly increases.
```

Use neutral descriptions when object identity is uncertain. Prefer "dark rectangular device" over guessing a specific model.
