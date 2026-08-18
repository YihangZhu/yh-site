# A framework for conducting ML research

7 steps, each with a time budget. The hard part isn't the order — it's sticking
to the limits. Most ideas die at step 4, and that's the point.
{ .standfirst }

<div class="phase-head" markdown="1">

## <span class="num">0</span> Get the lay of the land

1–2 weeks
{ .budget }

</div>

- Use Claude to gather related papers. Skim 20–30 abstracts and read 5 properly.
  Work out the main approaches, the standard benchmarks, and who is active in
  the area.
- Ask two or three people what's actually hard here, and what has already been
  tried and failed. Failed attempts rarely get published, so you can't learn
  this any other way.

<div class="phase-head" markdown="1">

## <span class="num">1</span> Get your hands dirty

1–2 weeks
{ .budget }

</div>

- Build the simplest thing that runs end to end, starting from a decent existing
  repository, to get a feel for the project.
- **Write the evaluation code now** — data splits, metric, seed control,
  logging. Every number you report from here on goes through it.
- **Keep a log file.** Anything unexpected, interesting, or important goes in
  it. This turns out to be your best source of ideas.

<div class="phase-head" markdown="1">

## <span class="num">2</span> Study one paper in depth

2–4 weeks, hard limit
{ .budget }

</div>

- Pick one direction for handling the challenges in the project.
- Pick a strong paper in that direction with a well-maintained code release.
  Spend a day checking the code runs before you commit weeks to it.
- Reproduce the main result, plus the ablations that are relevant to you.
- Analyse the paper's strengths and limitations — failure cases, unsupported
  assumptions or claims. These become the motivation for your own work.
- Use their training code to grow your own codebase, keeping the setups and
  findings worth keeping, and keeping the whole thing simple.

<div class="phase-head" markdown="1">

## <span class="num">3</span> Come up with ideas to test while expanding my knowledge on existing work

1–2 weeks
{ .budget }

</div>

- Aim for five or six candidates, not one. Sources: your log file; an assumption
  everyone in the area shares; cases where the method you reproduced fails; a
  technique from a neighbouring field; a real problem the benchmarks don't
  capture.
- For each one, finish this sentence: if this is right, the experiment that
  shows it is \_\_\_, and the result that proves it wrong is \_\_\_. If you
  can't finish it, it isn't a testable idea yet.
- Read the literature again to check for related work. Use Claude to widen the
  search — but verify anything it names before trusting it. Asking someone in
  the field is the reliable version. Fifteen minutes can save a month.
- Add the strongest existing methods to your own codebase, so later comparisons
  run through the same pipeline and differ in only one place.

<div class="phase-head" markdown="1">

## <span class="num">4</span> Try to kill each idea, cheaply

repeat until one survives
{ .budget }

</div>

- Small model, small dataset, fastest signal that could show the idea is wrong.
  Hours per attempt, not days.
- Aim for many quick attempts rather than a few careful ones. Careful comes
  next.
- Most ideas die here. Each one is cheap to lose and usually reshapes the
  next.
  { .kill }

A dead idea usually sends you back to step 3. Expect multiple rounds.
{ .return-note }

<div class="phase-head" markdown="1">

## <span class="num">5</span> Attack the idea that survived

2–4 weeks
{ .budget }

</div>

- Try to break it, not confirm it.
- Rigorous comparisons against existing methods, plus ablations, with proper
  statistical reporting.
- Check the claim holds elsewhere: another dataset, another model size, another
  architecture.
- Write the abstract and your main claim before the last round of experiments.
  It shows you whether you actually know what you're arguing.

<div class="phase-head" markdown="1">

## <span class="num">6</span> Write up and beyond

2–4 weeks
{ .budget }

</div>

- Full-scale runs. Experiments that show why it works, not just that it does.
- Clean code, clean configs, honest limitations — easy to write if you spent
  step 5 attacking your own result.
- Continue the project from the limitations of your current work, probably back
  to step 2.

<div class="principles" markdown="1">

## Principles

1. Keep comparisons and statistical reporting strictly fair. That means equal
   effort, not just equal intent — a baseline you ran once with default settings
   isn't a fair comparison, however careful the statistics around it are.
2. Publishing in a strong venue should be a by-product of having something
   interesting to say, not the goal itself. Aiming purely at publication is like
   starting a business to turn a quick profit rather than to build something
   good.
3. Take negative results seriously. A negative result is worth keeping when the
   experiment was capable of showing the opposite — that narrows the search
   space. "I couldn't make it work" is a much weaker claim than "it doesn't
   work".
4. Premature optimisation is the enemy. Don't tune, scale, or generalise
   anything until you know it's worth keeping.

</div>

<div class="coda" markdown="1">

**Who this is for.** It assumes you're new to the area. If you already know it
well, steps 0–2 shrink a lot and you start near step 3.

</div>
