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
