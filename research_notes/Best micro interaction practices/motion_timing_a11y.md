# Motion Timing, Easing, Performance & Accessibility for Micro-Interactions

## What duration ranges do experts recommend for UI micro-interactions?

### Takeaway
Expert guidance clusters micro-interaction feedback around **~100–160ms**, standard UI chrome (tooltips/dropdowns) around **125–250ms**, and larger surfaces (modals/drawers) around **200–500ms**, with a strong practitioner rule that routine UI motion should stay **under ~300ms**; exits are typically shorter than enters.

### Cited Findings
- Nielsen Norman Group: most UX animations should fall in **100–500ms**; simple feedback (checkbox/toggle) ≈ **100ms**; substantial changes (modal into view) ≈ **200–300ms**; at **500ms** animations often feel like a drag; practical sweet range often **100–400ms**, with **400ms** reserved for large travel on large screens — [NN/G: Executing UX Animations](https://www.nngroup.com/articles/animation-duration/)
- NN/G: entering/appearing objects usually need a **subtly longer** duration than exiting/disappearing; example: popup **300ms** appear vs **200–250ms** disappear — [NN/G](https://www.nngroup.com/articles/animation-duration/)
- Emil Kowalski (published skill / taste notes): button press **100–160ms**; tooltips/small popovers **125–200ms**; dropdowns/selects **150–250ms**; modals/drawers **200–500ms**; rule of thumb: **UI animations stay under 300ms**; a **180ms** select feels more responsive than **400ms** — [emilkowalski/skills animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md); [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips); [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste)
- Emil Kowalski (Agents with Taste duration table): micro-interactions **100–150ms**; standard UI (tooltips, dropdowns) **150–250ms**; modals/drawers **200–300ms**; exits can be **~20% faster** than entrance; larger elements animate slower; longer travel → longer duration — [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste)
- Material Design 3 (legacy easing/duration system, still used for transitions; spring physics is the newer default for components): suggested pairs — Emphasized on-screen **500ms**, Emphasized decelerate enter **400ms**, Emphasized accelerate exit **200ms**; Standard on-screen **300ms**, Standard decelerate enter **250ms**, Standard accelerate exit **200ms** — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- Material Design 3: scale duration with transition size (example small area **200ms**, large area **500ms**); exits shorter than enters because exits need less attention — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- Material Web motion tokens (generated from Material 3): short durations **50 / 100 / 150 / 200ms**; medium **250 / 300 / 350 / 400ms**; long **450 / 500 / 550 / 600ms**; extra-long **700–1000ms** — [material-web `_md-sys-motion.scss`](https://raw.githubusercontent.com/material-components/material-web/main/tokens/versions/v0_192/_md-sys-motion.scss)
- Material Design 2 (historical, still widely cited): mobile transitions often ~**300ms**; enter ~**225ms**, leave ~**195ms**; large/complex up to ~**375ms**; transitions **>400ms** may feel slow; desktop animations should be faster/simpler, typically **150–200ms**; small controls (e.g. switch) cited at **100ms**; drawer open **250ms** / close **200ms** — [M2 Duration & easing](https://m2.material.io/guidelines/motion/duration-easing.html)
- NN/G cites Material Design toggle feedback at **100ms** as a microinteraction pattern — [NN/G](https://www.nngroup.com/articles/animation-duration/)
- Apple HIG (via App Store accessibility criteria / WWDC springs): no fixed public ms table for micro-interactions; guidance emphasizes **brevity and precision** in feedback animations, purposeful motion, and spring duration chosen by feel rather than fixed cubic-bezier tables — [Apple Reduced Motion evaluation criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/); [WWDC23 Animate with springs](https://developer.apple.com/videos/play/wwdc2023/10158/); [HIG Motion](https://developer.apple.com/design/human-interface-guidelines/motion)
- web.dev: target **60 FPS** for smooth animation; each frame budget ≈ **16.7ms** (1000/60) — [web.dev: Why are some animations slow?](https://web.dev/articles/animations-overview)

### Inferences
- For product UI micro-interactions (press, toggle, tooltip, menu), converging practice is **~100–250ms**, not Material’s full-screen **400–500ms** emphasized transitions.
- Treat Material’s longer durations as guidance for **large spatial transitions**; treat Emil/NN/G ranges as the better default for **repeated chrome**.
- Where sources conflict on absolute caps (Emil “under 300ms” vs Material enter **400ms** / on-screen **500ms**), prefer the shorter band for high-frequency interactions and Material’s longer band only for infrequent, large-area motion.

### Gaps
- Official Apple HIG Motion page did not yield extractable fixed duration numbers (JS-rendered docs); no reliable primary Apple ms ranges for button/tooltip/modal were found.
- animations.dev course content behind waitlist; public Emil writing + published skill were used instead of course internals.


## What easing curves are recommended for enter vs exit vs press?

### Takeaway
Most modern web craft recommends **strong ease-out** for enter (and often exit), **ease-in-out** for on-screen moves, and **short, snappy press feedback**; Material instead pairs **decelerate (ease-out-like) for enter** and **accelerate (ease-in-like) for permanent exit**—a documented conflict with Emil Kowalski’s “never ease-in on UI” rule.

### Cited Findings
- Emil Kowalski easing flowchart: entering or exiting → **ease-out**; moving/morphing on screen → **ease-in-out**; hover/color → **ease**; constant motion → **linear**; default → **ease-out**; **never `ease-in` on UI** because it starts slow and feels delayed — [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste); [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md); [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips)
- Emil: same duration (**300ms**) with `ease-in` vs `ease-out` on a dropdown—`ease-out` feels faster because it accelerates early — [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips)
- Emil recommended custom curves (built-in CSS easings “too weak”):
  - `--ease-out: cubic-bezier(0.23, 1, 0.32, 1)`
  - `--ease-in-out: cubic-bezier(0.77, 0, 0.175, 1)`
  - `--ease-drawer: cubic-bezier(0.32, 0.72, 0, 1)` (iOS-like / Ionic)
  — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Emil press guidance: subtle **`scale(0.97)`** on `:active` for button press responsiveness; press duration band **100–160ms** — [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips); [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste); [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Emil: don’t enter from **`scale(0)`**; start from **`scale(0.9–0.97)`** + opacity — [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips); [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Material Design 3 easing roles:
  - **Begin and end on screen** → Emphasized (snappy takeoff, soft landing)
  - **Enter screen** → Emphasized **decelerate** (peak velocity → gentle rest)
  - **Exit permanently** → Emphasized **accelerate** (rest → peak velocity; feels non-retrievable)
  - **Exit temporarily** → Emphasized (ends at rest just off-screen; feels retrievable)
  — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- Material Web / Flutter M3 cubic-bezier tokens:
  - Emphasized: `cubic-bezier(0.2, 0, 0, 1)`
  - Emphasized decelerate: `cubic-bezier(0.05, 0.7, 0.1, 1)`
  - Emphasized accelerate: `cubic-bezier(0.3, 0, 0.8, 0.15)`
  - Standard: `cubic-bezier(0.2, 0, 0, 1)`
  - Standard decelerate: `cubic-bezier(0, 0, 0, 1)`
  - Standard accelerate: `cubic-bezier(0.3, 0, 1, 1)`
  - Legacy standard: `cubic-bezier(0.4, 0, 0.2, 1)`
  - Legacy decelerate: `cubic-bezier(0, 0, 0.2, 1)`
  - Legacy accelerate: `cubic-bezier(0.4, 0, 1, 1)`
  — [material-web motion tokens](https://raw.githubusercontent.com/material-components/material-web/main/tokens/versions/v0_192/_md-sys-motion.scss); [Flutter `Easing`](https://github.com/flutter/flutter/blob/main/packages/flutter/lib/src/material/motion.dart)
- Material note: Emphasized set is preferred for M3 style; **Standard set is fallback for Web/iOS** where Emphasized support is limited — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- Material note: newer M3 Expressive motion uses **springs**; easing/duration system is **legacy/fallback for transitions** and “no longer maintained” for new component work — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- NN/G: prefer **ease-out** for most motion (responsive start, eye can track rest); **ease-in** sometimes for exits (accelerates out of frame); linear motion usually feels unnatural — [NN/G](https://www.nngroup.com/articles/animation-duration/)
- Apple WWDC23 springs: prefer choosing perceptual **duration** then **bounce**; bounce **0** is versatile default; ~**0.15** feels brisk with longer tail; ~**0.30** noticeably bouncy; be cautious above ~**0.4** for UI — [WWDC23 Animate with springs](https://developer.apple.com/videos/play/wwdc2023/10158/)
- Emil springs (when used): e.g. `{ type: "spring", duration: 0.5, bounce: 0.2 }` or mass/stiffness/damping; keep bounce **0.1–0.3**; avoid bounce in most UI except playful/drag-to-dismiss — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)

### Inferences
- **Enter:** consensus across Emil, NN/G, and Material decelerate tokens → ease-out / decelerate.
- **Exit:** conflict — Emil uses ease-out for exit; Material uses accelerate for permanent exit; NN/G often uses ease-in for exit. For web micro-interactions, Emil’s ease-out-for-both is the more common modern craft rule; Material accelerate is intentional for “dismiss forever” semantics.
- **Press:** short duration + slight scale-down (`0.97`) is the clearest practitioner pattern; Material does not publish a dedicated “press easing” cubic distinct from short utility transitions.

### Gaps
- No single authoritative cubic-bezier specifically labeled “press” in Material or Apple HIG primary docs.
- Spring parameter tables for Material’s newer physics system were not fully extractable from the JS-rendered M3 overview page in this pass.


## How should prefers-reduced-motion be handled?

### Takeaway
Honor OS/browser **`prefers-reduced-motion: reduce`** by removing or replacing **non-essential spatial motion**; WCAG treats this as a sufficient technique for **2.3.3 Animation from Interactions (AAA)**. Reduced motion means **minimize non-essential movement**, not necessarily delete every visual transition—opacity/color/instant state can remain when they don’t imply movement.

### Cited Findings
- Media query values: `no-preference` and `reduce`; `reduce` means interfaces should minimize movement/animation, preferably removing all **non-essential** movement — [web.dev prefers-reduced-motion](https://web.dev/articles/prefers-reduced-motion); [MDN prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)
- WCAG 2.2 SC **2.3.3 Animation from Interactions (Level AAA)**: “Motion animation triggered by interaction can be disabled, unless the animation is essential…” — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions); [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- WCAG definition nuance: **motion animation** = steps that create illusion of movement / smooth transition of perceived size/shape/position; **does not include** changes of color, blurring, or opacity that do **not** change perceived size/shape/position — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
- WCAG solutions (any one): avoid unnecessary animation; provide a user control to turn off non-essential interaction animation; or use the UA/OS reduce-motion feature — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
- Sufficient technique **C39**: use `@media (prefers-reduced-motion: reduce)` to disable motion, or inverse pattern `@media (prefers-reduced-motion: no-preference)` to enable motion only when allowed — [WAI Technique C39](https://www.w3.org/WAI/WCAG22/Techniques/css/C39)
- MDN: preference value is **`reduce`, not “none”**—users expect motion animation disabled unless essential; do not treat as require `* { animation: none !important; }` for every effect — [MDN prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)
- MDN example pattern: replace vestibular-triggering **scale pulse** with gentler **opacity dissolve** under `reduce` — [MDN prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)
- web.dev: also listen in JS via `matchMedia('(prefers-reduced-motion: reduce)')` and stop Web Animations when preference changes; can conditionally load animation CSS; can gate animated `<picture>` sources with `media="(prefers-reduced-motion: no-preference)"` — [web.dev prefers-reduced-motion](https://web.dev/articles/prefers-reduced-motion)
- Emil: ship reduced-motion with every animation; keep opacity/color; drop transform-based motion; “fewer and gentler,” not always zero — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Apple App Store Reduced Motion criteria: disable/change depth simulation (parallax, animated blur, DOF), multi-axis/multi-speed/spinning/vortex, and consider stopping auto-advancing carousels; for decorative motion stop entirely; for meaningful motion replace with **dissolve / highlight fade / color shift** rather than removing all feedback — [Apple Reduced Motion evaluation criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/)
- Apple SwiftUI: `accessibilityReduceMotion` true → UI should avoid large animations, especially those that simulate the third dimension — [accessibilityReduceMotion](https://developer.apple.com/documentation/swiftui/environmentvalues/accessibilityReduceMotion)
- Related WCAG autoplay motion: SC **2.2.2 Pause, Stop, Hide (A)** — moving/blinking/scrolling that starts automatically, lasts **>5 seconds**, and is parallel with other content needs pause/stop/hide unless essential — [Understanding 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide)

### Inferences
- Practical web pattern: under `reduce`, remove `transform`/`translate`/`scale` motion; keep instant state or short opacity/color fades when they preserve comprehension.
- Prefer dual strategy: respect `prefers-reduced-motion` **and** offer an in-product motion toggle for sites with heavy decorative motion (WCAG explicitly lists both).
- Essential scrolling of content is allowed; parallax and decorative scroll-linked motion are the high-risk cases.

### Gaps
- WCAG 2.3.3 is AAA, so AA-only products may not be normatively required to meet it; still widely treated as best practice via OS preference support.
- Primary sources disagree slightly on whether opacity-only fades are always “safe”; WCAG’s motion-animation definition supports keeping non-positional opacity/color, while some practitioner guides still strip all transitions.


## What performance pitfalls (layout thrash, transition:all) should be avoided?

### Takeaway
Animate **`transform` and `opacity`** (compositor-friendly); avoid layout-triggering properties (`width`/`height`/`top`/`left`/`margin`/`padding`, etc.); **never use `transition: all`**—name exact properties. Use `will-change` sparingly and temporarily.

### Cited Findings
- web.dev: modern browsers can animate **`transform` and `opacity` cheaply**; animating anything else often fails smooth **60 FPS** — [Why are some animations slow?](https://web.dev/articles/animations-overview)
- web.dev rendering pipeline: Style → Layout → Paint → Composite; animating layout forces paint+composite too; compositor-only changes are cheapest — [animations-overview](https://web.dev/articles/animations-overview)
- web.dev guide: move with `translate`/`rotate`, resize with `scale`, show/hide with `opacity`; avoid properties that trigger layout or paint unless necessary; restrict to opacity/transform to stay on compositing stage — [How to create high-performance CSS animations](https://web.dev/articles/animations-guide)
- web.dev: CSS animations / Web Animations often run on the **compositor thread**, so they can continue while main-thread JS/layout work is busy; layout/paint animations still require main thread regardless of CSS vs JS — [animations-overview](https://web.dev/articles/animations-overview)
- web.dev Transitions module: prefer GPU-friendly `transform`/`opacity` over `width`/`height` which push other content and force recalculation every frame — [web.dev Learn CSS: Transitions](https://web.dev/learn/css/transitions)
- web.dev on `will-change`: use sparingly; only if you encounter performance issues; spec guidance is to apply when change is imminent; creating layers costs memory/GPU bandwidth — [animations-guide](https://web.dev/articles/animations-guide); [animations-overview](https://web.dev/articles/animations-overview)
- Emil hard rule: **`transform` and `opacity` only** (clip-path as rare fourth; height only for accordion); never animate `width`/`height`/`margin`/`padding`/`top`/`left`; **never `transition: all`**—name exact properties — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Emil: in Motion library, prefer full `transform: "translateX(...)"` string over `x`/`y`/`scale` shorthands under load (claims hardware acceleration difference) — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Core Web Vitals practitioner analysis (citing Almanac + Google CLS research): `transition: all` is extremely common and often unintentionally animates layout properties, causing CLS during load; layout-inducing animated properties include `width`, `height`, `margin`, `padding`, `top`/`left`/`right`/`bottom`, `border-width`, `font-size`; `transform`/`opacity` are CLS-safe; named property transitions recommended — [Layout Shift caused by CSS transitions](https://www.corewebvitals.io/pagespeed/layout-shift-caused-by-css-transitions)
- WebKit engineering note: `transition: all` historically caused browsers to consider/list huge sets of animatable properties and was costly enough to warrant engine optimizations—evidence that `all` is an expensive anti-pattern even before layout thrash — [WebKit PR #18054](https://github.com/WebKit/WebKit/pull/18054)

### Inferences
- “Layout thrash” in micro-interactions usually means repeatedly forcing style+layout+paint by animating geometric CSS instead of transforms.
- `transition: all` is a dual hazard: performance cost + accidental animation of layout/paint properties (and CLS risk).
- Hover-only size changes are especially dangerous for CLS because hover is not excluded the same way as click/tap in CLS attribution models (per Core Web Vitals article citing Google research).

### Gaps
- Exact cross-browser guarantee that *all* `transform`/`opacity` animations stay off main thread is nuanced (depends on layers, filters, stacking); web.dev states “in many cases,” not absolute.
- Emil’s Motion `x`/`y` vs `transform` string claim is practitioner guidance from his skill; not independently verified against Motion docs in this pass.


## What guidance comes from Emil Kowalski, Google Material motion, WCAG, or similar?

### Takeaway
The shared doctrine is: keep motion **short, purposeful, interruptible, and optional**; use **physical-feeling easing** (or springs); respect **reduced motion** for vestibular safety; and keep implementation on **compositor-friendly properties**. Sources diverge mainly on **exit easing** and **how long large transitions may run**.

### Cited Findings

#### Emil Kowalski / animations.dev ecosystem
- Course framing: choose correct easing, duration, and properties for performance; stop guessing — [animations.dev](https://animations.dev/)
- Frequency gate: **100+/day** interactions (e.g. keyboard-opened command palette) → **no animation**; tens/day → near-imperceptible only; occasional (modals) → standard; rare/first-time → delight budget — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- Purpose must be named (feedback, spatial consistency, state, prevent jarring change, explanation, delight) or don’t animate — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)
- High-frequency hover/list animations can become annoying; remove if seen tens/hundreds of times daily — [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips)
- Origin-aware popovers (`transform-origin` at trigger); subsequent tooltips skip delay/animation — [7 Practical Animation Tips](https://emilkowal.ski/ui/7-practical-animation-tips)
- Gate hover motion with `@media (hover: hover) and (pointer: fine)` — [animate SKILL](https://raw.githubusercontent.com/emilkowalski/skills/main/skills/animate/SKILL.md)

#### Google Material motion
- M3 suggested easing/duration pairs and enter-longer / exit-shorter principle — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- Concrete cubic-bezier + duration tokens in Material Web — [material-web motion tokens](https://raw.githubusercontent.com/material-components/material-web/main/tokens/versions/v0_192/_md-sys-motion.scss)
- Migration note: spring/physics system preferred for new expressive components; easing/duration retained for transitions/fallback — [M3 Applying easing and duration](https://m3.material.io/styles/motion/easing-and-duration/applying-easing-and-duration)
- M2 still useful for historical mobile/desktop duration scaling (desktop faster **150–200ms**) — [M2 Duration & easing](https://m2.material.io/guidelines/motion/duration-easing.html)

#### WCAG / WAI (vestibular safety)
- SC **2.3.3** (AAA): disable non-essential interaction-triggered motion animation — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
- Vestibular reactions can include dizziness, nausea, headaches, migraine, bed rest — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions); [web.dev prefers-reduced-motion](https://web.dev/articles/prefers-reduced-motion)
- High-risk patterns called out: parallax, non-essential scroll-linked movement — [Understanding 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
- Technique C39 for CSS media query implementation — [C39](https://www.w3.org/WAI/WCAG22/Techniques/css/C39)
- SC **2.2.2** covers auto-starting motion **>5s** — [Understanding 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide)
- MDN warns scaling/panning large objects can be vestibular triggers — [MDN prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)

#### Apple
- Make motion optional; don’t communicate important info by motion alone; use haptics/audio alternatives; aim for brief, precise feedback; gratuitous motion can cause physical discomfort — synthesized from Apple Reduced Motion criteria + SwiftUI reduce-motion docs + HIG Motion URL (page body not fully extractable) — [Reduced Motion criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/); [accessibilityReduceMotion](https://developer.apple.com/documentation/swiftui/environmentvalues/accessibilityReduceMotion); [HIG Motion](https://developer.apple.com/design/human-interface-guidelines/motion)
- Prefer springs; bounce 0 default; caution with high bounce — [WWDC23 Animate with springs](https://developer.apple.com/videos/play/wwdc2023/10158/)

#### web.dev / MDN performance + a11y
- Prefer transform/opacity; 60 FPS / 16.7ms frame budget — [animations-overview](https://web.dev/articles/animations-overview); [animations-guide](https://web.dev/articles/animations-guide)
- Implement and dynamically respect `prefers-reduced-motion` — [web.dev](https://web.dev/articles/prefers-reduced-motion); [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)

#### NN/G (adjacent well-known practitioner research)
- Duration bands, ease-out preference, accessibility caution for parallax/scroll-jacking, respect reduce-motion — [NN/G animation duration](https://www.nngroup.com/articles/animation-duration/)

### Inferences
- A durable “modern UI motion stack” for micro-interactions:
  1. **Duration:** 100–160ms press; 125–250ms chrome; ≤300ms default UI; Material 400–500ms only for large infrequent transitions
  2. **Easing:** strong ease-out enter; ease-out or Material accelerate for exit depending on dismiss semantics; avoid weak built-in curves for deliberate motion
  3. **A11y:** honor `prefers-reduced-motion`; strip spatial motion; keep essential feedback via opacity/color/instant change
  4. **Perf:** animate transform/opacity only; ban `transition: all`
- Biggest expert disagreement to preserve for implementers: **Material accelerate exit** vs **Emil ease-out exit**.

### Gaps
- Full text of Apple HIG Motion “best practices” section was not recoverable via fetch (documentation site returned shell only).
- Material Expressive spring composite token numeric tables were only partially available from overview snippets; prefer the published easing/duration token file for concrete CSS values until spring specs are pulled from a non-JS source.
- WCAG SC **2.3.1 Three Flashes** (seizures) is related but distinct from vestibular motion; not deeply expanded here beyond NN/G’s mention of flashing/hard cuts.
