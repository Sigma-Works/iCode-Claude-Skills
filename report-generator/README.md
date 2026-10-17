# report-generator

A Claude skill that writes a short parent update after each class. It's the companion to [`lesson-generator`](../lesson-generator): teach from the deck, then send parents a report on what their kids learned.

## Output

```
10/17/2026
Orange Belt Sprint 2 Lessons 3 & 4
Aisha, Ben, Carlos, Dana

<150-word report on what the class learned, written for parents>
```

- **Line 1:** date (MM/DD/YYYY)
- **Line 2:** belt, sprint and lesson number(s)
- **Line 3:** students in the class, comma separated, exactly as the teacher typed them
- **Report:** exactly 150 words, one paragraph, plain text ready to paste into an email

The report covers every learning goal that was taught, explains technical terms in plain words, mentions what students built and which games they played, previews the next class, and ends with a question parents can ask at home.

## Usage

In the same conversation as the lesson plans or deck:

> Write the parent report. Students: Aisha, Ben, Carlos, Dana

Or in a new conversation, attach the lesson plans:

> Make a parent report for these lessons. Class was today. Students: Aisha, Ben, Carlos, Dana. We skipped the project.

Claude always asks for the student list if you don't give one; it never makes up names. Optional notes (what was skipped, what students enjoyed) are folded into the report.

## Installation

### Claude Code

Copy the `report-generator` folder into one of:

- `.claude/skills/` inside a project repo (shared with everyone who uses that repo), or
- `~/.claude/skills/` (just for you)

### Claude apps (claude.ai / desktop)

Zip the `report-generator` folder and upload it as a custom skill in Claude's settings. Organization admins can share it with the whole team.

## Files

```
report-generator/
├── SKILL.md    # Instructions Claude follows
└── README.md   # This file
```

## Customizing

Edit `SKILL.md` to change the word count, date format, header lines, tone, or the paragraph structure (for example, adding a sign-off from your company).

## Privacy

Reports contain student first names. Claude only uses names the teacher provides in that conversation and reports on the class as a group, not individual students.
