---
layout: post
title: "MCQ Analysis, Create PT Plan, and Project Retrospective"
description: "Week of Oct 12: what my College Board MCQ says about my strengths and weaknesses by topic, how our Friends of Poway Seniors project meets the Create Performance Task, and where the project stands."
categories: [CSP]
permalink: /csp/mcq-cpt-retrospective
author: rex0dex
toc: false
comments: false
---

## Monday: MCQ Analysis

I took the College Board practice MCQ on Friday. My topic-by-topic analysis (what the CB Analytics report says about my strengths and weaknesses by Big Idea, what I was doing wrong in each weak topic, and how I will get better) is being added here once I pull my score report from AP Classroom.

---

## Tuesday: Create Performance Task Analysis

The Create Performance Task has two parts: what I submit (program code, a video, and a Personalized Project Reference), and written responses on exam day that ask about that code. So the question for our project is not "is it big?" but "does one part of it clearly show every required element, and can I explain it?"

My part of our Friends of Poway Seniors capstone is the **Spot the Scam trainer**. A senior sees a real message beside a scam version of the same thing, picks the one they trust, then taps the part of the scam that gave it away. Scam types they miss come back sooner until they catch them.

### Submission requirements

| Requirement | Where it is in my project |
|---|---|
| **Input** | The player clicks which message they trust, then taps a part of the scam message (`chooseTrusted`, `tapPart` in `trainer.js`). |
| **Output** | Feedback on screen: "Good eye" or "Careful", the highlighted red flags, the named scam type, and the explanation; the score updates. |
| **A list that manages complexity** | `SCENARIOS` in `scenarios.js` holds every message pair. Without the list I would need a separate variable and a separate `if` for each pair; with it, adding a new scam is adding one item and no game code changes. |
| **A student-developed procedure with a parameter** | `pickNext(state, scenarios, rng, lastId)` in `scheduler.js` chooses the next practice message. `recordResult(state, type, caught)` updates the schedule. |
| **Sequencing, selection, and iteration inside it** | `pickNext` groups the scenarios by type (iteration), finds which types are due (iteration + selection), then chooses in priority order with an `if / else if` chain (selection), in a fixed order of steps (sequencing). |
| **The procedure is called** | `newRound()` calls `pickNext(...)` every round; `finishRound()` calls `recordResult(...)`. |

### Written response readiness

**Program design, function, and purpose.** The purpose is to help older adults recognize scams before a real one reaches them. The function is the practice loop: show a pair, collect the choice and the tap, explain the red flag, and schedule what comes next. I can describe the input (choice and tap) and output (feedback and score) using the actual screens.

**Algorithm development.** `pickNext` is a real algorithm with a reason behind each step. Each scam type sits in a "Leitner box" from 1 to 3. A miss sends a type back to box 1 and makes it due again in 2 rounds; a catch moves it up a box and pushes its next review out to 5, then 10 rounds. Each round the procedure picks, in order: a missed type that is due, then a type the player has not seen, then the most overdue review, otherwise a weighted random choice that favors lower boxes. I can explain how a change to the inputs (a player who always misses "prize" scams) changes the output (prize scams appear about four times as often).

**Errors and testing.** This is the strongest part, because it really happened. My first version picked the most overdue type first. A test that simulated a player who gets everything right expected all 8 scam types in the first 8 rounds, and it failed: only 6 appeared, because reviews of types already caught were taking turns before new types were introduced. I changed the priority order so missed types come first, then new types, then other reviews, and the test passed. Other tests check that a missed type returns exactly on the round it is due and never earlier.

**Data and procedural abstraction.** The `SCENARIOS` list is the data abstraction: the game code never cares how many scams exist or what they say. `pickNext` is the procedural abstraction: `newRound` only needs to know "give me the next message", not how the schedule works. If I change the box gaps from 2/5/10 to something else, nothing outside `scheduler.js` changes.

### What I still need to do for the Create PT

- Record a video under 1 minute showing input, the program running, and output (no voice needed).
- Make the Personalized Project Reference: screenshots of `SCENARIOS` being created and used, `pickNext` defined with its parameters, and the line that calls it. No comments in the PPR code.
- Practice explaining the testing story above in my own words without notes, since that is what the written responses check.

---

## Wednesday: Project Retrospective

**Project:** Friends of Poway Seniors website, team of Chetan Tiduwar, Kashyap Tubati, and me. Plan and board: [fops-pages issue #1](https://github.com/rex0dex/fops-pages/issues/1).

### What went well

- **The site is live** at [rex0dex.github.io/fops-pages](https://rex0dex.github.io/fops-pages/), redesigned for older adults: 20px text, text-size buttons that remember your choice, a six-word menu, and large buttons.
- **Spot the Scam works end to end**, including the adaptive schedule and saved progress, and it has automated tests.
- **Backend:** our Flask backend has accounts, sign-in, saved progress, and a redesigned admin dashboard, and it works locally with the website.
- **Planning:** the work is on a kanban board with one plan issue and a sub-issue for each person's system.

### What did not go well

- **I built too much at once.** Before our presentation we had Bingo animations, multiplayer, and several movement games, but they were not each person's own work yet. We had to pull them back to "work in progress" pages so each person can build and commit their own part. Next time: smaller pieces, and each owner builds their own from the start.
- **Hosting:** login only works when the backend runs on my laptop. The live site cannot reach it yet.
- **Process mistakes:** I created too many separate issues at first instead of one plan with sub-issues, and had to clean them up.

### Next sprint

| Who | Next step |
|---|---|
| Aaditya | Grow Spot the Scam to 30+ message pairs; make the Create PT video and PPR |
| Kashyap | Commit solo Bingo, then multiplayer rooms |
| Chetan | Commit the Head Nod exercise, then Head Turn |
| Team | Ask Mr. Mortensen about hosting the backend on the class server; fix the backend's default secret key before it goes online |
