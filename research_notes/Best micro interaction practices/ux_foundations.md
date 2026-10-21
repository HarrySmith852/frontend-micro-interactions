# UX Foundations of Micro-Interactions

## How do Dan Saffer and other UX authorities define micro-interactions?

### Takeaway
Authoritative definitions converge on micro-interactions as **small, single-purpose product moments** structured as a trigger plus narrowly targeted feedback; Dan Saffer coined and popularized the term and the four-part model, while NN/g formalizes them as trigger–feedback pairs and IxDF restates Saffer’s framework for practitioners.

### Cited Findings
- Dan Saffer defines microinteractions as “the contained product moments that do one small task,” existing around and inside features in apps, websites, and appliances; examples include muting a phone, rating an app, or setting a status message — [Dan Saffer / Smart Design, “Microinteractions: Why details matter”](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- Saffer: features attract people to a product; details (microinteractions) keep them there; details are “a delivery system for emotions” and the “feel” part of “look and feel” — [Dan Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- When a microinteraction works especially well, it can become a **Signature Moment** elevated into the brand (examples cited: Facebook Like, Microsoft Start button, Google “I’m Feeling Lucky”) — [Dan Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- Primary book: Dan Saffer, *Microinteractions* (O’Reilly); O’Reilly lists publication as **May 2013**; NN/g cites the book as **2014** — [O’Reilly: Microinteractions](https://www.oreilly.com/library/view/microinteractions/9781449342760/); [NN/g: Microinteractions in User Experience (Oct 21, 2018)](https://www.nngroup.com/articles/microinteractions/)
- Book TOC and overview confirm structure: triggers, rules, feedback, modes, and loops; goal is to turn a product from one that is tolerated into one that is treasured — [O’Reilly: Microinteractions](https://www.oreilly.com/library/view/microinteractions/9781449342760/)
- Saffer (quoted via IxDF): “Microinteractions are an exercise in restraint, in doing as much as possible with as little as possible… ‘less is more’ should be the microinteraction designer’s mantra” — [IxDF: The Role of Micro-interactions in Modern UX](https://www.interaction-design.org/literature/article/micro-interactions-ux) (also [ixdf.org mirror](https://ixdf.org/literature/article/micro-interactions-ux))
- NN/g definition (Alita Kendrick, **Oct 21, 2018**): “Microinteractions are trigger-feedback pairs in which (1) the trigger can be a user action or an alteration in the system’s state; (2) the feedback is a narrowly targeted response to the trigger and is communicated through small, highly contextual (usually visual) changes in the user interface.” — [NN/g: Microinteractions in User Experience](https://www.nngroup.com/articles/microinteractions/)
- NN/g: microinteractions provide feedback (often system status or error prevention) and can also serve as a vehicle for branding — [NN/g: Microinteractions in User Experience](https://www.nngroup.com/articles/microinteractions/)
- NN/g boundary conditions: static always-on UI elements are **not** microinteractions (no distinct trigger); multi-step flows/features are **not** microinteractions (e.g., a full video player is a feature; its volume control can be a microinteraction); a button with **no** feedback is not a microinteraction — [NN/g: Microinteractions in User Experience](https://www.nngroup.com/articles/microinteractions/)
- IxDF: a micro-interaction is a small, task-based interaction that provides feedback or visual responses and guides users with subtle cues; designers use single-purpose animations to make products more intuitive, engaging, and efficient — [IxDF: The Role of Micro-interactions in Modern UX](https://www.interaction-design.org/literature/article/micro-interactions-ux)
- IxDF distinguishes **micro-interactions** (task guidance + feedback; often user-triggered) from **micro-animations** (visual polish/attention; may auto-play without direct task feedback) — [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux)
- Adobe XD Essentials (Apr 19, 2016), summarizing Saffer: atomic design moments typically accomplish an individual task; communicate status/feedback; prevent human error; enhance sense of direct manipulation; help users visualize results of actions — [Adobe Blog: Microinteractions and Their Macro Effect on UX](https://blog.adobe.com/en/publish/2016/04/19/microinteractions-and-their-macro-effect-on-user-experience-part-1)
- Historical talk framing (IxDA, Apr 3, 2013): Saffer presented microinteractions as the details that turn tolerated products into beloved ones, covering Triggers, Rules, Feedback, and Loops — [IxDA: Microinteractions: Designing with Details](https://ixda.org/video/microinteractions-designing-with-details/)

### Inferences
- “Microinteraction” is primarily a **Saffer-originated design concept** (book ~2013–2014), later operationalized by NN/g as a crisp trigger–feedback definition useful for critique and inventorying UI moments.
- Definitions emphasize **scope** (one small task / one trigger–feedback pair) more than aesthetic animation; animation is a common feedback channel, not the definition itself.
- Brand/signature moments are optional elevations of otherwise utilitarian microinteractions, not a requirement of the category.

### Gaps
- Full verbatim page-level excerpts from the print/ebook of *Microinteractions* were not retrieved (paywalled); definitions above rely on Saffer’s public Smart Design essay, O’Reilly catalog/overview, and secondary restatements by NN/g, IxDF, and Adobe.
- Exact first-coinage date of the term “microinteraction” beyond “Saffer / book era” was not independently verified from a primary glossary entry outside the book and surrounding talks.

---

## What are the four parts of a micro-interaction and common examples?

### Takeaway
Saffer’s classic model is **Trigger → Rules → Feedback → Loops/Modes**; NN/g collapses the teaching model into **trigger + feedback** for critique, while still citing Saffer’s fuller structure. Common examples span user-initiated (like, toggle, pull-to-refresh) and system-initiated (notifications, alarms) moments.

### Cited Findings

#### The four parts (Saffer)
- Microinteractions have four parts: **Trigger, Rules, Feedback, and Loops/Modes** — [Dan Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); restated by [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux); [Adobe XD Essentials (2016)](https://blog.adobe.com/en/publish/2016/04/19/microinteractions-and-their-macro-effect-on-user-experience-part-1); book chapters map 1:1 to these parts — [O’Reilly TOC](https://www.oreilly.com/library/view/microinteractions/9781449342760/)

| Part | Role (sourced) | Source |
| --- | --- | --- |
| **Trigger** | Starts the microinteraction; **manual/user** (click, icon, gesture, voice) or **system** (conditions met, e.g., text arrives → vibrate) | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux); [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| **Rules** | Invisible logic: sequence of events; what can/cannot be done | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux) |
| **Feedback** | Makes rules visible; visual, audio, haptic, motion, messages; absence of feedback also communicates | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux); Feedback chapter methods listed in [O’Reilly TOC](https://www.oreilly.com/library/view/microinteractions/9781449342760/) |
| **Loops & Modes** | Meta-rules: **Loops** = duration, repetition, change over time; **Modes** = infrequent critical configuration that would otherwise disrupt flow (e.g., pick city for weather) | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux) |

- Modes should be used sparingly—only for critical but infrequent actions — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- Loops can be **long loops**: adapt behavior on 2nd, 10th, or 1,000th return (e.g., onboarding shown only to first-time users) — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/); [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux)
- Book chapter topics under Rules include constraints, don’t start from zero, smart defaults, preventing errors, microcopy — [O’Reilly TOC](https://www.oreilly.com/library/view/microinteractions/9781449342760/)
- Book chapter topics under Loops/Modes include spring-loaded and one-off modes, styles of loops, long loops, progressive disclosure or reduction — [O’Reilly TOC](https://www.oreilly.com/library/view/microinteractions/9781449342760/)

#### NN/g operational framing
- User-initiated triggers: GUI command, gesture, or voice; system-initiated: predetermined conditions met; for GUI triggers, visual feedback is usually placed **near** the trigger — [NN/g: Microinteractions (2018)](https://www.nngroup.com/articles/microinteractions/)

#### Common examples (yes / no / depends)

| Example | Microinteraction? | Why | Source |
| --- | --- | --- | --- |
| Scrollbar | Yes | User-triggered; visual feedback of location in page | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Digital alarm | Yes | System-triggered; auditory (+ visual) when time condition met | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Button | Depends | No feedback on click → not a microinteraction | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Pull-to-refresh animation | Yes | User-triggered; visual feedback of action | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| GIFs (decorative) | No | Not triggered by system or user as a task pair | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Swipe animation | Yes (per table) | User-triggered visual feedback of swipe | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Email notification | Yes | System-triggered status feedback | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Full video player | No (feature) | Volume control *within* player can be a microinteraction | [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Like animation / heart | Yes | Confirms success of like | [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux); [NN/g Asana/Gap examples](https://www.nngroup.com/articles/microinteractions/) |
| Autocomplete as typing | Yes | Real-time feedback guiding input | [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux) |
| Upload progress bar | Yes | Status information during process | [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux) |
| “Typing…” in chat | Yes | System status of partner | [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux); Snapchat Bitmoji example in [NN/g](https://www.nngroup.com/articles/microinteractions/) |
| Mute phone / set status | Yes | Classic Saffer “one small task” moments | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/) |
| iPhone silent-switch vibrate | Yes | Haptic feedback confirming mode | [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux) |
| Password requirement checklist updating live | Yes | Error-prevention feedback | [NN/g eBay example](https://www.nngroup.com/articles/microinteractions/); [IxDF Mailchimp example](https://www.interaction-design.org/literature/article/micro-interactions-ux) |

### Inferences
- Practitioners should inventory microinteractions at the **moment** level (trigger + outcome), not at the feature level.
- Feedback channels are multimodal; Visual is default on screens, but audio/haptics are first-class in Saffer and platform guidelines.
- Loops/modes are where product maturity and personalization live (first visit vs. thousandth visit), which SEO blogs often omit when they reduce the model to “cute animation.”

### Gaps
- Detailed primary text for Saffer’s subtypes of loops (beyond TOC headings and secondary summaries) was not available without the full book.
- No authoritative quantitative catalog of “most common” microinteractions across industry—examples above are illustrative from NN/g, IxDF, and Saffer, not ranked by frequency.

---

## What benefits do they provide (feedback, perceived performance, delight, error prevention)?

### Takeaway
Authoritative literature ties microinteractions primarily to **visibility of system status**, **error prevention/undo**, **engagement/brand**, and **perceived performance** (via timely feedback and progress indicators). Delight is acknowledged but NN/g warns that motion used mainly for entertainment often fails usability tests; Material and Apple treat character/delight as secondary to clarity and restraint.

### Cited Findings

#### Feedback & visibility of system status
- NN/g: any display of system status is a microinteraction because it includes a trigger (user action or system-state change) and feedback — [NN/g: Microinteractions (2018)](https://www.nngroup.com/articles/microinteractions/)
- Heuristic #1 (Jakob Nielsen): systems should keep users informed about what is going on through appropriate feedback within reasonable time — [NN/g: Visibility of System Status (Aurora Harley, Jun 3, 2018)](https://www.nngroup.com/articles/visibility-system-status/)
- Appropriate feedback for a user action is “perhaps the most basic guideline of user-interface design”; without it users may re-tap buttons or lose trust — [NN/g: Visibility of System Status](https://www.nngroup.com/articles/visibility-system-status/); also [NN/g: 10 Heuristics Applied to Complex Applications](https://www.nngroup.com/articles/usability-heuristics-complex-applications/)
- Progress indicators (a microinteraction subcategory) show the system is still working and encourage continued commitment while waiting — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- “Standby” microinteractions signal the system is waiting for further input (e.g., iOS app icons shaking; Google Home listening animation) — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- IxDF lists showcasing system status as a primary role (e.g., download progress bar) — [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux)

#### Perceived performance & response-time psychology
- Classic response-time limits (Nielsen, from *Usability Engineering* 1993, still cited): **0.1 s** ≈ instantaneous / direct manipulation (no special feedback beyond showing the result); **1.0 s** ≈ thought flow stays uninterrupted (delay noticed; feeling of direct manipulation weakens); **10 s** ≈ limit for keeping attention on the dialogue—beyond that, users need feedback about when the system will finish — [NN/g: Response Times: The 3 Important Limits](https://www.nngroup.com/articles/response-times-3-important-limits/); [NN/g: Website Response Times](https://www.nngroup.com/articles/website-response-times/)
- Progress indicators reassure that the system is working, give something to look at, provide a reason to wait, and can **reduce perceived wait time** by diverting cognitive resources — [NN/g: Progress Indicators (Katie Sherwin, Oct 26, 2014)](https://www.nngroup.com/articles/progress-indicators/)
- Cited study (University of Nebraska–Lincoln / Nah 2004 summarized by NN/g): users shown a continuous progress bar reported higher satisfaction and were willing to wait on average **~3× longer** than those with no indicator — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)
- Guidelines: always give **immediate** feedback when an action starts; use a progress indicator for actions taking longer than about **1.0 second**; looped/spinner feedback for roughly **2–10 seconds**; **percent-done** for **≥10 seconds**; avoid static “Loading…” alone; don’t rely on “don’t click again” warnings—show that the first click was accepted — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)
- Material Design: motion can distract from backend work (fetching/loading), reducing **perceived latency** when transitions guide focus and loading happens behind the scenes — [Material Design (M1): Material motion](https://m1.material.io/motion/material-motion.html)
- IxDF: attention to micro-interaction detail “improves the product's perceived performance” — [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux)

#### Error prevention
- NN/g links microinteractions to Heuristic: error prevention—confirmations, undo, and avoiding error-prone situations — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Examples: Asana complete → dialog with undo; Gap heart toggle with short pump animation to make accidental favorite noticeable; eBay live password-requirement checklist preventing rework on submit — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Saffer principle: “Prevent human error. Don’t allow (or better yet, fix) actions that would break the microinteraction.” — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- IxDF: micro-interactions facilitate seamless interaction and prevent errors (e.g., live password checks) — [IxDF](https://www.interaction-design.org/literature/article/micro-interactions-ux)
- Immediate feedback helps users identify and fix errors as soon as they are made; tied to direct manipulation — [NN/g: Visibility of System Status](https://www.nngroup.com/articles/visibility-system-status/)

#### Delight, engagement, and brand
- Saffer: difference between products we love vs. tolerate is often the microinteractions; well-designed ones can increase adoption and loyalty by making dull/difficult moments enjoyable — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- NN/g: microinteractions improve UX by encouraging engagement, displaying system status, providing error prevention, and communicating brand; they differentiate similar products — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- NN/g Asana unicorn: utilitarian undo dialog + occasional celebratory animation as dual microinteractions; brand tone matters (fun brand ≠ professional brand using a donut pull-to-refresh) — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Brand examples: Apple Messages birthday balloons; Snapchat Bitmoji presence; Xbox power-on melody as signature audio brand — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Material Design lists “Character, polish, and delight” among motion benefits—alongside focus, gesture hints, hierarchy, and masking loading — [Material Design (M1): Material motion](https://m1.material.io/motion/material-motion.html)
- Caution (NN/g animation, Page Laubheimer, **Jan 12, 2020**): motion is most appropriate as **subtle feedback for microinteractions**, rather than to induce delight or entertain; “surface-level delight… quickly sours”; downtime/transition entertainment animations often frustrate usability-test participants — [NN/g: The Role of Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Animation helps overcome **change blindness** (e.g., cart badge updates far from the click target) so feedback is noticed without heavier UI chrome — [NN/g: Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Animation also communicates state/mode changes, spatial/navigation metaphors, and signifiers for gestures; overuse becomes attention hijacking / dark patterns (e.g., flashing countdown timers) — [NN/g: Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)

#### Trust
- Communicating status creates predictability and trust in both the interface and the brand; consequential actions should not occur without informing users — [NN/g: Visibility of System Status](https://www.nngroup.com/articles/visibility-system-status/)

### Inferences
- Benefits stack: **functional** (status, errors, performance perception) first; **emotional/brand** second and only when aligned with product personality.
- “Perceived performance” in this literature is mostly **feedback timing + progress communication**, not marketing claims about delight making apps “feel faster” without evidence.
- NN/g and platform HIGs are more skeptical of delight-for-its-own-sake than many commercial design blogs.

### Gaps
- Direct experimental citations quantifying “delight → retention” specifically for microinteractions (beyond Asana anecdote and general progress-bar wait study) were sparse in the primary org sources reviewed.
- Full Apple HIG “Motion” page content did not render via automated fetch of [developer.apple.com HIG Motion](https://developer.apple.com/design/human-interface-guidelines/motion); guidance below under do’s/don’ts uses a documented HIG mirror plus Apple accessibility docs.

---

## What are commonly cited do's and don'ts?

### Takeaway
Across Saffer, NN/g, IxDF, Material Design, and Apple HIG, consensus is: **purpose over decoration**, **immediate subtle feedback**, **short durations**, **consistency**, **error prevention**, and **accessibility (reduce motion / multimodal feedback)**—avoid gratuitous, slow, frequent, or attention-hijacking motion.

### Cited Findings

#### Do’s — Dan Saffer (design principles for details)
- **Don’t start from zero** — use known user/platform/context data — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- **Bring the data forward** — surface useful internal data in the manual trigger — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- **Prevent human error** — disallow or auto-fix breaking actions — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- **Use the overlooked** — convey feedback via existing chrome (cursor, scrollbar, dial, button state) instead of adding UI — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- **Speak human** — match audience language; prefer simple direct copy otherwise — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- **Long loops** — adapt over repeat use (2nd / 10th / 1,000th visit) — [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/)
- Book feedback chapter themes (TOC): feedback illuminates rules; feedback is for humans; **less is more**; feedback as personality delivery; methods include visual, animation, messages, audio, earcons, speech, haptics — [O’Reilly TOC](https://www.oreilly.com/library/view/microinteractions/9781449342760/)
- Restraint mantra: do as much as possible with as little as possible — [IxDF quoting Saffer](https://www.interaction-design.org/literature/article/micro-interactions-ux)

#### Do’s — NN/g (microinteractions + animation + progress)
- Serve a purpose: system status, error prevention, brand—microinteractions “shouldn’t be fluffy” but may still embody brand tone — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Place visual feedback near the GUI trigger — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Prefer **subtle, brief, unobtrusive** animation for feedback, state change, navigation metaphors, and signifiers — [NN/g: Animation and Motion in UX (2020)](https://www.nngroup.com/articles/animation-purpose-ux/)
- Use animation to make feedback noticeable when static changes suffer change blindness — [NN/g: Animation and Motion in UX](https://www.nngroup.com/articles/animation-purpose-ux/)
- Support undo and prevent rework with clear state feedback (e.g., favorites toggle; live field validation) — [NN/g: Microinteractions](https://www.nngroup.com/articles/microinteractions/)
- Immediate feedback on action start; progress feedback for >~1s waits; percent-done for ≥~10s; allow cancel on longer processes — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/); [NN/g: Response Times](https://www.nngroup.com/articles/response-times-3-important-limits/)
- For percent-done bars: prefer starting slower then speeding up so you don’t overpromise; give approximate time estimates with buffer — [NN/g: Progress Indicators](https://www.nngroup.com/articles/progress-indicators/)

#### Do’s — IxDF best practices
1. Understand user needs / purpose before inventing details  
2. Give **immediate** feedback  
3. Focus on **simplicity**  
4. Maintain **consistency** across similar actions  
5. Humanize interactions (emotionally appropriate, on-brand)  
— [IxDF: The Role of Micro-interactions in Modern UX](https://www.interaction-design.org/literature/article/micro-interactions-ux)

#### Do’s / Don’ts — Material Design motion (M1 guidance still widely cited)
- Motion should be **responsive** (react at the touch point), **natural** (easing, real-world forces), **aware** (choreography with surroundings), **intentional** (guide focus) — [Material motion](https://m1.material.io/motion/material-motion.html)
- Duration guidance: larger mobile animations **300–400 ms**; smaller **150–200 ms**; longer/shorter can feel sluggish or hard to follow — [Material motion](https://m1.material.io/motion/material-motion.html)
- **Do** animate quickly so users never wait for animation to finish; **Don’t** stagger/slow many elements unnecessarily — [Material motion](https://m1.material.io/motion/material-motion.html)
- **Do** keep transitions clear/simple/cohesive; **Don’t** send many items in conflicting directions — [Material motion](https://m1.material.io/motion/material-motion.html)
- Ink ripples / immediate response confirm input at the point of touch — [Material motion](https://m1.material.io/motion/material-motion.html)
- Gestures: user’s touch should **directly control** movement; animation velocity should match gesture velocity—don’t fire a canned animation that misrepresents speed — [Material Design: Gestures](https://m2.material.io/design/interaction/gestures.html)
- Objects leaving screen may use shorter durations; longer travel / larger surface changes may need longer durations — [Material Design: Duration & easing](https://m1.material.io/motion/duration-easing.html)

#### Do’s / Don’ts — Apple Human Interface Guidelines (Motion)
- Official entry point: [Apple HIG — Motion](https://developer.apple.com/design/human-interface-guidelines/motion) (live page is JS-rendered; content below from documented HIG mirror reflecting current guidance, including changelog through **Sep 9, 2025**) — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Do** add motion purposefully to support the experience; **Don’t** add motion for its own sake—gratuitous animation distracts and can cause discomfort — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Do** make motion optional; never use motion as the **only** channel for important information—supplement with haptics/audio — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Do** keep feedback motion realistic and consistent with gesture direction/expectations — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Do** aim for **brevity and precision**; brief precise feedback often communicates better than prominent animation — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Don’t** add custom motion to **frequent** UI interactions (system already animates standards; extra motion becomes tax) — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- **Do** let people **cancel**/interrupt motion; don’t force waiting for animations to finish, especially if repeated — [HIG Motion mirror](https://appguidelines.com/human-interface-guidelines/version/22/motion/)
- Accessibility: respect **Reduce Motion**; avoid large animations especially those simulating 3D when preference is on — [Apple: accessibilityReduceMotion](https://developer.apple.com/documentation/swiftui/environmentvalues/accessibilityreducemotion); evaluation criteria for depth simulation, multi-axis/spinning motion, auto-advancing carousels — [App Store Connect: Reduced Motion evaluation criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/)
- If motion conveys meaning (status change, hierarchy), don’t remove it entirely under Reduce Motion—replace with dissolve/fade/color shift — [Reduced Motion evaluation criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/)

#### Explicit don’ts (cross-source)
| Don’t | Source |
| --- | --- |
| Use animation mainly to entertain or “delight” during downtime | [NN/g Animation (2020)](https://www.nngroup.com/articles/animation-purpose-ux/) |
| Overuse motion competing for attention (many simultaneous animations dilute each) | [NN/g Animation — Hipmunk example](https://www.nngroup.com/articles/animation-purpose-ux/) |
| Use flashing/aggressive motion as dark-pattern attention hijacking | [NN/g Animation](https://www.nngroup.com/articles/animation-purpose-ux/) |
| Treat decorative GIFs / always-on static chrome as microinteractions | [NN/g Microinteractions](https://www.nngroup.com/articles/microinteractions/) |
| Use looped spinners for long (>~10s) waits; use static “Please wait” only; threaten “don’t click again” | [NN/g Progress Indicators](https://www.nngroup.com/articles/progress-indicators/) |
| Make users wait for animations; mis-match gesture velocity | [Material motion](https://m1.material.io/motion/material-motion.html); [Material Gestures](https://m2.material.io/design/interaction/gestures.html); [Apple HIG Motion](https://appguidelines.com/human-interface-guidelines/version/22/motion/) |
| Rely on motion alone for critical information; ignore Reduce Motion | [Apple HIG Motion](https://appguidelines.com/human-interface-guidelines/version/22/motion/); [Reduced Motion criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria/) |
| Over-mode: modes only for critical infrequent configuration | [Saffer / Smart Design](https://smartdesignworldwide.com/ideas/microinteractions-details-matter/) |
| Off-brand “fun” microinteractions on serious products | [NN/g Microinteractions](https://www.nngroup.com/articles/microinteractions/) |

### Inferences
- The durable best-practice set is closer to **usability heuristics + motion restraint** than to “add more micro-animations.”
- Platform guidelines (Material durations; Apple cancelability / Reduce Motion) supply implementable constraints that complement Saffer’s conceptual model.
- Consistency and proximity of feedback are as important as the aesthetic quality of the animation.

### Gaps
- Material Design 3 live overview ([m3.material.io/styles/motion/overview](https://m3.material.io/styles/motion/overview)) did not return readable body text via automated fetch; duration/character guidance above uses Material Design 1/2 published motion docs, which remain the most citable public Material motion pages.
- Official Apple HIG Motion HTML did not return body text via automated fetch; notes rely on a structured HIG mirror plus Apple accessibility documentation—recommend verifying against the live HIG before implementation sign-off.
- Few primary sources publish a single numbered “10 commandments of microinteractions” list; do’s/don’ts above are synthesized from overlapping authoritative recommendations, not one canonical checklist.

---

## Source index (primary / reputable)

| Source | Date (when known) | URL |
| --- | --- | --- |
| Dan Saffer, *Microinteractions* (O’Reilly) | May 2013 (O’Reilly); often cited 2014 | https://www.oreilly.com/library/view/microinteractions/9781449342760/ |
| Dan Saffer / Smart Design essay | undated page (post-book) | https://smartdesignworldwide.com/ideas/microinteractions-details-matter/ |
| NN/g — Microinteractions in UX (Kendrick) | Oct 21, 2018 | https://www.nngroup.com/articles/microinteractions/ |
| NN/g — Animation and Motion in UX (Laubheimer) | Jan 12, 2020 | https://www.nngroup.com/articles/animation-purpose-ux/ |
| NN/g — Visibility of System Status (Harley) | Jun 3, 2018 | https://www.nngroup.com/articles/visibility-system-status/ |
| NN/g — Progress Indicators (Sherwin) | Oct 26, 2014 | https://www.nngroup.com/articles/progress-indicators/ |
| NN/g — Response Times: 3 Important Limits (Nielsen) | enduring guidelines from 1993 book / updated article | https://www.nngroup.com/articles/response-times-3-important-limits/ |
| IxDF — Role of Micro-interactions in Modern UX (Soegaard) | ~2025 (“10 months ago” at fetch) | https://www.interaction-design.org/literature/article/micro-interactions-ux |
| Material Design — Material motion (M1) | Material Design 1 era docs | https://m1.material.io/motion/material-motion.html |
| Material Design — Duration & easing | M1 | https://m1.material.io/motion/duration-easing.html |
| Material Design — Gestures | M2 | https://m2.material.io/design/interaction/gestures.html |
| Apple HIG — Motion | live; mirror changelog to Sep 9, 2025 | https://developer.apple.com/design/human-interface-guidelines/motion |
| Apple — Reduce Motion (SwiftUI) | current docs | https://developer.apple.com/documentation/swiftui/environmentvalues/accessibilityreducemotion |
| Adobe XD Essentials (secondary summary of Saffer) | Apr 19, 2016 | https://blog.adobe.com/en/publish/2016/04/19/microinteractions-and-their-macro-effect-on-user-experience-part-1 |
| IxDA talk listing (Saffer) | Apr 3, 2013 | https://ixda.org/video/microinteractions-designing-with-details/ |
