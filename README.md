# Show me

**A render you have not seen does not exist.**

A Claude skill that stops your agent describing things at you and makes it render them instead.
Plans, comparisons, layouts, reports, options to choose between. It writes a self-contained HTML
page and opens it in your browser, in front of you, before it says a word about it.

There is nothing to install beyond the skill. No dependencies, no CDN, no build step.

## Install

```
/plugin marketplace add charlie947/show-me
/plugin install show-me@show-me
```

Or drop `skills/show-me/SKILL.md` into `~/.claude/skills/show-me/`.

## Use it

Say **show me**. Or ask for a plan, a comparison, three options, or anything you would rather
look at than read.

## What it fixes

**Walls of prose.** Ask for anything with a shape to it and you get eight paragraphs. So you
skim, and skimming an agent's plan is how you approve the wrong thing and find out an hour later.

**Choosing from descriptions.** Two options described in words is a ruling on the wrong object.
This renders three, side by side, and you pick with your eyes.

**Work that never arrives.** The most common failure is not a bad render, it is a finished render
nobody opened. `open -a "Google Chrome"` creates a tab without bringing the browser forward, so
the page stacks up behind whatever you were looking at. The skill uses `osascript` to activate the
window AND select the tab, then reads the active tab's URL back to prove you are looking at it.

## What it will not do

It keeps HTML for things you look at and plain text for things you paste. Social posts, newsletter
bodies and config files stay as text, because HTML there breaks the paste target or costs you
tokens on every future session.

## Licence

MIT. Built by [Charlie Hills](https://charliehills.substack.com).
