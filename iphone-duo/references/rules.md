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
