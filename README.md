# Content Production Systems

I publish long-form and short-form writing on a weekly cadence, and I run the operation like a
production line: a written process spec every session reads before drafting, automated quality
gates on every draft, a scheduled batch job that writes ahead of me, and dated decision gates
that revise strategy on measurements instead of mood. My degree is in finance. I taught myself
AI-assisted development by engineering my own workflows first, and this is the system I have
iterated hardest. Large language models automate the research, the drafting, and the checking.
Direction and sign-off stay with me.

This page documents the machinery and leaves the writing itself out of scope. The machinery is
the part that transfers.

## How a piece gets made

Ideas accumulate in a banked index. One long-form session opened with 19 banked idea drafts and
narrowed on three axes: format fit, virality, brand fit.

```text
19 banked idea drafts
 -> 5 shortlisted, directions brainstormed for all 5
 -> 1 chosen, direction locked
 -> outline confirmed before any prose, with per-section word budgets
 -> drafted section by section, pattern scan after every section
 -> full-draft scan, status flipped to review
```

The step that pays compound interest sits in the second line: all five brainstorms get written
back to their draft files, including the four that lost. The next session opens with the
narrowing already paid for and goes straight to picking.

Before prose, the workflow interviews me: themes, the concrete real-life anchor each theme hangs
on, target length, landing direction. The outline gets confirmed first because a pivot at
outline stage costs minutes and a pivot at draft stage costs the draft. Sections get word
budgets up front (a 2,500-word piece gives the hook 200 words and each core theme 800), and a
section runs over only when it earns the overage.

## One build, gated

Heavier pieces run as a staged build: named agent roles, one gate per phase, and research agents
that write full files to disk while returning tight summaries, so the drafting context stays
clean. The load-bearing files from one piece's working folder, research filenames generalized:

```text
00-plan.md        roles, phase gates, and the sourcing rule, written first
01-spine.md       the structural skeleton the draft must follow
research-*.md     five research files, every factual claim tagged by origin
sources-used.md   the citation ledger
voice-profile.md  the voice parameters this piece is drafted under
article-draft.md  first full assembly
critique.md       a red-team pass briefed to hit the weakest claim hardest
voice-qa.md       the automated pattern audit, findings logged
article-final.md  ships when every gate above passes
```

The sourcing rule is absolute: no fabricated numbers. Every factual claim carries an origin tag
(my own notes, the web, or unverified), and unverified claims get resolved or cut before the
final. The build also has a budget, two research rounds and two revision passes maximum, then
ship. Bounded iteration is what separates a pipeline from a hobby.

## The batch layer

A scheduled job runs every Sunday evening and drafts the coming week: five X posts and three
LinkedIn posts spread across my five content pillars, with a deliberate format mix of standalone
takes, one thread, one platform-native original, and cross-platform previews. Every draft passes
through the automated voice scan before it saves. HIGH-severity findings force a rewrite.
MED-severity findings save with the violation count recorded in the file's frontmatter. The
finished week files into a per-week queue directory with a schedule README, and a digest lands
in my inbox when the queue is ready. Every queued post then waits for my review. Publishing
stays a human action.

## Distribution

Long-form publishes to Substack first, its long-form home. The same day, X gets a thread-length
adaptation and LinkedIn gets a condensed professional version, each rewritten under that
platform's voice file rather than pasted across. Sections strong enough to stand alone spin out
as companion pieces on a weekly cadence, so one heavy piece feeds a month of distribution.
Written cross-posting rules decide which of the five pillars appear on which platform; two of
the five cross over only when a clearly professional angle earns it. An export script strips the
authoring artifacts (frontmatter, editor callouts, internal links, drafting notes) so a clean
publish copy regenerates from the source file on demand.

## What makes it hold up

### The voice gate

Heavy AI assistance has one failure mode that matters most: prose that reads machine-made. I
engineered the defense the way you would engineer a linter, and it runs as a gate.

- A pattern reference documents 15 named AI anti-patterns (significance inflation,
  throat-clearing openers, hedging stacks, synonym cycling, and eleven more), each mapped to one
  of three fix classes: cut, replace, or rewrite. Format rules ride along, including a hard ban
  on em dashes.
- A master voice file holds the invariants plus a six-dial parameter table set per piece:
  audience, register, edge, evidence weight, and target length among them. Six per-platform
  voice files carry only their deltas from the master, so a rule change lands in exactly one
  place.
- The automated scan checks a draft against the full reference and reports violations with line
  numbers and severity. Wired into the drafting workflow, it fails the run on HIGH-severity
  findings the way a failing test fails a build. It runs on every section during drafting and
  again on the assembled piece before the file saves.

The gate runs before saving, and that ordering is the design. A post-hoc review negotiates with
finished prose. A gate rewrites it.

### The retro loop

Every working session ends with a retrospective, and the lessons distill into a dated practices
file the next session reads on resume. Each entry carries its date and a link back to the
session that produced it, and an entry that recurs gets marked as recurred, which separates
one-off mistakes from patterns. A standing avoid-list sits beside the practices. The loop has
produced real policy. Three rules it forced: batch-verify every statistic, quote, and dated
event up front rather than at publish time; verify the citation type, so a load-bearing claim
traces to primary evidence and a secondary review gets demoted to a see-also; and raise the
fact-check bar as the register gets more confident, because an assertion stripped of hedges has
no cover if it breaks.

### Decision gates

Strategy documents start from primary sources, the platforms' own published policy pages, and
anything I could not confirm gets marked unconfirmed in the text. New information arrives as a
dated revision block that explicitly supersedes the sections it contradicts, so the document
carries its own correction history, ledger-style. Experiments close with a gate committed in
advance: one distribution experiment ran a 30-day baseline test with the branch for each outcome
written down before day one. Day 30 reads the measurements and takes a branch. Nobody relitigates
the strategy from scratch.

## The process, productized

I write technical guides on AI workflow practice sourced from these systems. The backlog is
itself a system: 17 ranked guide topics, each entry naming the exact skill and configuration
files that back it, so a published guide ships with working setup files instead of hand-waving.
Two are published. Two more are in drafting. Every guide clears the same voice gate before it
goes out.

## Tools

- Claude Code with custom skills for drafting, voice scanning, repurposing, and the weekly batch
- A scheduled task runner for the Sunday job, with an email digest when the queue is ready
- Obsidian as the content database: YAML frontmatter as machine-readable state (status,
  schedule, violation counts), with Dataview queries keeping the idea index in sync without
  manual edits
- Python for the export pipeline
- Plain Markdown end to end, so every stage is diffable and greppable

## The point

Every gate in this system exists because I use large language models heavily and want prose a
reader trusts. The division of labor is engineered: the model researches, drafts, and checks;
the gates hold the voice and the facts; I set direction and sign everything that ships. The same
shape, a written spec, hard gates, batch automation, and dated decision points, is how I now
build any operational workflow. Writing is where I proved it.
