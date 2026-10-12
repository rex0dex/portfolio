---
layout: post
title: "AP CSP Practice MCQ Analysis"
description: "Chetan Tiduwar, Kashyap Tubati, and Aaditya Prem took the College Board practice MCQ together. This is our topic-by-topic analysis of strengths, weaknesses, and how we will get better."
categories: [CSP]
permalink: /csp/mcq-cpt-retrospective
author: rex0dex
toc: false
comments: false
---

**Team:** Chetan Tiduwar, Kashyap Tubati, Aaditya Prem. We took the College Board practice MCQ together on Friday, so this analysis is shared.

**How this analysis is organized.** We are not listing "question 60: we picked B, the answer was C." Every question tests a **topic** (like conditionals, lists, or the internet), so we analyze by topic: what the topic is, what we were doing that leads to mistakes, why that thinking is wrong, and what we will do to get better. We only missed a few questions, so we also go through the areas where we are least confident even when we got the question right, plus the test-taking habits that cost points.

---

## 1. Our results

| | Result |
|---|---|
| Score | _from the AP Classroom score report_ |
| Strongest Big Idea (CB Analytics) | _from the report_ |
| Weakest Big Idea (CB Analytics) | _from the report_ |
| Topics of the questions we missed | _from the report_ |

### The five Big Ideas and how much of the exam they are

| Big Idea | Exam weight | What it covers |
|---|---|---|
| 1. Creative Development | 10–13% | Collaboration, program design, finding and fixing errors |
| 2. Data | 17–22% | Binary, compression, extracting information from data |
| 3. Algorithms and Programming | 30–35% | Variables, lists, conditionals, iteration, procedures, algorithms |
| 4. Computer Systems and Networks | 11–15% | The internet, fault tolerance, parallel and distributed computing |
| 5. Impact of Computing | 21–26% | Beneficial and harmful effects, digital divide, bias, safe computing |

Big Idea 3 is the biggest part of the exam and the one we practice every day in our lessons, so our goal there is near-perfect accuracy. Big Ideas 2, 4, and 5 are where we have spent the least class time, so that is where most of our study plan goes.

---

## 2. Big Idea 3: Algorithms and Programming

### College Board pseudocode versus Python
**What it is.** The exam writes code in College Board pseudocode, not Python. `x ← 5` stores, `x = 5` compares, lists start at **index 1**, and loops are written `REPEAT n TIMES`, `REPEAT UNTIL (condition)`, and `FOR EACH item IN list`.

**What goes wrong.** We read pseudocode with Python habits. The most common trap is the index: in Python `list[1]` is the second item, but in pseudocode `list[1]` is the **first**. The next is `REPEAT UNTIL`, which runs while the condition is **false** and stops when it becomes true, the opposite of a Python `while`.

**How we will get better.** Before answering any code question, we rewrite the first line in our heads as Python and say the index rule out loud ("pseudocode starts at 1"). We will trace every loop question on scratch paper with a small table of variable values per pass, instead of guessing from the shape of the code.

### Tracing loops and accumulators
**What it is.** Questions that show a loop and ask for the final value of a variable, or ask which code segment produces a result.

**What goes wrong.** Off-by-one errors: counting one pass too many or too few, or forgetting that the accumulator was updated **before** the loop ended. We also sometimes "recognize" a familiar pattern and answer from memory without checking a detail that was changed.

**How we will get better.** Trace with an actual table (pass number, each variable) for at least the first two passes and the last one. In our own lessons (3.08 Iterations, 3.10 Lists) we learned to predict before running; we will apply the same predict-then-check habit on paper.

### Conditionals and Boolean logic
**What it is.** `IF / ELSE`, nested conditionals, and expressions with `AND`, `OR`, and `NOT`.

**What goes wrong.** `NOT (a AND b)` is not the same as `NOT a AND NOT b`. Questions that ask which code is **equivalent** to another are where this shows up, and boundary values (`<` versus `≤`) decide the answer.

**How we will get better.** For "equivalent code" questions, test both versions with the values just below, at, and above the boundary, the same method we taught in our own 3.06 Conditionals lesson. For `NOT` with `AND`/`OR`, apply De Morgan's law deliberately: `NOT (a AND b)` = `NOT a OR NOT b`.

### Procedures, parameters, and return values
**What it is.** Procedures that take parameters and `RETURN` a value, and questions about what a call produces.

**What goes wrong.** Mixing up `DISPLAY` (shows something) with `RETURN` (sends a value back to the caller), and not noticing when a procedure returns early from inside a loop.

**How we will get better.** When tracing a procedure, mark where each `RETURN` can happen; the first one reached ends the procedure. Review 3.12 Calling Procedures and 3.13 Developing Procedures.

### Algorithm efficiency and undecidable problems
**What it is.** Comparing algorithms by how the number of steps grows, binary versus linear search, reasonable versus unreasonable time, heuristics, and problems no algorithm can solve (undecidable).

**What goes wrong.** Forgetting that **binary search needs sorted data**, and mixing up "unreasonable time" (exponential, still solvable in principle) with "undecidable" (no algorithm can always solve it).

**How we will get better.** Memorize the three-way difference: reasonable (polynomial), unreasonable (exponential or factorial), undecidable (no algorithm exists). Review our 3.17 Algorithmic Efficiency homework, where 1,000 books took 1,000 linear checks but only 10 binary ones.

### The robot grid
**What it is.** Questions with a robot (triangle) on a grid using `MOVE_FORWARD()`, `ROTATE_LEFT()`, `ROTATE_RIGHT()`, and `CAN_MOVE(direction)`.

**What goes wrong.** Losing track of which way the robot faces after a rotation, especially after several turns inside a loop.

**How we will get better.** Draw the grid and physically turn the paper, or write the facing direction after every line. Never trace a robot question purely in our heads.

---

## 3. Big Idea 2: Data

**Binary and overflow.** We need to convert between binary and decimal quickly and know that n bits store 2ⁿ values (8 bits: 256 values, 0 to 255). The mistake to avoid is thinking more bits only changes the largest number; it also explains **overflow** errors and **rounding** errors when a computer has a fixed number of bits. **Plan:** practice 5 conversions a day until it is automatic, and memorize powers of 2 up to 2¹⁰.

**Lossless versus lossy compression.** Lossless can rebuild the original exactly (needed for text and code); lossy throws data away to get smaller (fine for photos and music). The trap is assuming lossy is always worse; the question usually asks which fits a **situation**. **Plan:** for every compression question, first ask "does the original need to come back exactly?"

**Metadata and data analysis.** Metadata is data about data (a photo's date and location), and changing it does not change the data itself. Questions about cleaning data, finding patterns, and the limits of data (a dataset cannot answer a question it has no data for) are easy points if we read carefully. **Plan:** in data questions, check whether the dataset actually contains the information the answer needs.

---

## 4. Big Idea 4: Computer Systems and Networks

**How the internet works.** We need the vocabulary exactly: the internet is a network of networks; **IP** addresses and routes packets; **TCP** guarantees delivery and order; **UDP** is faster but does not guarantee delivery; **HTTP** is how the web uses the internet; **DNS** turns names into IP addresses. The common mistake is treating "the internet" and "the World Wide Web" as the same thing. **Plan:** make a one-page sheet of these protocols and what each one does.

**Fault tolerance and redundancy.** Questions show a network diagram and ask whether two devices can still communicate if a connection fails, or how many connections can fail. **Plan:** for each one, cross out the failed connections on paper and look for any remaining path, instead of eyeballing it.

**Parallel and distributed computing.** Speedup = sequential time ÷ parallel time, and the parallel time is set by the **longest** branch, not the total. The mistake is adding up the parallel tasks instead of taking the longest one. **Plan:** work three practice problems on speedup by hand.

---

## 5. Big Idea 5: Impact of Computing

This is a large share of the exam, and it is reading-heavy rather than code-heavy, which makes it easy to lose points by rushing.

- **Beneficial and harmful effects:** the same innovation can be both, and questions often ask for an effect that was **not intended**.
- **The digital divide:** unequal access to computing because of location, money, or ability. It connects directly to our capstone: Friends of Poway Seniors exists partly because older adults are often on the wrong side of it.
- **Bias in computing:** bias comes from the **data** and from the people who design the algorithm, not from the computer itself.
- **Crowdsourcing and citizen science**, and **legal and ethical** topics like Creative Commons, open source, and copyright.
- **Safe computing:** phishing, keylogging, malware, multi-factor authentication, encryption (symmetric versus public key), and personally identifiable information. Our capstone's Scam Defense trainer is built around exactly these attacks, so we should be strongest here.

**Plan:** for every Big Idea 5 question, underline what the question actually asks (most beneficial, least likely, NOT a reason) before reading the choices, because the wrong answers are often true statements that answer a different question.

---

## 6. Big Idea 1: Creative Development

Collaboration, the development process, and types of errors: **syntax** (breaks the language rules), **logic** (runs but gives the wrong result), **run-time** (fails while running, like dividing by zero), and **overflow**. The trap is calling a logic error a syntax error just because the result is wrong. **Plan:** when a question describes a bug, ask "did it run?" first. In our lessons we saw this directly: an `if` with no `else` runs and prints nothing, which is a logic error, not a syntax error.

---

## 7. Test-taking habits that cost points

These are not topics, but they are where most of our lost points come from.

1. **Reading the question too fast.** `NOT`, `LEAST`, `EXCEPT`, and "which of the following is NOT" flip the answer. We will underline these words before reading the choices.
2. **"Select two answers" questions.** Missing that a question needs two answers means a guaranteed miss. We will check for "select two" first.
3. **Answering from pattern recognition.** If code looks familiar, a detail has probably been changed. We trace anyway.
4. **Time.** About 70 questions in 120 minutes is under 2 minutes each. We will mark long tracing questions, skip them, and come back, so easy Big Idea 5 points are never left unanswered.
5. **Not using scratch paper.** Every robot, loop, binary, and network question gets worked on paper.

---

## 8. Our improvement plan

| Area | Action | How we will know it worked |
|---|---|---|
| Pseudocode and tracing | Trace one College Board pseudocode question per day on paper, with a variable table | Zero index or off-by-one mistakes on the next practice set |
| Binary and data | Five binary conversions a day; review compression and metadata | Convert 8-bit numbers both ways in under 30 seconds |
| Internet and networks | One-page protocol sheet; three fault-tolerance and speedup problems | Explain TCP, UDP, IP, DNS, and HTTP without notes |
| Impact of computing | Review safe computing and bias using our Scam Defense capstone | Full marks on Big Idea 5 questions in the next practice exam |
| Habits | Underline NOT/EXCEPT, check "select two", skip-and-return on long questions | Finish the next practice exam with time to review |

We will compare these against the AP Classroom score report on the next practice MCQ to see which plan items actually moved our scores.
