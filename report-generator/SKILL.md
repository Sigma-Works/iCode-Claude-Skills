---
name: report-generator
description: Write a short parent-facing class report (date, belt/sprint/lessons, student names, and a 150-word summary of what students learned) from lesson plans or a deck made with lesson-generator. Use when a teacher asks for a class report, parent update, parent message, or parent email after teaching a lesson. Not for building slides (use lesson-generator).
---

# Report Generator

Companion to the `lesson-generator` skill. After a class is taught, write a short report that parents read to learn what their child did in class.

## When to Activate

- After a class, the teacher asks for a parent report, parent update, class summary or parent email.
- In the same conversation as a lesson-generator deck, or in a new one with the lesson plans attached.
- **Not** for making slides or planning a class: use `lesson-generator`.
- **Not** for report cards or progress notes on individual students: this report covers the class as a group.

## Inputs

Collect these before writing. Look in the conversation first (lesson plans, a lesson-generator deck, the user's message).

| Input | Where it comes from | If missing |
|---|---|---|
| Date | User, or today's date | Use today's date |
| Belt / program | Lesson plan "Program Name" or the deck | Ask |
| Sprint number | Lesson plan "Sprint Name and Number" | Ask |
| Lesson number(s) | Lesson plan "Class Name and Number" | Ask |
| Student names | **The user only** | **Always ask. Never invent, guess or reuse names from another class.** |
| What was taught | Lesson plan objectives + outline; lesson-generator deck slides and games | Ask for the lesson plans or deck |
| Teacher notes (optional) | User, e.g. "we skipped the project", "they loved Grid Garden" | Assume the full lesson was taught |

If only the student names are missing, ask for just those in one short question. Ask for everything that is missing in a single message.

## Output format

Output exactly this, as plain text the teacher can paste into an email or message:

```
<date as MM/DD/YYYY>
<Belt> Sprint <#> Lesson(s) <#s>
<student names, comma separated>

<report: exactly 150 words>
```

Format rules:

- **Date:** month/day/year with leading zeros, e.g. `10/17/2026`.
- **Line 2:** e.g. `Orange Belt Sprint 2 Lessons 3 & 4`. Use "Lesson" for one, "Lessons" with `&` for two, and a range like `3–5` for three or more in a row (non-consecutive: `3, 5 & 7`).
- **Line 3:** names exactly as the user typed them (spelling and capitalization), in their order, separated by `, `.
- One blank line, then the report as a single paragraph.
- No headings, bullets, bold, emojis, sign-off or greeting unless the user asks.

## Writing the 150-word report

**Word count: exactly 150 words.** Count it with a tool (for example `wc -w`) before sending, and adjust by adding or cutting words until it is 150. Hyphenated terms and `@keyframes`-style terms count as one word. If no tool is available, number the words in groups of 10 and count again; do not estimate.

Audience: parents, many of them non-programmers. Tone: warm, upbeat, specific, professional.

Structure, in one paragraph:

1. **Opening (1 sentence):** the big idea of the class in plain words.
2. **What they learned (3–5 sentences):** cover every learning goal from the lesson plan(s). Name the real concept (e.g. "CSS position", "z-index", "@keyframes") and explain it in a few plain words, or with an analogy, in parentheses or after a comma.
3. **What they did (1–2 sentences):** the hands-on work: what they built, activities, the games they played (by name).
4. **Next class (1 sentence):** what comes next, from the lesson plan's project or the next lesson, if known. Skip if unknown.
5. **Home connection (1 sentence):** an easy question or action for parents, e.g. "Ask your child to show you…".

Rules:

- Describe the **class as a group**. Do not make claims about individual students (who did well, who struggled) unless the user gives that information explicitly.
- Only report what was actually taught. If the user says something was skipped, leave it out.
- Don't mention class behavior, the points system, or classroom-management details.
- No jargon without a plain explanation. No exaggeration ("mastered", "experts") — use "learned", "practiced", "built", "explored".
- Do not include student names inside the report paragraph; they're on line 3.

## Example

Input: the Orange Belt Sprint 2 Lesson 3 (CSS position and animation) and Lesson 4 (UX and UI design) lesson plans, taught as one class with Flexbox Froggy and Grid Garden breaks. Students: "Aisha, Ben, Carlos, Dana".

```
10/17/2026
Orange Belt Sprint 2 Lessons 3 & 4
Aisha, Ben, Carlos, Dana

Today our Orange Belt coders learned how websites decide where things go and how they move. Students explored the five CSS position values (static, relative, absolute, fixed and sticky) and used them to pin a "NEW!" badge onto a card. They discovered how z-index decides which element sits in front, then built their own CSS animations with @keyframes, trying ideas like a rainbow title and a racing car. In the second half, students stepped into the shoes of web designers. They learned the difference between UX (the blueprint of a website) and UI (its look and feel), created a user persona, and sketched a wireframe for their own home page. Along the way, they practiced their new skills in coding games such as Flexbox Froggy and Grid Garden. Next class, students will build their home page from a Bootstrap theme. Ask your child to show you an animation they made!
```

(The report paragraph above is exactly 150 words.)

## Before sending — checklist

- [ ] Date is MM/DD/YYYY
- [ ] Belt, sprint and lesson numbers match the lesson plan(s)
- [ ] Student names are exactly what the user gave
- [ ] Report is 150 words, counted with a tool
- [ ] Every learning goal taught is mentioned; nothing untaught is
- [ ] Plain text, single paragraph, no extra headings or sign-off

## Anti-Patterns

- Writing a report with placeholder or guessed student names instead of asking.
- Estimating the word count ("about 150") instead of counting it.
- Asking several follow-up questions one at a time; ask for everything missing in one message.
- Praising or singling out individual students, or mentioning behavior or the points system.
- Listing every fine-grained objective as jargon; group them into a few plain-language learning goals.

## Multiple classes

If the user asks for reports for several classes or groups, produce one block per group in the format above, separated by a line with `---`.
