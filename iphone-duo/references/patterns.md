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
