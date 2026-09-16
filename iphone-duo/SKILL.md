---
name: iphone-duo
description: Design and build app UI for iPhone Duo, the folding iPhone with an outer and an inner display joined by a center hinge. Use when the task involves iPhone Duo, a foldable iPhone, dual displays, the hinge or folding region, the vertical bar placement, asymmetric safe areas, size-class changes on unfold, or adapting an existing iOS screen to open and close. Covers device states and sizes, safe areas, hinge avoidance, column grids, navigation placement, per-app-type adaptive patterns, and a do/don't rule set.
---

# iPhone Duo

iPhone Duo has a compact **outer display** and a larger **inner display** joined by a center hinge. The same app moves between them in seconds, often mid-task. You are designing **one app that adapts**, never two unrelated screens.

Everything here comes from Apple's public iPhone Duo guidance (September 2026) plus one community kit's derived values. **Every number carries a confidence badge** and you must repeat the badge when you quote a number:

| Badge | Meaning |
|---|---|
| `OFFICIAL` | Stated by Apple in the HIG, Tech Talks or Tech Specs |
| `DERIVED` | Calculated from an official number (e.g. pt from px at 3x) |
| `RECOMMENDED` | A design value chosen because Apple has not published one |
| `ILLUSTRATIVE` | Drawn for clarity, not for measurement |
| `ASSUMPTION` | Believed true from context, unconfirmed |

Anything not `OFFICIAL` is a starting point to verify in the Xcode 27.1 simulator and on device. Never present a `DERIVED` or `RECOMMENDED` value to a user as an Apple specification.

## The five things that decide every layout

1. **Design for size classes and reserved regions, not for poses.** People fold, prop and stand the device in many ways. Apple asks you to respond to the size class and to the regions the system reports, never to enumerate physical postures.
2. **Bars go to the side, and you leave them there.** On the outer display and on inner landscape, navigation, the prominent action, toolbar groups and the tab bar are laid out vertically along one edge. That placement is the core iPhone Duo pattern. Moving them back to the top and bottom wastes vertical space and breaks what people learn everywhere else.
3. **Task continuity is the whole point.** When the device opens or closes, keep the same screen, the same selection and the same scroll position. Adding a level of hierarchy is fine. Rebuilding the interface is not.
4. **The extra inner area is for secondary context, not for bigger elements.** Show the next level of hierarchy or supporting detail beside the primary task. Scaling every element up adds no information and pushes content below the fold.
5. **Read every safe-area inset on its own.** Insets on iPhone Duo are asymmetric, because the vertical bar sits along one edge only. `left == right` is never a safe assumption here.

## Route to the right reference

| You are doing | Read |
|---|---|
| Picking a device state, sizes, size classes, poses, camera and folding regions | [references/anatomy.md](references/anatomy.md) |
| Safe areas, hinge avoidance, margins, max text width, column grids | [references/layout.md](references/layout.md) |
| Where nav bars, tab bars, sidebars, toolbars, sheets and menus go | [references/navigation.md](references/navigation.md) |
| Adapting a feed, list-detail, chat, media, map, shop, dashboard, settings or calendar | [references/patterns.md](references/patterns.md) |
| Reviewing a design or a diff against the rules | [references/rules.md](references/rules.md) |

## Workflow

1. **Choose the state people will use most for this task.** The outer display is usually the first touch, so design it first and treat inner as the expansion.
2. **Lay out inside the guides.** Start from the safe area and the layout margins for that state, not from fixed offsets.
3. **Apply your product UI.** Keep the vertical bar, the bars and the panes where the system puts them; replace only the content.
4. **Build the matching opposite state next to it.** Check that the task, the selection and the scroll position carry over.
5. **Validate.** Nothing important on the hinge, nothing under the vertical bar, at most one extra level of hierarchy, every inset handled separately, and a dark-mode pass.

## Constants worth knowing before you open a reference

- Control size: **44 x 44 pt** default, **28 x 28 pt** minimum. `OFFICIAL`
- Vertical bar width: **94 pt**. `RECOMMENDED` (Apple says the bar has a fixed width but has not published the value)
- Hinge avoidance band: **27 pt centered on the fold**. `RECOMMENDED`
- Max width for a text column: **680 pt**. `RECOMMENDED`
- Logical sizes assume a **3x** scale factor. `ASSUMPTION`

## When you cannot confirm something

Say so. Apple had not published every iPhone Duo specification as of September 2026. If a value you need is not in these references, state that it is unpublished, give the nearest official anchor, and recommend measuring it in the simulator. Do not invent a number and do not present a community value as Apple's.
