# iPhone Duo skill

A Claude Code / Claude Agent skill for designing and building app UI for **iPhone Duo**, the folding iPhone with a compact outer display and a larger inner display joined by a center hinge.

It loads when a task mentions iPhone Duo, a foldable iPhone, dual displays, the hinge or folding region, the vertical bar, asymmetric safe areas, or adapting an iOS screen to open and close.

## What's inside

```
iphone-duo/
  SKILL.md                  the five rules that decide every layout, workflow, key constants
  references/
    anatomy.md              six device configurations with sizes, size classes, poses, reserved regions
    layout.md               safe areas, hinge avoidance band, margins, max text width, column grids
    navigation.md           where nav bars, tab bars, sidebars, toolbars, sheets and menus go
    patterns.md             nine adaptive patterns (feed, list-detail, chat, media, maps, shop, dashboard, settings, calendar)
    rules.md                ten do/don't rules, a review checklist, and the sources
```

[`IPHONE_DUO_GUIDE.md`](IPHONE_DUO_GUIDE.md) is the same content merged into one file, if you just want to read it.

## Install

Claude Code, for one project:

```bash
git clone https://github.com/yehdan8-debug/iphone-duo-skill.git /tmp/iphone-duo-skill
cp -R /tmp/iphone-duo-skill/iphone-duo .claude/skills/iphone-duo
```

Or for every project, copy it to `~/.claude/skills/iphone-duo` instead.

## How the numbers are marked

Apple had not published every iPhone Duo specification as of September 2026, so every value carries a confidence badge and the skill tells the agent to repeat that badge whenever it quotes one.

| Badge | Meaning |
|---|---|
| `OFFICIAL` | Stated by Apple in the HIG, Tech Talks or Tech Specs |
| `DERIVED` | Calculated from an official number |
| `RECOMMENDED` | A design value chosen because Apple has not published one |
| `ILLUSTRATIVE` | Drawn for clarity, not for measurement |
| `ASSUMPTION` | Believed true from context, unconfirmed |

Anything not `OFFICIAL` is a starting point to verify in the Xcode 27.1 simulator and on device.

## Credit and legal

Official guidance comes from Apple's Human Interface Guidelines, Tech Talks and Tech Specs for iPhone Duo (published 9 September 2026), listed in full at the end of [`iphone-duo/references/rules.md`](iphone-duo/references/rules.md).

Non-official values are derived from the community **iPhone Duo UI Kit v1.0** by [Noah Elhadedy](https://noahelhadedy.com), a free unofficial resource not affiliated with or endorsed by Apple.

iPhone, iOS and Apple are trademarks of Apple Inc. This repository is unofficial, is not affiliated with or endorsed by Apple, and redistributes no Apple design resource files, fonts, symbols or product bezels.

## License

MIT for the text in this repository. See [LICENSE](LICENSE).
