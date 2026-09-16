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
