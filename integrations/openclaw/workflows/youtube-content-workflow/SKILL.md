---
name: youtube-content-workflow
description: Run a five-agent YouTube production workflow through Content Strategist, Script Agent, Thumbnail / Title Agent, Distribution / SEO Agent, and Growth Analyst. Use when the user wants one prompt to produce a full video package or review an existing video's performance and plan the next one.
---

# YouTube Content Workflow

Use this workflow when the user wants a full YouTube production pass from one prompt.

## Available OpenClaw agents

- `content-strategist`
- `script-agent`
- `thumbnail-title-agent`
- `distribution-seo-agent`
- `growth-analyst`

## Trigger examples

- "Run the YouTube content workflow for this topic"
- "Build a full video package for this idea"
- "Take this video idea through strategy, script, packaging, and SEO"
- "Review this video's metrics and tell me what the next video should be"

## Default operating mode

- Orchestrate the workflow from the main session
- Use the specialized OpenClaw agents above in order
- Keep each handoff tight and explicit
- Save durable outputs to files when the user asks for a repeatable asset set

## Workflow order

### 1. Strategy

Send the request to `content-strategist` first.

Input should include:
- target audience
- topic or channel goal
- constraints
- desired video format if known

Require back:
- chosen angle
- target viewer
- core promise
- 3 hook options
- key talking points
- success criteria

### 2. Script

Send the approved strategy brief to `script-agent`.

Require back:
- recommended hook
- structure
- full spoken-word script
- retention notes
- CTA

### 3. Packaging

Send the script package to `thumbnail-title-agent`.

Require back:
- lead packaging concept
- 3-5 title options
- 3 thumbnail text options
- visual direction
- CTR hypotheses

### 4. Distribution

Send the strategy brief plus packaging set to `distribution-seo-agent`.

Require back:
- primary positioning/query angle
- YouTube description
- chapters
- keyword/topic signals
- 72-hour distribution plan
- repurposing copy

### 5. Analysis

Use `growth-analyst` in one of two ways:

- For new videos: ask it to define the launch hypothesis, targets, and post-publish review criteria
- For published videos: provide metrics and ask for diagnosis plus next-video recommendations

Require back:
- what to monitor
- likely failure modes
- next experiment
- recommendation back to `content-strategist`

## Output contract for the main session

Return a compact final package with these sections:

1. Strategy Brief
2. Script
3. Titles and Thumbnail
4. SEO and Distribution
5. Growth Review or Launch Hypothesis

Keep the final user-facing response compact unless the user asks for full artifacts inline.

## File outputs

If the user wants reusable artifacts, save them under:

- `memory/youtube-workflows/YYYY-MM-DD-[slug].md`

Suggested structure inside the file:
- original request
- strategy brief
- script
- packaging set
- publishing package
- growth hypothesis or review

## Rules

- Do not skip Strategy unless the user explicitly provides a locked brief
- Do not let Packaging invent promises the script does not fulfill
- Do not let SEO override audience clarity
- If metrics are missing, Growth Analyst must label assumptions clearly
- If the idea is weak, say so early and stop before full production unless the user insists

## If the user asks for a faster pass

Run a compressed version:
- `content-strategist`
- `script-agent`
- `thumbnail-title-agent`

Then append a short DIY SEO checklist instead of running the full distribution stage.
