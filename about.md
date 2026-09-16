---
layout: article
titles:
  # @start locale config
  en      : &EN       Hey, I'm Felix Bögge
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
  fr      : &FR       Hey, I'm Felix Bögge
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

<p class="about-hero-title">Hey, I'm Felix Bögge</p>

I'm a Backend Engineer transitioning into AI Engineering, with 2+ years of professional experience building backend systems in Python — Django, FastAPI, REST APIs, SQL, Docker and Git. I enjoy building software that's reliable and well-tested, and I'm especially interested in how those same engineering habits carry over into AI-powered applications, where it's easy to optimize for a flashy demo and skip the parts that make something actually usable.

Right now I'm deepening that into AI Engineering specifically — LLM-based applications, RAG, embeddings and vector databases, and agentic architectures. I've built AI agents with tool and function calling and agentic workflows with LangChain and LangGraph, and I use LangSmith for observability and RAGAS to evaluate retrieval and generation quality, always with an eye on cost and scalability rather than just whether an answer looks right once. Claude Code and agentic coding are part of how I build now, not just what I build.

As part of my AI Engineering training at Turing College, I've been building portfolio applications with production-oriented architecture. My current project, [Plantopia](/FB/2026/09/16/Plantopia.html), is an AI-powered plant diagnostic app that combines an AI agent, RAG, semantic search, web search and agentic orchestration to identify plant conditions and recommend treatment. It's given me a concrete place to see how LLMs, data, tools, evaluation and backend engineering actually fit together — and it's why I'm actively looking to move into an AI Engineering role, while staying open to backend roles where software engineering and AI intersect.

<!-- Bicycle tour paragraph goes here — Felix is writing this one himself. -->

<div style="clear: both;"></div>
