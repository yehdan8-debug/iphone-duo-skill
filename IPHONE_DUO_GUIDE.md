# iPhone Duo UI Guide

A single-file instruction document for designing and building app UI for iPhone Duo, the folding iPhone. This is the same content as the `iphone-duo` skill, merged for reading end to end.

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
| Picking a device state, sizes, size classes, poses, camera and folding regions | [#anatomy](#anatomy) |
| Safe areas, hinge avoidance, margins, max text width, column grids | [#layout](#layout) |
| Where nav bars, tab bars, sidebars, toolbars, sheets and menus go | [#navigation](#navigation) |
| Adapting a feed, list-detail, chat, media, map, shop, dashboard, settings or calendar | [#patterns](#patterns) |
| Reviewing a design or a diff against the rules | [#rules](#rules) |

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

---

# Device anatomy

Two displays, one hinge, and a set of regions your layout has to respect.

## The six configurations

These six states cover every documented way to hold iPhone Duo. Standing the device on its edges reuses the same sizes and rules, so it needs no layout of its own.

### Outer Portrait (device closed, held upright)

| Property | Value | Badge |
|---|---|---|
| Logical size | 466 x 678 pt | `DERIVED` |
| Resolution | 1398 x 2034 px | `OFFICIAL` |
| Width size class | Compact | `OFFICIAL` |
| Bars | Vertical, on the side | `OFFICIAL` |
| Hinge | Not on this display | `OFFICIAL` |

### Outer Landscape (device closed, turned sideways)

| Property | Value | Badge |
|---|---|---|
| Logical size | 678 x 466 pt | `DERIVED` |
| Resolution | 2034 x 1398 px | `OFFICIAL` |
| Width size class | Compact | `OFFICIAL` |
| Bars | Vertical, overflow sooner | `OFFICIAL` |
| Vertical bar side | Follows the camera edge | `ASSUMPTION` |

### Inner Portrait (device fully open, held upright)

| Property | Value | Badge |
|---|---|---|
| Logical size | 669 x 951 pt | `DERIVED` |
| Resolution | 1878 x 2670 px | `OFFICIAL` |
| Size classes | Regular + Regular | `OFFICIAL` |
| Bars | Horizontal, top and bottom | `OFFICIAL` |
| Hinge line | Horizontal at 475.5 pt | `DERIVED` |

### Inner Landscape (device fully open, the natural open posture)

| Property | Value | Badge |
|---|---|---|
| Logical size | 951 x 669 pt | `DERIVED` |
| Resolution | 2670 x 1878 px | `OFFICIAL` |
| Size classes | Regular + Regular | `OFFICIAL` |
| Bars | Vertical, on the side | `OFFICIAL` |
| Division region | Inactive, zero width | `OFFICIAL` |

### Partial Book (inner display, partially folded like a book)

| Property | Value | Badge |
|---|---|---|
| Logical size | 951 x 669 pt | `DERIVED` |
| Division region | Active, splits the display | `OFFICIAL` |
| System components | Move away from the fold | `OFFICIAL` |
| Split views | Columns adapt to the fold | `OFFICIAL` |
| Avoidance band | 27 pt centered | `RECOMMENDED` |

### Partial Tabletop (inner display, propped on a surface)

| Property | Value | Badge |
|---|---|---|
| Logical size | 669 x 951 pt | `DERIVED` |
| Top region | Content viewed at a distance | `OFFICIAL` |
| Bottom region | Interactive controls | `OFFICIAL` |
| Overlay arrangement | Moves to each side of the fold | `OFFICIAL` |
| Avoidance band | 27 pt centered | `RECOMMENDED` |

## Outer display

Used when the device is closed. It is wider and shorter than other iPhone displays, so the system moves the status bar and puts bars to the side to keep vertical space for content.

- **Outer camera:** always present, a round cutout in the top corner. `OFFICIAL`
- **Vertical controls:** back, prominent action, toolbar groups, tab bar, ordered top to bottom. `OFFICIAL`
- **Vertical bar:** 94 pt wide. Apple says bars have a fixed width but gives no value. `RECOMMENDED`
- **Safe area:** recommended insets of 8 pt top and bottom, 94 pt trailing. `RECOMMENDED`
- **Content region:** keep your layout inside the safe area and the layout margins.

## Inner display

Used when the device is open. Regular width and height leave room for sidebars and two panes.

- **Leading pane:** list, sidebar or primary view.
- **Trailing pane:** detail or secondary view.
- **Inner camera:** hidden until active. When it activates, the UI moves aside. Treat any drawn position as illustrative.
- **Folding region:** zero width when flat. When partially open it divides the display and excludes the center.
- **Vertical bar:** stays on the side in landscape. Horizontal bars return only in portrait. `OFFICIAL`

## Poses

People fold, prop and stand the device. Apple asks you to design for **size classes**, not for each pose, and to let reserved regions shape the layout.

| Pose | What it means | Badge |
|---|---|---|
| Flat | Division region has zero width and is inactive. Treat the display as one surface. | `OFFICIAL` |
| Folded like a book | The hinge divides the inner display into two usable regions. Content that spans the fold is harder to see. | `OFFICIAL` |
| Propped on a surface | Top region for content viewed at a distance, bottom region for controls. | `OFFICIAL` |
| Standing on its edges | Listed by Apple as a way to position the device. Same size classes, so the same layouts apply. | `OFFICIAL` |

## Reserved regions

Areas system content avoids, or that components adapt around. Many system components handle them for you. Custom layouts must query them.

| Region | Behavior | Badge |
|---|---|---|
| Outer camera | Always present, a round cutout in the top corner. Side controls are arranged around it by the system. | `OFFICIAL` |
| Inner camera | Present only while the camera is active. The interface moves aside to clear it. | `OFFICIAL` |
| Folding region | Present only when the device is partially open. Divides the inner display and excludes the center. | `OFFICIAL` |

Apple has not published exact reserved-region info in the HIG text. Drawn positions for the two cameras are illustrative, and screen corner radii are illustrative too.

---

# Layout guides

Where content can go in each device state.

## Safe areas

A safe area is the part of the screen not covered by hardware or system UI. On iPhone Duo it is asymmetric, because the status bar, bars and vertical bar all sit along one edge.

Three rules:

1. **Read every inset on its own. Never assume left equals right.**
2. **Let backgrounds and images run to the screen edges.** Keep text and controls inside the safe area.
3. **In Split View multitasking each pane carries its own insets on its outer edge,** so the opposite edge can carry an inset you did not expect.

| Inset | Value | Badge |
|---|---|---|
| Outer, top and bottom | 8 pt | `RECOMMENDED` |
| Outer, trailing | 94 pt (vertical bar) | `RECOMMENDED` |
| Inner portrait, top | 88 pt (status bar plus nav bar) | `RECOMMENDED` |
| Inner portrait, bottom | 20 pt | `RECOMMENDED` |
| Inner landscape, trailing | 94 pt | `RECOMMENDED` |
| Leading inset, all states | 0 pt | `ILLUSTRATIVE` |

Apple publishes no iPhone Duo safe-area numbers in Design Resources. These are measured from HIG imagery. Always read the live insets from the system rather than hardcoding these.

## Hinge area

The hinge runs through the center of the inner display and, at 475.5 pt from the edge in both orientations, is the line that divides it. When flat it takes no space. When partially folded it becomes a divider that splits the screen.

| Property | Value | Badge |
|---|---|---|
| Hinge position | 475.5 pt from the edge | `DERIVED` |
| Division width when flat | 0 pt | `OFFICIAL` |
| Division width when folded | Not published | `RECOMMENDED` |
| Avoidance band | 27 pt centered on the fold | `RECOMMENDED` |

Rules:

- **Keep buttons, sliders and small targets out of the band.**
- **Prefer layouts that adapt on their own.** Split views and arrangement views resize panes to either side for you.
- **Scrolling content such as feeds and articles may pass the fold. Controls may not.**
- **Avoid extreme repositioning.** Move only what is needed to stay visible and easy to tap.

## Margins and content width

Margins keep content off the screen edges. A maximum content width keeps long text readable when the display grows, so lines do not simply get longer.

| Property | Value | Badge |
|---|---|---|
| Content margin, outer display | 16 pt | `RECOMMENDED` |
| Content margin, inner display | 20 pt | `RECOMMENDED` |
| Gap between panes, outer | 16 pt | `RECOMMENDED` |
| Gap between panes, inner | 20 pt | `RECOMMENDED` |
| Max width for text | 680 pt | `RECOMMENDED` |

- **Use layout margins instead of fixed offsets** so content adapts as the display changes.
- **Give long text a comfortable measure and spend the remaining width on a second pane, not on longer lines.**
- **Keep controls in the pane they belong to,** for example the buttons above a list.

## Columns

Column overlays for each state. Apple recommends an **even** number of columns so content divides cleanly at the fold. Column counts, margins and gaps below are kit values, not Apple specifications.

| State | Columns | Badge |
|---|---|---|
| Outer portrait | 4 | `RECOMMENDED` |
| Outer landscape | 4 | `RECOMMENDED` |
| Inner portrait | 6 | `RECOMMENDED` |
| Inner landscape | 8 | `RECOMMENDED` |
| Partial book | 4 + 4 | `RECOMMENDED` |

- **Use an even column grid as an overlay**, or turn on the hidden layout grid in the kit templates with Ctrl-G.
- **In Partial Book the grid splits into two groups that meet at the hinge**, instead of placing a column on the fold.

---

# Navigation patterns

How navigation elements move between the outer and inner displays. The goal is always the same: people find controls where they left them.

The governing rule: **on the outer display and on inner landscape, bars are vertical and sit along one edge. Horizontal bars return only in inner portrait.** Keep the order of controls stable across every state, top to bottom: navigation first, then the prominent action, then toolbar groups, then the tab bar.

## Navigation bar

- **Outer:** back and the prominent action sit at the top of the vertical bar on the side display.
- **Inner portrait:** the bar is horizontal at the top, so the title and actions read as they do on any iPhone.
- **Inner landscape:** back stays on the side bar and the title moves into the content area.

Moving controls to the side display keeps vertical space for content and keeps them where people reach.

## Tab navigation

- **Outer:** tabs sit at the bottom of the vertical bar, below the toolbar groups.
- **Inner:** the tab bar can become a sidebar, so tab destinations and their contents are visible at once.

When it expands, destinations stay one tap away without covering what people are reading. The set of destinations never changes, only its presentation.

## Sidebar

Collections and destinations that persist between views.

- **Outer:** the sidebar becomes the root list you start from.
- **Inner:** it is displayed alongside the detail, so a tap moves the detail pane without losing the list.

## Vertical navigation

The vertical bar itself carries one column of current and app controls aligned with the hardware.

- **Outer:** the vertical bar keeps the same order and position on the outer display and on the inner display in landscape. Only the content area grows.
- People learn one place for actions. Apple keeps side controls aligned with the hardware, and on the same side in right-to-left languages.

## Toolbar

Actions for the current screen. They share the vertical bar with navigation and tabs, so space runs out sooner on the outer display.

- **Outer:** only the most important items surface, the rest move into the system overflow menu.
- **Inner:** more items fit, but they stay in the same order. Give frequent actions and badged items a higher visibility priority so the right ones survive the squeeze.

## Split navigation

A list and its detail. One view at a time on the outer display, both views side by side on the inner display.

- **Outer:** tapping a row on the list pushes the detail. The list stays in the stack.
- **Inner:** the detail pane appears beside the list and the selection stays highlighted. Folding the inner display resizes both panes to either side of the fold.

Preserve the selection and the scroll position across the transition.

## Contextual actions

Actions for a single item, shown where the item is.

- **Outer:** the menu opens next to the item on the outer display. It stays on the same side of the list as the item, never across the fold.
- **Inner:** the system menu moves away from the fold automatically. Custom menus should follow the same rule so they stay readable and easy to tap.

## Sheets

Focused, self-contained content for the current context.

- **Outer:** the sheet keeps its controls in a vertical strip, like the app underneath. On the inner display it is presented as a modal card and the app stays visible around it.
- **Partially folded:** the system slides it to one side of the hinge rather than splitting it. Close or Done is one tap away in both states.

---

# Adaptive patterns

Nine closed-to-open patterns for common product types. Each one keeps the primary task in place and uses the inner display for one more level of information. **Never a different app.**

For each pattern: what stays, what changes, and the mistake to avoid.

## Feed

A continuous stream of items.

- **Stays:** the stream, the scroll position and the item order.
- **Changes:** the columns of cards and a pane for filters or trending topics appear beside it.
- **Avoid:** adding a second column in a context where card width already carries the meaning, and reflowing so people lose their place.

## Master detail

A list and the detail beside it.

- **Stays:** the selected row stays selected and highlighted.
- **Changes:** the detail appears in the trailing pane instead of pushing over the list.
- **Avoid:** clearing the selection on the transition, and jumping the list back to the top.

## Messaging

A conversation, where the open state is the primary view.

- **Stays:** the composer, the draft text and the scroll position in the thread.
- **Changes:** the conversation list joins the leading side. The thread keeps the same width and stays readable.
- **Avoid:** stretching bubbles to the full inner width, which destroys the shape people read a chat by.

## Media

Listening or watching, with content on one side.

- **Stays:** the now-playing item, the transport controls and elapsed time.
- **Changes:** artwork grows and a queue or related list appears beside it.
- **Avoid:** scaling the artwork to fill the inner display while the controls slide below the fold.

## Maps

A map with a place or a route in context.

- **Stays:** the map viewport and the center of the search result.
- **Changes:** the place card moves from a sheet over the map into its own pane, so the map is never covered.
- **Avoid:** keeping a bottom sheet that now covers half the inner display and puts controls on the fold.

## E-commerce

Browsing a catalog and drilling into a product.

- **Stays:** the category, the filters and the scroll position in the grid.
- **Changes:** more products per row, and the product detail with its buy action opens in a second pane.
- **Avoid:** putting the buy button across the fold, which is the one control that must always be easy to press.

## Dashboard

Numbers and charts in a summary.

- **Stays:** the metrics shown and their order.
- **Changes:** stat tiles sit side by side instead of stacked, and charts get the width they need.
- **Avoid:** simply enlarging every tile, which adds no information, and letting a chart straddle the hinge.

## Settings

Hierarchical preferences, several levels deep.

- **Stays:** the group and the row the person came from.
- **Changes:** the category list and the detail pane are shown at the same time.
- **Avoid:** collapsing back to the root list when the device opens, which is the clearest form of losing task continuity.

## Calendar

A day or month view with events.

- **Stays:** the visible date range and the selected event.
- **Changes:** a single-column agenda becomes a wider view, and event detail moves into a pane.
- **Avoid:** placing a day column on the fold. Split the grid evenly at the hinge instead.

## Dark mode check

Every pattern needs a dark pass. On iPhone Duo the check has two extra parts:

- **The vertical bar and its controls** sit on a different surface than the content. Confirm contrast on both sides in dark mode.
- **The folding region** darkens differently than a flat surface. Anything that relies on a subtle fill or hairline near the fold can disappear.

---

# Do and don't

Ten rules drawn from Apple guidance for iPhone Duo. Use this as a review checklist for any design or diff.

## 1. Preserve task continuity

**Do:** keep the same screen, selection and scroll position when the device opens or closes, so people pick up exactly where they were.

**Don't:** rebuild the interface after unfolding. A new layout forces people to search for their place again, often mid-task.

## 2. Use the extra area for secondary context

**Do:** show the next level of hierarchy or supporting information next to the primary task.

**Don't:** simply scale every element larger. Bigger rows and wider cards add no information and push content below the fold.

## 3. Respect the hinge and reserved regions

**Do:** keep interactive elements on either side of the fold and away from the camera regions.

**Don't:** place critical actions across the fold. When the device is partially folded, the center is curved and hard to see and press.

## 4. Keep bars where the system puts them

**Do:** on the outer display and inner landscape, let toolbars and tab bars sit on the side. That placement is the core iPhone Duo pattern.

**Don't:** move bars back to the top and bottom. Overriding the vertical placement wastes vertical space and breaks what people learn on other apps.

## 5. Keep control order stable across poses

**Do:** navigation first, then the prominent action, then toolbar groups, then the tab bar. People should not relearn where actions live.

**Don't:** reorder actions for each pose. Controls that jump between poses are hard to find and track.

## 6. Split grids evenly at the fold

**Do:** use an even number of columns so content divides cleanly when the device folds.

**Don't:** let a column straddle the hinge. A card or image cut by the fold loses its most important detail.

## 7. Let scrolling content stay in place

**Do:** let feeds and articles keep flowing when the device folds. Move controls, not the stream.

**Don't:** push a feed around the fold. Displacing continuous content makes people lose their reading position.

## 8. Handle each safe-area inset on its own

**Do:** read every side separately. Insets are asymmetric on iPhone Duo because controls sit along one edge.

**Don't:** mirror left and right insets. Copying the trailing vertical bar inset to the leading edge wastes space and misaligns content.

## 9. Keep a readable line length

**Do:** on the inner display, give long text a comfortable measure and use the remaining width for a second pane.

**Don't:** run text across the whole inner display. Very long lines are tiring to read and make the extra width feel empty.

## 10. Use the system overflow menu

**Do:** when items overflow, move your own extra actions into the system menu so everything lives in one place.

**Don't:** add a second custom overflow menu. Two ellipsis buttons make people guess which one holds the action they need.

## Review checklist

Run this before calling an iPhone Duo screen done:

- [ ] Opening or closing the device preserves screen, selection and scroll position
- [ ] The inner display adds at most one extra level of hierarchy
- [ ] Nothing interactive sits within the 27 pt band centered on the fold `RECOMMENDED`
- [ ] No column, card or chart straddles the hinge
- [ ] Bars are vertical on the outer display and on inner landscape
- [ ] Control order is identical in every state
- [ ] Each safe-area inset is read separately, none mirrored
- [ ] Text has a max measure, roughly 680 pt `RECOMMENDED`, with extra width spent on a second pane
- [ ] Every control is at least 44 x 44 pt, never below 28 x 28 pt `OFFICIAL`
- [ ] Only one overflow menu exists, the system one
- [ ] Backgrounds and images run to the edges, text and controls stay inside the safe area
- [ ] Dark mode checked, including the vertical bar surface and the folding region
- [ ] Every non-`OFFICIAL` number in the implementation is marked as needing simulator or device verification

## Sources

Official Apple documentation behind these rules. Search the titles on developer.apple.com for the latest versions.

- Human Interface Guidelines, Designing for iPhone Duo (published 9 September 2026): anatomy, poses, reserved regions, arrangement views, vertical controls
- Human Interface Guidelines, Layout, Split views, Toolbars, Tab bars, Sheets: general layout, safe area and navigation guidance that still applies on iPhone Duo
- Human Interface Guidelines, Accessibility and Typography: control sizes (44 x 44 pt default, 28 x 28 pt minimum) and the iOS text style ramp
- Tech Talks, Design for iPhone Duo; Raise the bar with iPhone Duo; Strike a pose with adaptive layouts on iPhone Duo: control placement, overflow and priority, reserved regions, displacement, arrangements
- Tech Talks, Prepare your app for iPhone Duo; Leverage multiple displays and scenes on iPhone Duo: size classes, asymmetric safe areas, hinge states, Split View multitasking, scenes
- iPhone Duo Tech Specs: display sizes and pixel resolutions for both displays

Non-official values in this skill are derived from, or measured against, the community iPhone Duo UI Kit v1.0 (September 2026) by Noah Elhadedy, an unofficial resource not affiliated with or endorsed by Apple. iPhone, iOS and Apple are trademarks of Apple Inc.
