---
layout: article
titles:
  # @start locale config
  en      : &EN       About
  en-GB   : *EN
  en-US   : *EN
  en-CA   : *EN
  en-AU   : *EN
  zh-Hans : &ZH_HANS
  zh      : *ZH_HANS
  zh-CN   : *ZH_HANS
  zh-SG   : *ZH_HANS
  zh-Hant : &ZH_HANT
  zh-TW   : *ZH_HANT
  zh-HK   : *ZH_HANT
  ko      : &KO
  ko-KR   : *KO
  fr      : &FR       About
  fr-BE   : *FR
  fr-CA   : *FR
  fr-CH   : *FR
  fr-FR   : *FR
  fr-LU   : *FR
  # @end locale config
key: page-about
show_title: false
---

<style>
.about-photo {
  float: right;
  width: 45%;
  max-width: 340px;
  margin: 0 0 1.5rem 2rem;
  border-radius: 8px;
}
.about-hero-title {
  font-size: 2.1rem;
  font-weight: 700;
  line-height: 1.25;
  margin: 0 0 1.25rem;
}
@media (max-width: 480px) {
  .about-photo {
    float: none;
    width: 100%;
    max-width: 100%;
    margin: 0 0 1.5rem;
  }
}
</style>

<img class="about-photo" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/avatar.jpg" alt="Felix Bögge">

<p class="about-hero-title">Hi, Felix here</p>

I spent the last couple of years as a Backend Engineer, mostly heads-down in Python — Django, FastAPI, REST APIs, SQL, Docker, the usual toolbox. What I actually care about is software that still works after the demo is over: the boring parts, the edge cases, the thing not falling over at 2am. That's exactly what pulled me toward AI-powered applications — it's easy to make something look impressive in five minutes and a lot harder to make it hold up, and that gap is where I want to work.

These days I'm deep in AI Engineering — RAG, embeddings, vector databases, agents that actually call tools instead of just talking about it. I've built agentic workflows with LangChain and LangGraph, and I've gotten fairly obsessive about the unglamorous half of the job: tracing runs in LangSmith, scoring retrieval quality with RAGAS, and asking "what does this actually cost per run" before I get excited about an answer that looked good once. Claude Code and agentic coding aren't just tools I use — they've changed how I sit down and build something.

Right now that all comes together in [Plantopia](/FB/2026/09/16/Plantopia.html), my capstone project at Turing College — an AI agent that looks at a photo of a sick plant, asks the questions a photo can't answer, and returns an actual diagnosis with a treatment plan, backed by RAG, semantic search and web search rather than a single confident guess. Building it end to end — the agent, the data, the evaluation, the deployment — is exactly the kind of work I want to keep doing, and it's why I'm actively looking for an AI Engineering role, while staying open to backend roles where the two intersect.

Outside of tech, I spent ten months cycling from Germany to Sri Lanka, carrying a tent and mostly working out the route as I went. Some stretches were straightforward; others meant climbing mountains, enduring harsh weather conditions, or fixing my bicycle with whatever tools I had on hand. It taught me to stay calm with incomplete information and adjust rather than freeze — the same instinct I reach for now when a spec is unclear or a system does something I didn't expect.

<div style="clear: both;"></div>
