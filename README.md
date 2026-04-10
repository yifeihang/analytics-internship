# Voxel AI Research & Analytics Intern Take-Home

Thanks for your interest in this internship. We are receiving dozens of applications per day,
many of them high quality, so we need some help from you to establish eligibility.

Our hiring process has two parts.
1. A take-home test (this).
2. An online interview, if your test submission is good.

We know that looking for internships sucks, so we're primed to move fast and give you actual
feedback to minimize your stress.
1. Please send in your submission by 5pm Pacific time on Sunday April 19, 2026. Late answers
   will not be considered, with no exceptions (sorry).
2. We'll read your submission within two business days of receipt. An earlier submission thus
   has a chance of making it to interview and offer before a later submission of possibly better
   quality. (We're a business, not your professor.)
3. You'll receive a response within two business days.
4. If you're selected for interview, we'll do our best to make that happen within a week.

Please don't contact us with questions. We won't have time to respond.

## Context

You are given a set of JSON files. Each file represents one customer call and contains:

- meeting metadata
- a list of extracted `safety_use_cases`
- a list of extracted `nonsafety_use_cases`
- evidence snippets supporting each extracted use case

These files were produced by an internal extraction pipeline over call transcripts, then
anonymized.

Voxel wants you to answer two questions:

1. What non-safety or adjacent opportunities are actually showing up in these calls?
2. How much should we trust the current extraction output?

## Your task

Produce a short analysis that:

1. Creates a cleaned, normalized view of the use cases in the dataset.
2. Identifies the main quality issues in the extraction output.
3. Recommends the top 3 non-safety or adjacent opportunities Voxel should pay attention to, with
   evidence.
4. Suggests one practical way to improve the extraction or review workflow.

It's your choice how long to spend on this, of course, but we think that more than 2-3 hours
would be overkill.

## What you should submit

Please fork this GitHub repo, make your changes in it, then send a PR.

- a 1-2 page memo or a short slide deck answering the business question
- a short `SUBMISSION.md` explaining your approach
- a notebook or script (we will not run it, but will probably read it)
- whatever other supporting files you see fit

## Guidance

You can use any tools you want, including LLMs. We are evaluating whether you use tools well and
can spot model hallucinations, junk data, or other sketchy outputs.

This project is intentionally ambiguous. We do not expect a perfect taxonomy or a perfect
answer. We want clear judgment, interesting thinking, and great communication.

Some examples of issues you might notice:

- the same concept appearing in both safety and non-safety buckets
- duplicate concepts phrased slightly differently
- generic admin or workflow items that may not be true use cases
- calls with noise or weird outputs
- labels that overstate or misrepresent what the underlying evidence actually supports

## What good work looks like

A strong submission will do many of the following:

- impose a sensible structure on a noisy label set
- distinguish product signal from customer-specific noise
- use as much data as possible
- make uncertainty explicit
- produce something that could actually inform a product or go-to-market decision

## Evaluation criteria

We will evaluate submissions on roughly these criteria:

- quality of analysis, synthesis, and business judgment
- clear, smart communication (an LLM-generated memo/deck or `SUBMISSION.md` will be a *big* red
  flag!)
- handling of ambiguity and data messiness

Of course we've used both Claude and Codex to one-shot this assigment, and they each produce
*something* within a few minutes... but are their results any good, and will we be able to tell
if you do the same if you can't talk through the details in an interview?

## Notes

- You do not need to build a polished app or dashboard.
- A lightweight, well-reasoned analysis is better than a complicated but shallow one.
- Brevity is good! Don't make us read five pages when one would do.
- If you make assumptions, say what they are.
- We're serious about not contacting us with questions. Please don't. Sorry.
