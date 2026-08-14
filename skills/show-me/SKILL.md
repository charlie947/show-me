---
name: show-me
description: Use when the user asks to see something rather than read about it - "show me", "let me see it", "what does it look like", "give me options", or any moment you are about to describe a layout, a plan, a comparison or a design in prose. Renders it as a self-contained HTML page and opens it in the browser, in front of them.
---

# Show me

**A render they have not seen does not exist.**

This skill closes the gap between finishing something and actually handing it over. Describing a
picture in prose is not showing it. Printing a file path is not showing it. Both feel like
delivery and neither one is.

There is nothing to install. You write the HTML, you open it, they look at it.

## When this fires

Any time the answer is visual and you are about to type it out instead:

- a plan, a structure, a roadmap, a set of steps
- a comparison between two or more things
- a layout, a page, a design, a wireframe
- a report, a review, a dashboard, a summary of where you got to
- **any moment the user has to choose between options**

If they would have to read it twice, draw it once.

## Mode 1 - SHOW

One thing, or a stack of versions.

1. Write a **complete, self-contained HTML file** to a temp path. Inline CSS, no external
   requests, no CDN links, no web fonts. It has to render with the network off.
2. Include `<meta charset="utf-8">`. Without it every apostrophe becomes three characters of
   gibberish.
3. Open it and **bring the browser to the front** (see below).
4. Only then say anything about it.

## Mode 2 - PICK

Two or more directions the user has to choose between.

**Three minimum.** Two options is a yes-or-no wearing a disguise. Three is where someone starts
seeing what they actually want, and the answer is often a piece of the first inside the shape of
the third.

Lay them side by side on one page, each with a short label and a one-line description of the
argument it makes - not the decoration, the argument. Then ask.

**Never ask someone to choose between visual options described in words.** A text description of
a layout is your mental model of it, not the thing itself, so you get a ruling on the wrong
object or no ruling at all. Render first, ask second.

## Opening it properly

**`open -a "Google Chrome" file.html` is not showing them anything.** It creates the tab and does
not bring the browser forward, so it stacks up behind whatever they are actually looking at. On
macOS use this instead:

```bash
osascript <<'EOF'
tell application "Google Chrome"
  activate
  set w to front window
  make new tab at end of tabs of w with properties {URL:"file:///ABSOLUTE/PATH"}
  set active tab index of w to (count of tabs of w)
end tell
EOF
```

`activate` brings the window forward and setting `active tab index` selects the new tab. You need
both. On Linux, `xdg-open` is the equivalent, and on Windows, `start`.

**Then verify it worked.** Read the active tab's URL back and check it is yours - another window
or another process may have taken focus in between:

```bash
osascript -e 'tell application "Google Chrome" to return URL of active tab of front window'
```

A command that exits 0 is proof it ran, never proof they saw it.

## What renders as HTML, and what must not

**HTML** for anything they will look at or share: plans, reviews, comparisons, reports,
dashboards, option grids, session handoffs.

**Plain text** for anything they will paste into another tool: social posts, newsletter bodies,
docs, config files, instruction files. HTML there breaks the paste target, and in a config file
it costs tokens on every future session while buying nothing.

State which one you are producing before you build it.

## Two things that ruin it

**No background grid or texture on anything text-heavy.** It looks good on a dashboard and makes
a dense document genuinely hard to read.

**Look at it yourself first.** A render you have not opened is a render you cannot describe
honestly, and it is how a broken page gets presented as a candidate.


## What you say around it

The render does the explaining. Your words around it should be almost nothing.

**Lead with the verdict, not the process.** First line is what they are looking at and what you
think of it. Never open with what you are about to do or how you got there.

**End with one next thing**, on its own line, doable now:

```
Next: pick a direction and I will build it out.
```

One next step, not a menu. Not "let me know if you want changes", not a list of five things they
could ask for. If there is genuinely nothing next, say the work is done and stop.

**Say the verdict out loud, including the failures.** "This one is broken, the other two are
worth looking at" beats silence, and it beats presenting a broken page as a candidate.


## Do not guess

The failure that wastes the most time is not a bad render. It is a confident one built on
something nobody checked.

If you do not know a filename, a number, a status, a path, or what a link points to, **go and
check it** - read the file, run the query, open the page. A plausible answer you did not verify
is the failure, not a shortcut.

If you genuinely cannot check, say **"not verified"** in those words and name what is missing.
Never fill a gap with something that merely sounds right, never infer a value from a filename,
and never report the result of a check you did not run.

This is the same instinct Anthropic's own guidance names in its hallucination guidance: give the
model explicit permission to admit uncertainty and say it does not know, rather than leaving it
to pick the most likely-sounding answer.

## The check before you speak

One question: **have they seen this, with their eyes, in this session?**

If no, you are not finished, however done the artefact is.
