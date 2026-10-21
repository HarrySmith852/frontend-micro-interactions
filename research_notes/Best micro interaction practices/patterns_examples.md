# High-Value Micro-Interaction Patterns and Real-World Examples

**Scope:** Actionable, frontend-implementable micro-interaction patterns with strongest UX ROI; like/favorite, toggle, and form-error craft; anti-patterns; delight vs distraction evidence.  
**Evidence legend used below:** *Research/heuristic evidence* (NN/g studies, lab tests, WCAG, classical response-time research) vs *practitioner craft / designer opinion* (Stripe, Linear-adjacent blogs, Smashing Magazine, design-engineering posts). Claims without a URL are omitted or listed under Gaps.

---

## Which micro-interaction patterns have the strongest UX ROI?

### Takeaway
Highest-ROI micro-interactions are those that **confirm system status, prevent/recover from errors, and preserve direct-manipulation feel within ~100–1000ms**—not decorative delight. Feedback for waits, button acknowledgement, toggles that apply immediately, inline form validation (timed correctly), undo after irreversible-feeling actions, and clear drag previews consistently map to usability heuristics and measured wait-tolerance gains.

### Cited Findings
- Microinteractions are defined as **trigger–feedback pairs**: a user action or system-state change produces a narrowly targeted, contextual UI response. Examples that qualify: scrollbar feedback, pull-to-refresh animation, swipe feedback, email notifications; a button with **no** click feedback is *not* a microinteraction. — [NN/g: Microinteractions in User Experience](https://www.nngroup.com/articles/microinteractions/)
- NN/g ranks microinteraction value around four jobs: **encourage engagement, display system status, provide error prevention, communicate brand**—with status and error prevention framed as core usability (Heuristic #1 visibility of system status; error prevention), not optional polish. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Classical response-time limits (still cited by NN/g as unchanged for decades): **≤0.1s** feels instantaneous (direct manipulation); **≤1.0s** keeps thought flow uninterrupted; **≤10s** keeps attention—beyond that users need explicit progress/done estimates. — [NN/g: Response Times: The 3 Important Limits](https://www.nngroup.com/articles/response-times-3-important-limits/); [NN/g: Website Response Times](https://www.nngroup.com/articles/website-response-times/)
- Progress indicators reduce uncertainty and can raise wait tolerance: in a University of Nebraska–Lincoln waiting study cited by NN/g, users who saw a **continuous moving progress bar waited on average ~3× longer** and reported higher satisfaction than users with no indicator. Guideline: **immediate acknowledgement always**; looped spinner for ~**2–9s**; **percent-done** for **≥10s**; avoid static “Loading…” and “don’t click again” warnings. — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/) (cites Nah, F. 2004, *Behaviour and Information Technology*)
- Pull-to-refresh is explicitly called out as a microinteraction whose job is system-status feedback (LinkedIn circular progress on feed refresh). — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Motion’s highest-value UX uses (NN/g research synthesis): **feedback for microinteractions**, **state-change metaphors**, **spatial navigation continuity**, and **strengthening signifiers**—not entertainment. Change blindness makes static feedback (e.i., cart badge update far from the click) easy to miss; brief motion near the trigger increases noticeability. — [NN/g: The Role of Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Toggle switches have high ROI when they **apply immediately** (like a physical light switch); if Save/Submit is required, use checkbox/radio instead—mismatched mental models cause confusion (United Airlines counterexample; iOS Airplane Mode positive example). — [NN/g: Toggle-Switch Guidelines](https://www.nngroup.com/articles/toggle-switch-guidelines/)
- Form error recovery has high task ROI: inline validation after field completion, messages next to fields, color + icon (not color alone), avoid premature validation; validation summaries should not be the *only* signal. — [NN/g: 10 Design Guidelines for Reporting Errors in Forms](https://www.nngroup.com/articles/errors-forms-design-guidelines/)
- A List Apart / CX Partners eye-tracking study: **inline validation improved form completion speed, success, and satisfaction** vs post-submit-only validation, especially for hard fields (username availability, password rules); simple fields needed less confirmation. — [A List Apart: Inline Validation in Web Forms](https://alistapart.com/article/inline-validation-in-web-forms/)
- Baymard usability testing: premature inline validation (“yelling” before the user finishes) frustrates users and can disrupt typing; remove errors as soon as the field is corrected. — [Baymard: Usability Testing of Inline Form Validation](https://baymard.com/research-articles/inline-form-validation/)
- Drag-and-drop ROI depends on **continuous spatial feedback**: ghost preview, drop-zone highlighting, and **~100ms eased preview** of sibling items moving aside before release; threshold timing for when neighbors reshuffle is a key craft decision. — [NN/g: Drag-and-Drop](https://www.nngroup.com/articles/drag-drop/)
- Stripe design engineering (Benjamin De Cock, CSSConf / Motionographer write-up): two primary reasons to animate UI—**(1) help users understand flow between states**, **(2) make the app feel faster** (“Actual speed barely matters. Perceived speed truly matters.”). Rules of thumb: animate **opacity + transform only**, keep most animations ~**300ms**, animate independently, use **custom easings**. Checkout “Remember me” view transitions and verification timing as perceived-speed craft. — [Motionographer: Why motion matters (Stripe / De Cock)](https://motionographer.com/2015/07/06/user-interface-design-why-motion-matters/)
- Linear-adjacent craft (Emil Kowalski, design engineer associated with Linear tooling/community): frequent daily actions (command palettes, keyboard nav) often need **no animation**; when used, keep UI motion generally **under 300ms**; faster spinners can improve *perceived* load speed without changing actual duration. — [emilkowal.ski: You Don't Need Animations](https://emilkowal.ski/ui/you-dont-need-animations/)
- Practitioner summary of Linear motion timings (secondary analysis, not a Linear official doc): hover ~**100–150ms**, small interactions ~**200ms**, view transitions up to ~**350ms**, spring for gesture-driven drag reorder, stagger ~**20ms**/item on filtered lists. — [DesignMD: Linear vs Vercel motion](https://www.designmd.co/blog/linear-vs-vercel-motion)

### Inferences
- **Prioritize implementation order for product teams:** (1) acknowledgement of every primary control within 100ms (pressed/disabled/loading), (2) wait feedback ladder (0–1s / 2–9s / 10s+), (3) toggles that commit immediately with optimistic UI + revert on failure, (4) form validation that prevents rework, (5) undo snackbars for delete/favorite/archive, (6) drag previews/thresholds for reorder-heavy UIs, (7) brand delight only on rare, high-emotion moments.
- Patterns with **measurable or strongly evidenced ROI** cluster around *uncertainty reduction* and *error cost reduction*, not novelty. Decorative motion has weak or negative ROI in goal-directed contexts.
- Frontend implication: invest engineering budget in **state machines** (idle → pending → success/error) and **optimistic updates** more than in Lottie flourishes.

### Gaps
- No peer-reviewed, cross-product **dollar ROI** study comparing “ship micro-interactions A vs B” for modern SaaS (Stripe/Linear/Notion) was found; most “ROI” claims are heuristic or single-study wait/form metrics.
- Notion-specific published micro-interaction case studies with measured outcomes were not located in this pass.
- Mobbin-style screen roundups generally show *what* exists, not *why* it works; no Mobbin source with rigorous causal reasoning was included.

---

## What makes a like/favorite, toggle, or form-error interaction feel good?

### Takeaway
These patterns feel good when feedback is **immediate, local to the trigger, reversible, and multi-channel (position/color/motion/icon)—without screaming at the user mid-input**. Likes need a short, non-permanent attention pulse plus easy undo; toggles need physical metaphor + instant effect; form errors need post-completion, actionable, field-adjacent messaging (with research split on submit-only vs blur validation depending on product context).

### Cited Findings

#### Like / favorite
- Gap.com favorite heart: **short pumping-heart animation** communicates state change; clicking again reverts to grey (undo). NN/g calls this appropriate because it is **subtle, brief, and distinguishes the newly favorited item** from already-favorited hearts—helping catch accidental taps on touch UIs. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Favoriting is framed as both **system-status communication** and **error prevention via undo**, not pure delight. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Asana completion: utilitarian undo toast **plus** occasional unicorn = dual microinteractions (status/undo vs brand delight). NN/g notes delight is optional; competitors like Trello can omit fanfare and still meet expectations. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)

#### Toggle
- Toggles must **deliver immediate results**; requiring Save breaks the real-world light-switch metaphor. Do not mix instant toggles with submit-gated fields on the same form. — [NN/g: Toggle-Switch Guidelines](https://www.nngroup.com/articles/toggle-switch-guidelines/)
- Labels should be **concise, non-neutral**, describing the on-state (e.g., “Email notifications”), front-loaded with keywords; avoid question phrasing and ambiguous neutrals (“Include non-maternity items?”). — [NN/g: Toggle-Switch Guidelines](https://www.nngroup.com/articles/toggle-switch-guidelines/)
- Visual design: look like a slider; **position change + high-contrast color**; beware cultural color meanings (red-as-on can conflict with “stop”); optional On/Off descriptors, but single descriptors can be ambiguous (Windows 10 example). Consistency across the app matters (Chase Bank inconsistency called out). — [NN/g: Toggle-Switch Guidelines](https://www.nngroup.com/articles/toggle-switch-guidelines/)
- GitHub Primer (design system, practitioner): toggle = **immediate boolean config**; never replace a checkbox that needs Save; show loading before flipping if server must confirm; keyboard like a button (Tab + Enter/Space); adequate touch target. — [Primer: Toggle switch](https://primer.github.io/design/components/toggle-switch/)

#### Form validation / errors
- NN/g guidelines (research-informed heuristics): prefer **inline validation after the user finishes a field**; success indicators mainly for **complex** fields (username availability, password strength); keep messages **next to fields**; use color + **icon** (+ optional subtle icon pulse—not animated text); don’t validate mid-typing for typical fields; don’t rely only on top summaries; don’t hide errors in tooltips. — [NN/g: Errors in Forms](https://www.nngroup.com/articles/errors-forms-design-guidelines/)
- Hostile / premature errors feel like being shouted at: wait until the user leaves a field for format errors; mark required fields clearly up front; reserve red/warning chrome for true errors. — [NN/g: Hostile Patterns in Error Messages](https://www.nngroup.com/articles/hostile-error-messages/)
- GOV.UK Design System (large-scale public-service research practice): **do not validate on blur by default**; validate on continue/submit; keep user-entered values; show **error summary + focus move** + per-field messages; turn off HTML5 validation. Inline-as-you-type only when research shows net benefit (e.g., character count). — [GOV.UK: Recover from validation errors](https://design-system.service.gov.uk/patterns/validation/)
- Tension noted: NN/g and Baymard favor well-timed **inline** validation; GOV.UK defaults to **submit-time** for government forms. Both agree: **don’t yell before the user finishes**. — [NN/g](https://www.nngroup.com/articles/errors-forms-design-guidelines/); [GOV.UK](https://design-system.service.gov.uk/patterns/validation/); [Baymard](https://baymard.com/research-articles/inline-form-validation/)
- A List Apart study: inline validation most valuable when answers aren’t obvious; success checkmarks on trivial fields can confuse (“Is this my correct name?”). — [A List Apart: Inline Validation](https://alistapart.com/article/inline-validation-in-web-forms/)
- WCAG: if an input error is detected, identify the item in error and describe it **in text** (not color alone). — [W3C: Understanding SC 3.3.1 Error Identification](https://www.w3.org/WAI/WCAG22/Understanding/error-identification)
- eBay registration (NN/g example): password requirements list updates dynamically while typing; leaving incomplete shows red error—microinteractions preventing rework. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)

#### Button press / loading / success (related craft)
- Immediate visual acknowledgement on press prevents double-submit; NN/g explicitly rejects “don’t click again” copy as the primary defense. — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)
- Smashing Magazine (practitioner synthesis): buttons should feel tangible via immediate visual response; shake-on-wrong-password uses a culturally shared “no” gesture. — [Smashing: Functional Animation Improves UX](https://www.smashingmagazine.com/2017/01/how-functional-animation-helps-improve-user-experience/)
- Emil Kowalski: subtle **scale-down on press** increases felt responsiveness; Sonner toast enter/exit direction supports swipe-to-dismiss spatial consistency. — [You Don't Need Animations](https://emilkowal.ski/ui/you-dont-need-animations/)

#### Drag thresholds (related high-value pattern)
- NN/g: sibling items should animate aside (~**100ms** with easing) as a **preview before release**; deciding whether overlap of edges vs cursor/center triggers reshuffle is critical to natural feel. Touch needs timing delay to separate tap vs grab. — [NN/g: Drag-and-Drop](https://www.nngroup.com/articles/drag-drop/)
- Practitioner pattern: reshuffle when dragged item’s **center crosses** neighbor edge (less twitchy than edge-touch); snap with short settle (~100ms); use activation threshold so tiny pointer noise isn’t a drag. — [Smart Interface Design Patterns: Drag-and-Drop UX](https://smart-interface-design-patterns.com/articles/drag-and-drop-ux/); [Dan Cătălin Burzo: Thresholds, offsets, and snapping](https://danburzo.ro/microinteractions/thresholds-offsets-snapping/)
- Airtable (NN/g example): drag-reorder columns show preview of new order before commit. — [NN/g: Animation Purpose in UX](https://www.nngroup.com/articles/animation-purpose-ux/)

### Inferences
- **Feel-good checklist for frontend:**
  - **Like:** optimistic fill + ≤200–300ms local motion + haptic if available + instant undo; keep motion off after settle.
  - **Toggle:** optimistic slide + synchronized track color; if network required, show pending without lying permanently; revert + inline error on failure.
  - **Form error:** validate after blur *or* on submit (choose by context), never on empty focus; `aria-invalid` + `aria-describedby`; focus management to summary on submit-time errors.
  - **Button:** pressed state <100ms; morph to spinner in-place; success check then restore or navigate.
- Conflict between GOV.UK and NN/g on *when* to validate is a product-risk decision: high-stakes / accessibility-first services → submit + summary; consumer SaaS with complex fields → blur/inline for hard fields only.

### Gaps
- No controlled study isolating “heart burst animation” vs static fill for conversion/retention was found.
- Exact millisecond specs for iOS/Material toggles appear in secondary blogs; treat platform HIG docs as authoritative for native apps (not fully re-fetched here).
- Pull-to-refresh “delight” variants (branded spinners) lack comparative usability data beyond status-feedback necessity.

---

## What anti-patterns (excessive animation, decorative motion, slow delays) hurt UX?

### Takeaway
Motion hurts when it **hijacks attention, invents artificial delay, loops without progress information, or fires on high-frequency actions**. Anti-patterns with strong evidence: scroll-triggered content delays, decorative peripheral motion, >10s spinners without percent-done, mid-typing form scolding, attention-hijacking dark patterns, and non-essential motion that ignores `prefers-reduced-motion` / vestibular needs.

### Cited Findings
- Human peripheral vision is highly motion-sensitive; irrelevant motion is hard to ignore and degrades UX (ads as classic case). NN/g: use motion with a **light touch**, primarily for feedback—not delight-first. Downtime/transition “filler” animations often frustrate usability-test participants. — [NN/g: Animation Purpose in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- **Scroll-triggered text animations** forced users to wait for content to “load”; participants complained explicitly. Users don’t distinguish artificial aesthetic delay from real performance delay. Guidelines: consider task context (high-stakes users hate “cute”); animate secondary visuals not body text; play **once**, not on every re-scroll. Even **one extra second** of delay is noticeable. — [NN/g: Scroll-Triggered Text Animations Delay Users](https://www.nngroup.com/articles/scroll-animations/)
- Animation timing: **fast** for user-initiated, already-focused actions; **slower/subtler** for system-initiated or peripheral changes. Overly frequent animations accumulate annoyance. — [NN/g: Animation for Attention and Comprehension](https://www.nngroup.com/articles/animation-usability/)
- Hipmunk loading example: **too many simultaneous animations** dilute attention—cute chipmunk + counting results + skeleton + progress + list reshuffles compete. — [NN/g: Animation Purpose in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Dark pattern: flashing sale countdown with enlarging digits hijacks attention via loss aversion. Decorative squiggle motion with no benefit distracts from content. — [NN/g: Animation Purpose in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Progress anti-patterns: **static** “Please wait”; **looped spinners >10s**; **don’t-click-again** warnings; showing a spinner for **<1s** flashes (users can’t track what happened). Percent bars that race then hang at 99% negate benefits. — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)
- Form anti-patterns: validate before input complete; error-only via tooltip; summary-only without field messages; success indicators on trivial required fields; hostile tone. — [NN/g: Form Errors](https://www.nngroup.com/articles/errors-forms-design-guidelines/); [NN/g: Hostile Error Messages](https://www.nngroup.com/articles/hostile-error-messages/); [Baymard](https://baymard.com/research-articles/inline-form-validation/)
- Toggle anti-patterns: visual flip with **no real effect**; toggles in submit forms; neutral/ambiguous labels; low-contrast on/off; inconsistent control types for same job. — [NN/g: Toggle Guidelines](https://www.nngroup.com/articles/toggle-switch-guidelines/)
- WCAG 2.3.3 Animation from Interactions: motion triggered by interaction must be **disableable** unless essential; parallax/scroll-coupled motion can trigger vestibular disorders (nausea, migraine). Prefer respect for OS reduced-motion. — [W3C: Understanding SC 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
- web.dev accessibility guidance: avoid excessive flashing (>3/sec), non-essential movement; provide pause/stop/hide for auto-playing motion lasting >5s. — [web.dev: Animation and motion](https://web.dev/learn/accessibility/motion)
- Smashing (practitioner): animation without purpose feels awkward; example PayPal receipt concept taking ~**4 seconds** before details appear is excessive vs a short fade. Ask: will it annoy on the **100th** use? — [Smashing: Functional Animation](https://www.smashingmagazine.com/2017/01/how-functional-animation-helps-improve-user-experience/)
- Emil Kowalski: animating **high-frequency** UI (Raycast open, keyboard list highlight) makes the product feel slow and breaks action–feedback coupling; rule of thumb **<300ms** when you do animate. — [You Don't Need Animations](https://emilkowal.ski/ui/you-dont-need-animations/)
- Stripe De Cock: animating layout properties (width/height) instead of transform/opacity risks jank; failing 60fps “kills” perceived smoothness. — [Motionographer / Stripe](https://motionographer.com/2015/07/06/user-interface-design-why-motion-matters/)

### Inferences
- Frontend anti-pattern watchlist: `transition: all`, layout thrash, scroll-linked `translate` on large text blocks, mandatory onboarding Lotties, skeleton shimmer that never resolves, disabled buttons with no explanation, optimistic toggles that don’t roll back.
- **Artificial delay** (including “delight” minimum animation time on common paths) is one of the costliest anti-patterns because it taxes every repetition.
- Reduced-motion support is both accessibility compliance and UX quality for a non-trivial user segment.

### Gaps
- Limited quantitative thresholds for “how much stagger is too much” beyond practitioner heuristics (e.g., Linear list stagger secondary write-up).
- Few published A/B tests isolating micro-interaction anti-patterns in production SaaS beyond lab/usability quotes.

---

## Any research or case studies on delight vs distraction?

### Takeaway
Evidence favors **functional motion first, delight sparingly**. NN/g research repeatedly finds that surface delight sours quickly, while status/error/feedback motion retains value; brand delight works when rare, on-brand, and paired with utilitarian feedback (Asana undo + occasional unicorn). Practitioner case studies (Stripe, Linear craft) optimize for **perceived speed and clarity**, treating delight as secondary and frequency-gated.

### Cited Findings
- NN/g: animations are “less critical” when they are **time-filling visual stimulations**; surface-level delight **quickly sours**. Prefer usability roles: system clues, signifiers, spatial metaphors. — [NN/g: Animation Purpose in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Psychological basis cited by NN/g: animate motion captures attention (“It’s Alive!” study)—useful for feedback, dangerous for decoration. — Pratt et al. 2010 referenced in [NN/g Animation Purpose](https://www.nngroup.com/articles/animation-purpose-ux/)
- Asana case (NN/g qualitative): unicorn delight is memorable **because** it is sporadic and accompanied by an undo dialog that does real UX work; Trello’s lack of fanfare is acceptable for many users—delight is differentiator, not requirement. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Brand microinteractions succeed when tone matches brand (Apple Messages birthday balloons; Xbox power-on chime; Snapchat Bitmoji presence). Misaligned novelty (e.g., silly pull-to-refresh on a serious brand) is discouraged as opinionated brand guidance from NN/g. — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Scroll animation study: aesthetic intent (“modern brand”) can still produce **task friction**; aesthetic-usability effect helps only if motion is subtle and non-blocking. Leisure browsing tolerates more delight than medical/finance tasks. — [NN/g: Scroll Animations](https://www.nngroup.com/articles/scroll-animations/)
- Progress indicators study: feedback can make waits more tolerable (higher satisfaction, longer wait willingness)—this is **instrumental** “delight” (reduced anxiety), not ornamental. — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)
- Stripe (De Cock): after early excess, emphasis on **subtlety**; motion for state comprehension and perceived speed; “benevolent lying” with verification animation timed to real SMS latency expectations—craft case study on perception, not A/B delight metrics. — [Motionographer](https://motionographer.com/2015/07/06/user-interface-design-why-motion-matters/)
- Linear design posts emphasize calm hierarchy and reducing visual competition (“Don’t compete for attention you haven’t earned”) more than decorative micro-delight. — [Linear: Behind the latest design refresh](https://linear.app/now/behind-the-latest-design-refresh)
- Emil Kowalski (Linear marketing + product craft): Product Intelligence marketing animation is purposeful (explains feature); morphing feedback widget delight is OK **because rare**; daily tools should skip delight animations. — [You Don't Need Animations](https://emilkowal.ski/ui/you-dont-need-animations/)
- Smashing Magazine: distinguish **functional animation** (cognitive load, change blindness, spatial recall) from branding animation (emotion); balance by purpose + longevity (100th use test). Sponsored/opinionated but widely cited practitioner framework. — [Smashing: Functional Animation](https://www.smashingmagazine.com/2017/01/how-functional-animation-helps-improve-user-experience/); [Smashing: Animated Microinteractions in Mobile Apps](https://www.smashingmagazine.com/2016/08/experience-design-essentials-animated-microinteractions-in-mobile-apps/)

### Inferences
- **Decision rule for product teams:** If the interaction happens **>once per session for power users**, optimize for speed and clarity; reserve delight for **milestones** (first success, empty→value, rare celebrations) and always attach utilitarian feedback (undo, status).
- “Delight” with the best evidence base is often **anxiety reduction** (progress, confirmation), not cuteness.
- Design-engineering leaders (Stripe/Linear sphere) converge with NN/g: **restraint, custom easing, transform/opacity, sub-300–500ms**, reduced motion—despite different brand aesthetics.

### Gaps
- No public Stripe/Linear/Notion **controlled experiment** quantifying delight animations’ impact on retention/NPS was found.
- Aesthetic-usability effect is real but NN/g does not claim it outweighs task delays from decorative motion.
- Children’s sites tolerate more whimsy (NN/g notes), but that transfer poorly to B2B SaaS—avoid overgeneralizing.

---

## Appendix: Pattern → Frontend implementation priorities (synthesis)

| Pattern | High-ROI job | Evidence weight | Key implementation notes |
| --- | --- | --- | --- |
| Button press / pending / success | Acknowledge + prevent double action | Strong (response-time + progress research) | Instant pressed state; in-button spinner; disable after accept |
| Toggle | Instant preference change | Strong (NN/g heuristics + design systems) | Optimistic UI; pending if needed; revert on error; `role="switch"` |
| Like / favorite | Status + undo | Medium-strong (NN/g examples) | Local ≤300ms motion; undo; don’t loop animation |
| Form validation | Prevent rework / recover | Strong (ALA study, Baymard, NN/g, GOV.UK, WCAG) | Blur or submit; never empty-focus yell; field-adjacent text |
| Pull-to-refresh | System status | Medium (NN/g definition/examples) | Clear progress; brand only if on-tone |
| Loading / success | Uncertainty reduction | Strong (wait studies + thresholds) | 2–9s loop; ≥10s percent-done; skip spinner if <1s |
| Drag reorder | Preview + thresholds | Medium-strong (NN/g + craft) | Activation threshold; center-cross reshuffle; ~100ms settle |

**Primary source hub URLs:**  
[NN/g Microinteractions](https://www.nngroup.com/articles/microinteractions/) · [NN/g Animation Purpose](https://www.nngroup.com/articles/animation-purpose-ux/) · [NN/g Response Times](https://www.nngroup.com/articles/response-times-3-important-limits/) · [NN/g Progress Indicators](https://www.nngroup.com/articles/progress-indicators/) · [NN/g Toggles](https://www.nngroup.com/articles/toggle-switch-guidelines/) · [NN/g Form Errors](https://www.nngroup.com/articles/errors-forms-design-guidelines/) · [NN/g Scroll Animations](https://www.nngroup.com/articles/scroll-animations/) · [NN/g Drag-Drop](https://www.nngroup.com/articles/drag-drop/) · [A List Apart Inline Validation](https://alistapart.com/article/inline-validation-in-web-forms/) · [GOV.UK Validation](https://design-system.service.gov.uk/patterns/validation/) · [Stripe motion (De Cock)](https://motionographer.com/2015/07/06/user-interface-design-why-motion-matters/) · [Emil Kowalski](https://emilkowal.ski/ui/you-dont-need-animations/) · [WCAG 2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions)
