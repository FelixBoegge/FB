---
layout: article
title: Plantopia
mathjax: false
---

![Plantopia](https://raw.githubusercontent.com/felixboegge/FB/master/assets/plantopia/banner.png)

Plantopia is an AI agent that looks at a photo of a sick plant — houseplant, garden or balcony — asks the handful of questions a photo can't answer, and comes back with a ranked list of what's probably wrong and a treatment plan to fix it. Behind it sits a full agent pipeline with retrieval-augmented generation grounded in a curated plant-disorder knowledge base, rather than a single model call guessing from a photo, and it's now live at [plantopia-ai.com](https://plantopia-ai.com).

## The problem

Plant symptoms are rarely diagnostic on their own. Yellowing leaves alone are consistent with overwatering, underwatering, nitrogen deficiency, too little light, root rot, spider mites, natural aging, or transplant shock. A photo can show you the symptom, but it can't tell you which of those it is.

Most plant-ID apps skip straight past that problem. You upload a picture, and they return one confident answer based on image classification alone — no questions asked, no reasoning shown. That works fine for "what species is this?" It works badly for "what's wrong with it?", because the information that actually resolves the ambiguity — how often you water, whether the pot drains, how much light it gets, what the weather's been doing — isn't in the photograph at all.

## How Plantopia solves it

Plantopia asks before it answers, the way a doctor takes a history before diagnosing. It looks at the photo, forms some working hypotheses, then pauses to ask the two or three questions that would actually distinguish between them — not a generic form, but questions chosen for that specific plant and that specific set of symptoms. Only after it has that context does it commit to a diagnosis.

And it commits to more than one. Instead of a single verdict, it returns a differential: two or three ranked candidates, each with the evidence for it, the evidence against it, and a quick test you can run to tell them apart. If the evidence is too thin to be confident, it says so instead of guessing — a wrong "probably fine" is worse than "I'm not sure, here's what to check."

## What it can do

- **Rejects non-plant photos** before anything else runs, and flags photos that are too blurry to work with
- **Identifies the species**, cross-checking a vision model's read of the photo against a dedicated plant-ID service, and says how confident it is
- **Extracts symptoms with their position on the plant** — interveinal yellowing and leaf-tip yellowing point to different causes, so where a symptom is matters as much as what it is
- **Asks a handful of targeted questions**, most already pre-filled from the photo's own metadata, before it commits to anything
- **Pulls in real weather data** for outdoor plants — day by day, with dates, because "a couple of frost nights in the last three weeks" is only useful if you know whether that was last night or two weeks ago
- **Returns a ranked differential**, not a single answer, with the reasoning and a five-minute test behind each candidate
- **Builds a dated treatment plan**, starting with the least invasive step
- **Warns you if a problem is contagious** to your other plants
- **Remembers every plant you've diagnosed** — a history of past observations, diagnoses and treatment steps, so you can see whether things are actually improving
- **Learns durable facts about you**, like "tends to overwater" or "lives in a low-light apartment," and uses them as context in later diagnoses — visible and deletable at any time
- **Re-checks progress** — upload a new photo of a known plant and get a verdict (better, worse, unchanged, or something new) without repeating the same questions
- **Answers follow-up questions in a chat scoped to that plant**, and tells you which sources it actually consulted for each answer

![Plantopia's My Plants view](https://raw.githubusercontent.com/felixboegge/FB/master/assets/plantopia/my-plants.jpg)

## How it works

Under the hood, a diagnosis runs through a defined pipeline rather than a single free-form model call — there are steps that have to happen in a strict order (you can't diagnose before you've identified the plant, and the clarifying questions always have to be asked before a verdict is reached), and a loose "just figure it out" agent won't reliably guarantee that.

Roughly, a run flows like this: the photo is checked and the species identified, then symptoms are extracted with their location on the plant. The agent pauses there to ask its clarifying questions and waits for your answers. Once it has them, it reasons about which disorders are actually worth investigating before doing any lookups — naming candidates by name rather than trusting a similarity search to surface the right one, which turned out to matter a lot: on cases where the wording didn't closely match the reference material, the right document was sitting at rank 16 out of 43 in plain similarity search. Reasoning first and then retrieving by name took retrieval accuracy on that class of cases from roughly 82% to 100%.

From there it enriches its reasoning with whatever it's missing — the plant's care profile, recent weather if it's outdoors, a web search if the internal knowledge base doesn't cover that disorder well — and only then produces the diagnosis, checks whether it's contagious, and builds the treatment roadmap.

Conversational follow-up (the plant-specific chat) works differently, because a conversation doesn't have a fixed shape the way a diagnosis does — it uses a more flexible reasoning loop instead of the fixed pipeline, but draws on the same tools and the same stored history.

![Plantopia diagnosis result](https://raw.githubusercontent.com/felixboegge/FB/master/assets/plantopia/diagnosis-result.jpg)

## Under the hood

- **Backend:** Python / FastAPI, with the agent pipeline built on LangGraph as two graphs — one a strict state machine for diagnosis, the other a ReAct-style loop for chat
- **Frontend:** React, built with Vite and styled with Tailwind CSS
- **Database:** PostgreSQL with pgvector, hosted on Supabase — stores everything from plants and diagnoses to the vector-indexed disorder corpus and the agent's own conversation checkpoints
- **Models:** routed through OpenRouter, split by task — cheap models for simple binary checks, a vision model for identification and symptom extraction, a stronger reasoning model for the actual diagnosis and treatment planning, and an embedding model for retrieval
- **Observability:** every graph run is traced in LangSmith — nodes, tool calls, token usage — and LangGraph Studio lets me step through a run node by node while developing
- **External services:** Pl@ntNet for a second opinion on species; OpenStreetMap's geocoder turns a coarsened GPS fix into a place name; Open-Meteo fetches the three weeks of weather behind that place and the seven-day forecast ahead; Tavily web search as a fallback when the curated knowledge base doesn't cover a disorder well
- **Deployment:** containerized and running on Google Cloud Run (GCP), behind a custom domain with a managed TLS certificate; real email delivery for account verification instead of a stub mailer

## Built to hold up

Because a diagnosis is only useful if it's actually right, the project carries a golden-set evaluation harness that scores real model runs against hand-labeled cases — not just unit tests asserting on code paths, but a measurement of whether the diagnosis itself lands on the correct answer. On the last full run, it hit 89% top-1 accuracy and 96% top-3 accuracy across 28 cases spanning different disorder categories. It's backed by a fairly large automated test suite too — over 2,000 backend tests plus a Playwright-driven browser suite that exercises the real frontend against a real backend, because a passing component test has, more than once, described a screen that didn't actually work.

## Closing thoughts

Building this meant going well past the agent logic into the surrounding product: auth, a data model that survives account deletion cleanly, a deployment pipeline, and a UI that has to make a multi-step, occasionally-paused process feel like a single coherent action. Every model call is metered too — cost in USD and tokens is tracked per diagnosis and rolled up per plant and per account, so a run's price is never a mystery. A lot of the interesting problems weren't in the model calls at all — they were in things like making sure a photo's capture date (not its upload date) is what the weather lookup anchors on, or stripping GPS data out of an uploaded image without also destroying the pixels a diagnosis depends on.

You can try it live at [plantopia-ai.com](https://plantopia-ai.com), or read the code and the full design writeup in the [GitHub repository](https://github.com/FelixBoegge/plantopia).
