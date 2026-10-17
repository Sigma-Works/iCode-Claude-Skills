---
name: lesson-generator
description: Turn one or more lesson-plan files (PDF, DOCX, text) into a 60–90 minute classroom slide deck that hits every learning objective, with a hands-on web game after each learning goal. Use when a teacher uploads lesson plans and asks for slides, a deck, or a presentation to teach from.
---

# Lesson Generator

Build a teach-ready slide deck from the user's lesson plans. The deck must:

1. Cover **every** learning objective in the lesson plans (nothing dropped, nothing invented that contradicts them).
2. Run **60–90 minutes**, scaled to how much there is to teach.
3. Put an **interactive web game right after each learning goal**, so students immediately apply what they just learned.
4. Work for a small, energetic class of **4–10 students** (often kids or teens).

## Step 1 — Gather inputs

Read every attached lesson plan in full. Extract into a working list:

- Program / course name, unit or sprint, lesson numbers and titles
- Every numbered objective, verbatim (these are the checklist you must hit)
- Class-outline content, definitions, examples and code snippets
- Activities, projects, labs, required materials, worksheets
- Any links, preparation notes, or resource folders mentioned

Then check the user's message for:

| Input | If given | If not given |
|---|---|---|
| Game websites to use | Use only those sites (verify each, Step 3) | Choose games yourself (Step 3) |
| Class length | Use it | Compute it (Step 2) |
| Class size / age | Use it | Assume 4–10 students, ages ~8–14 |
| Class behavior notes ("chaotic", "quiet", "advanced") | Adapt activities and management slides | Assume mixed energy |

Do not stop to ask unless the lesson plans are missing or unreadable. State the assumptions you made in one line when you finish.

## Step 2 — Group objectives into learning goals and set the length

Lesson plans often list many fine-grained objectives (e.g. 8–12). One game per objective would be too many. Group related objectives into **learning goals** (clusters that share a concept), usually 2–6 per class. Example: "define position", "explain top/left", "apply position", "describe z-index", "use z-index" → one goal: *Position & stacking*.

**Length (unless the user set one):**

| Learning goals | Class length | Games |
|---|---|---|
| 2–3 | 60 min | 2–3 |
| 4 | 75 min | 4 |
| 5–6 | 90 min | 5–6 |

If two lesson plans are combined into one class, count goals across both.

**Time budget per learning goal** (adjust to fit the total):

- Teach: 6–10 min (explain, show, quick check for understanding)
- Try-it / activity: 3–5 min (hands-on in their own project, or an unplugged movement activity)
- Game: 5–7 min
- Fixed blocks: warm-up + rules 3–5 min at the start; project kickoff 5–8 min if the lesson plan has a project; exit ticket 2–3 min at the end

Write the schedule out (minute ranges per segment) before building. The minutes must add up exactly to the class length.

## Step 3 — Pick and verify the games

Each game must practice the skill of the learning goal it follows. Prefer **free, no-login, browser-based** games; kids should not need accounts or payment.

**If the user named websites:** fetch each site, list its games, and pick ones that match each learning goal. Note which are free vs paid; never assign a paid/Pro game without flagging it.

**If not:** pick from your own knowledge. Good starting points (verify before use — availability and pricing change):

| Topic | Games |
|---|---|
| CSS flexbox / grid / positioning | Codepip: Flexbox Froggy, Grid Garden, Anchoreum (codepip.com/games — check which are Free vs Pro); Flexbox Defense |
| CSS selectors | CSS Diner |
| HTML basics | Codepip HTML games (check if free) |
| JavaScript / general programming | CodeCombat (free levels), Elevator Saga (older students), Untrusted |
| Block coding / logic (younger kids) | Blockly Games, Code.org activities, Lightbot |
| Python | CodeCombat (Python mode), CheckiO |
| Git | Learn Git Branching |
| SQL | SQL Murder Mystery, SQL Island |
| Typing / keyboard skills | typing.com, Nitro Type |
| Robotics / logic / algorithms | Code.org, Blockly Games (Maze, Bird), Lightbot |
| Design / UX | Can't Unsee, The Boolean Game, Kerning game (type.method.ac), Color game (color.method.ac) |

**Always verify:** fetch each chosen game URL to confirm it loads, is free, and matches the goal. If a game page can't be fetched, pick another or tell the user. Give each game: exact URL, target levels for the time slot (e.g. "levels 1–8"), and a "speedy finisher" stretch option.

If no game fits a learning goal, use a short in-browser challenge instead (e.g. edit CodePen/their own project to hit a target) and say so.

## Step 4 — Plan the deck

Slide sequence (typical 22–35 slides):

1. **Cover** — course, unit, lesson numbers, a fun title
2. **Mission map** — the schedule with minute ranges; game breaks visually distinct
3. **Class rules** — a callback (e.g. "Hello!" → "World!" = hands off keyboards), "help with words, don't grab the mouse", and a points system that earns game time
4. For **each learning goal**:
   - Section intro slide (eyebrow "Part N", one-sentence big idea)
   - 2–5 teaching slides, one idea each, using the lesson plan's definitions and examples
   - 1 activity slide (try-it in code, or an unplugged "act it out" for movement)
   - 1 quick-check slide (predict / point / shout-out question; answer revealed on click or in notes)
   - **Game slide** — game name, URL, mission (levels), time, speedy-finisher option
5. **Project kickoff** (if the lesson plan has a project/lab) — requirements copied faithfully; optional labs marked optional
6. **Exit ticket** — one question per learning goal; answers in speaker notes; worksheet / homework reminder

Before building, map every objective from Step 1 to at least one slide. If any objective has no slide, add one.

## Step 5 — Write the content

**For a class of 4–10 kids:**

- Big type, short sentences, one idea per slide. A kid should get each slide in 5 seconds.
- Use analogies from their world (lunch lines, stickers, video games, houses).
- Every 8–10 minutes of talking, change mode: stand-up activity, pair challenge, quiz, or game.
- Name individuals' jobs (timer keeper, "captain") to channel energy.
- Use pairs or two small teams, not large groups.
- Show real code on dark code-block panels with syntax colors; keep code under ~12 lines per slide.
- Where the slide format allows live embeds, add small live demos (e.g. a running CSS animation).

**Speaker notes on every slide** — the teacher reads these, not the kids. Include:

- Which objective(s) the slide covers ("Objective 3: …")
- What to say / ask, with expected answers
- Common student mistakes to watch for
- What to cut if running late
- For game slides: how to start, set a timer, and how to stop ("Hello!" → "World!")

**Footer on each slide:** course name and the minute range for that segment, so the teacher always knows if they're on schedule.

## Step 6 — Build the deck

Use the best slide output available in the current environment, in this order:

1. A format the user named (PowerPoint, Google Slides) — use the matching skill.
2. A **Slides artifact type** if the session offers one (list artifact types first). Follow that type's own instructions.
3. Otherwise a **.pptx** via the pptx skill, or a self-contained HTML slide deck.

Design: one dark color, one light, 1–2 accents (pick from the course/belt/brand color if known); readable contrast; a rounded or friendly display font plus a clean sans for body text; a monospace font for code. Game-break slides should look different from teaching slides (e.g. dark background, big game title) so kids recognize them instantly.

## Step 7 — Check before handing off

- [ ] Every lesson-plan objective appears on at least one slide (and is labelled in notes)
- [ ] A game follows each learning goal and practices that goal's skill
- [ ] Every game URL was verified and is free (or flagged)
- [ ] Segment minutes add up to the class length (60–90)
- [ ] Project/lab requirements match the lesson plan exactly
- [ ] Every slide has speaker notes

## Step 8 — Hand off

Reply briefly: what the deck covers, the class length and why, which games were used (and any paid ones skipped), any assumptions, and which segment is the buffer to cut if the class runs long.
