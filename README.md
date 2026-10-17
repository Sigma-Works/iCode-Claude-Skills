# Claude Skills for Coding Instructors

Claude skills that help coding instructors plan classes and keep parents in the loop. They were built for small belt-based coding classes (4–10 students), but work with any lesson plans.

## Skills

| Skill | What it does | Input | Output |
|---|---|---|---|
| [`lesson-generator`](skills/lesson-generator) | Turns lesson plans into a ready-to-teach slide deck with a web-game break after each learning goal | Lesson-plan files (PDF, Word, text) | A 60–90 minute slide deck with speaker notes |
| [`report-generator`](skills/report-generator) | Writes a short parent update about what the class learned | Lesson plans or a lesson-generator deck, plus student names | Date, belt/sprint/lessons, student list, and a 150-word report |

## Workflow

The two skills are designed to be used together:

1. **Before class:** attach the lesson plans and ask Claude to make the slides (`lesson-generator`).
2. **Teach** from the deck. Each slide shows the minute range, and speaker notes cover what to say and the answers.
3. **After class:** ask Claude for the parent report and give it the student names (`report-generator`).
4. Paste the report into your email or messaging tool for parents.

Example prompts:

> Make a slideshow from these lesson plans. Use games from https://codepip.com/games/.

> Write the parent report. Students: Aisha, Ben, Carlos, Dana

## Repository structure

```
claude-skills/
├── README.md
└── skills/
    ├── lesson-generator/
    │   ├── SKILL.md      # Instructions Claude follows
    │   └── README.md     # Details, options and customizing
    └── report-generator/
        ├── SKILL.md
        └── README.md
```

Each skill folder is self-contained. The folder name matches the `name:` field in its `SKILL.md`.

## Installation

### Claude Code

Copy the skill folders you want into one of:

- `.claude/skills/` inside a project (shared with everyone who uses that project), or
- `~/.claude/skills/` (just for you)

```bash
git clone <this-repo-url>
cp -r claude-skills/skills/* ~/.claude/skills/
```

### Claude apps (claude.ai / desktop)

Zip a skill's folder (for example `lesson-generator/`) and upload it as a custom skill in Claude's settings. Organization admins can share uploaded skills with the whole team.

```bash
cd skills && zip -r lesson-generator.zip lesson-generator
```

## Contributing

- Add a new skill as its own folder under `skills/` with a `SKILL.md` and a `README.md`.
- Keep the `description` in each `SKILL.md` frontmatter clear about **when** to use the skill; Claude uses it to decide when the skill applies.
- Test changes on real lesson plans before merging.
- Don't commit build artifacts such as `.zip` files.

## Privacy

`report-generator` uses student first names supplied by the teacher in the conversation. Don't commit real student names, reports, or lesson materials containing student information to this repo.
