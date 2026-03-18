---
title: STYLES.md
---

<header class="hero">
  <div class="wrap hero-grid">
    <div>
      <h1>STYLES.md</h1>
      <p class="lede">
        A simple, open format for defining how your project writes, designs, and
        communicates — readable by humans and AI coding agents alike.
      </p>
      <p class="lede">
        Think of STYLES.md as a <strong>README for style</strong>:
        a predictable, single place for your writing standards, design tokens, and
        AI agent constraints.
      </p>
      <div class="cta-row">
        <a class="button primary" href="#framework">Explore the framework</a>
        <a class="button secondary" href="https://github.com/mgifford/STYLE.md">View on GitHub</a>
      </div>
    </div>
    <aside class="code-card" aria-label="Simple sample STYLES.md snippet">
      <h2>Simple sample STYLES.md</h2>
      <p><a href="./STYLES-template.md">See full STYLES-template.md</a></p>
      <pre><code># STYLES.md

## Voice and tone
- Plain language: grade 8 reading level
- Active voice preferred
- Sentence case for headings

## Design tokens
- Primary color: #111111
- Font stack: Inter, system-ui, sans-serif

## AI agent rules
- Follow AGENTS.md for constraints
- Never override accessibility rules</code></pre>
    </aside>
  </div>
</header>

<section class="notice-experimental" aria-label="Experimental status notice">
  <div class="wrap">
    <p class="notice-heading">⚠️ Experimental — Validate before use</p>
    <p>
      This project is <strong>still experimental</strong>. Most content was generated with
      AI assistance and <strong>has not yet been fully validated in real-world conditions</strong>.
    </p>
    <p>
      A STYLES.md file will not automatically make your project consistent or accessible.
      What it <em>can</em> do is make your standards explicit, machine-readable, and
      easier for both humans and AI agents to follow.
    </p>
    <p>
      <strong>Please share your experience</strong> — positive or negative — in the
      <a href="https://github.com/mgifford/STYLE.md/issues">issue queue</a>.
    </p>
  </div>
</section>

<section id="why">
  <div class="wrap">
    <h2>Why STYLES.md?</h2>
    <div class="prose">
      <p>
        Style guides used to be PDFs, Figma boards, or wiki pages that nobody could find.
        In an era of AI-assisted development, a style guide must be a
        <strong>machine-readable logic gate</strong>.
      </p>
      <p>
        STYLES.md puts your writing conventions, design tokens, and AI agent constraints
        in one predictable file at your repo root — where humans, automation, and AI
        agents can all find and use it.
      </p>
      <p>
        It is part of a broader ecosystem of open standards:
        <a href="https://github.com/mgifford/ACCESSIBILITY.md">ACCESSIBILITY.md</a> and
        <a href="https://github.com/mgifford/sustainability.md">SUSTAINABILITY.md</a>
        provide the foundational guardrails that STYLES.md builds on.
      </p>
    </div>
  </div>
</section>

<section id="framework">
  <div class="wrap">
    <h2>The framework</h2>
    <div class="prose">
      <p>
        STYLES.md is one part of a three-pillar ecosystem. Together, these standards define
        not just <em>what</em> you build, but <em>how</em> you build it:
      </p>
    </div>
    <div class="cards">
      <a class="card" href="https://github.com/mgifford/ACCESSIBILITY.md">
        <h3>ACCESSIBILITY.md</h3>
        <p>The foundational requirement. Style is a subset of accessibility. Defines inclusion guardrails and contributor requirements.</p>
      </a>
      <a class="card" href="https://github.com/mgifford/sustainability.md">
        <h3>SUSTAINABILITY.md</h3>
        <p>The environmental constraint. Good style is lightweight and efficient. Defines compute and content efficiency rules.</p>
      </a>
      <a class="card" href="https://github.com/mgifford/STYLE.md">
        <h3>STYLES.md</h3>
        <p>The expression layer. Voice, tone, design tokens, and AI agent constraints for your specific project.</p>
      </a>
    </div>
  </div>
</section>

<section id="two-surfaces">
  <div class="wrap">
    <h2>Two surfaces, one standard</h2>
    <div class="prose">
      <p>
        STYLES.md distinguishes between two surfaces that share the same project:
      </p>
    </div>
    <div class="cards">
      <div class="card">
        <h3>GitHub Pages site</h3>
        <p>Public-facing pages built with Jekyll. Governed by design tokens, layout patterns, typography, and responsive breakpoints.</p>
      </div>
      <div class="card">
        <h3>Repository documentation</h3>
        <p>README, AGENTS.md, STYLES.md, examples, and templates. Governed by writing standards, heading hierarchy, and link conventions.</p>
      </div>
    </div>
    <div class="prose steps-footer">
      <p>
        Voice, tone, and accessibility requirements apply to <strong>both surfaces</strong>.
        Design tokens and layout patterns apply to the site surface only.
        See <a href="./STYLES.md">STYLES.md</a> for the full scope table.
      </p>
    </div>
  </div>
</section>

<section id="start">
  <div class="wrap">
    <h2>How to get started</h2>
    <div class="prose">
      <ol>
        <li>
          <strong>Fork</strong> this repository or copy
          <a href="./STYLES-template.md">STYLES-template.md</a> into your project root.
        </li>
        <li>
          <strong>Choose a flavor</strong> from the
          <a href="./examples/">examples</a> folder that matches your context.
        </li>
        <li>
          <strong>Customize</strong> the voice, tokens, and rules for your project.
          Replace all <code>[PLACEHOLDER]</code> values.
        </li>
        <li>
          <strong>Reference</strong> it in your <code>AGENTS.md</code> and LLM prompts
          so AI agents stay on-brand.
        </li>
        <li>
          <strong>Add the companion standards</strong> —
          <a href="https://github.com/mgifford/ACCESSIBILITY.md">ACCESSIBILITY.md</a> and
          <a href="https://github.com/mgifford/sustainability.md">SUSTAINABILITY.md</a> —
          for a complete governance baseline.
        </li>
      </ol>
    </div>
  </div>
</section>

<section id="resources">
  <div class="wrap">
    <h2>Resources in this repository</h2>
    <div class="cards">
      <a class="card" href="./STYLES.md">
        <h3>STYLES.md</h3>
        <p>This project's own style implementation. Two-surface structure, design tokens, and AI agent rules.</p>
      </a>
      <a class="card" href="./STYLES-template.md">
        <h3>STYLES-template.md</h3>
        <p>A minimal skeleton to copy into your own project and customize.</p>
      </a>
      <a class="card" href="./examples/">
        <h3>Examples</h3>
        <p>Worked examples for formal-gov, tech-minimal, and low-bandwidth contexts, plus a discovery prompt to generate a STYLES.md for any existing project.</p>
      </a>
      <a class="card" href="./AGENTS.md">
        <h3>AGENTS.md</h3>
        <p>Operational instructions for AI coding agents working in this repository.</p>
      </a>
      <a class="card" href="./ACCESSIBILITY.md">
        <h3>ACCESSIBILITY.md</h3>
        <p>Foundational accessibility commitment and contributor guardrails.</p>
      </a>
      <a class="card" href="./SUSTAINABILITY.md">
        <h3>SUSTAINABILITY.md</h3>
        <p>Environmental and compute-efficiency constraints for this project.</p>
      </a>
    </div>
  </div>
</section>
