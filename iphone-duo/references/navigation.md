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
