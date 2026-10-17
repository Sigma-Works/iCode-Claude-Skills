# lesson-generator

A Claude skill that turns lesson plans into a ready-to-teach slide deck with built-in game breaks.

Give Claude one or more lesson-plan files (PDF, Word, or text). It returns a 60–90 minute slide deck that:

- **Covers every learning objective** in the lesson plans, with each objective labelled in the speaker notes
- **Scales the class length** to the amount of content (2–3 learning goals → 60 min, 4 → 75 min, 5–6 → 90 min)
- **Adds a web game after each learning goal** so students practice what they just learned (e.g. Codepip's Flexbox Froggy after a CSS layout lesson)
- **Fits small classes of 4–10 students** with a callback signal, points system, movement activities and quick checks
- **Includes teacher speaker notes** on every slide: what to say, expected answers, common mistakes, what to cut if running late
- **Shows a minute marker** on every slide so the teacher always knows if the class is on schedule

## Usage

Attach the lesson plans and ask, for example:

> Make a slideshow from these lesson plans.

> Make slides from these two lesson plans for a 60-minute class of 6 kids. Use games from https://codepip.com/games/.

Optional things you can tell Claude:

| Option | Example |
|---|---|
| Game websites to use | "Use games from codepip.com and code.org" |
| Class length | "It's a 75-minute class" |
| Class size / age | "8 students, ages 10–12" |
| Class behavior | "They're chaotic" / "They're advanced" |

If you don't name game sites, Claude picks free, no-login games that match each topic and checks that each link works.

## Installation

### Claude Code

Copy the `lesson-generator` folder into one of:

- `.claude/skills/` inside a project repo (shared with everyone who uses that repo), or
- `~/.claude/skills/` (just for you)

### Claude apps (claude.ai / desktop)

Zip the `lesson-generator` folder and upload it as a custom skill in Claude's settings. Organization admins can share it with the whole team.

## Files

```
lesson-generator/
├── SKILL.md    # Instructions Claude follows
└── README.md   # This file
```

## Customizing

Edit `SKILL.md` to change:

- **Timing rules** — Step 2 (class length table and minutes per segment)
- **Default game list** — Step 3 (add your company's preferred sites)
- **Slide structure** — Step 4 (e.g. add a fixed "Codie Upgrade" slide)
- **Classroom management style** — Steps 4–5 (callback phrase, points system)

## Notes

- Game availability and pricing change. The skill tells Claude to verify every game link at build time and to flag paid ones.
- Decks are built in the best format available: a Slides artifact in Claude apps, or PowerPoint / HTML elsewhere. Ask for a specific format (e.g. "as a PowerPoint") to override.
