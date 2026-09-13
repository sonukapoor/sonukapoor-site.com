---
layout: detail
title: "The reachability ceiling"
page_title: "The reachability ceiling"
hide_title: true
date: 2026-09-13
description: "Reachability analysis promises to cut vulnerability noise by telling you whether your code calls the broken function. Measured against a random sample of 150 npm advisories, only about one in six names a function at all, and the rest fail silently."
keywords:
  - Reachability analysis
  - npm advisories
  - OSV
  - GHSA
  - Supply chain security
  - Vulnerability management
  - SCA
  - False negatives
  - Software composition analysis
schema:
  "@context": "https://schema.org"
  "@graph":
    - "@type": "ScholarlyArticle"
      "@id": "https://sonukapoor.com/articles/reachability-ceiling/#article"
      url: "https://sonukapoor.com/articles/reachability-ceiling/"
      mainEntityOfPage: "https://sonukapoor.com/articles/reachability-ceiling/"
      headline: "The reachability ceiling"
      description: "A random sample of 150 GHSA npm advisories, classified on whether the advisory names a function a consumer's own code would call. 16.7 percent do. When none is named, reachability tooling reports not affected rather than cannot determine."
      datePublished: "2026-09-13"
      dateModified: "2026-09-13"
      inLanguage: "en"
      isAccessibleForFree: true
      author: { "@id": "https://sonukapoor.com/#person" }
      publisher: { "@id": "https://sonukapoor.com/#person" }
      isPartOf: { "@id": "https://sonukapoor.com/#website" }
      about:
        - "@type": "Thing"
          name: "Software composition analysis"
        - "@type": "Thing"
          name: "Reachability analysis"
      citation:
        - "@type": "SoftwareSourceCode"
          name: "npm-vuln-symbols"
          description: "Sample, both classification rounds, extraction code and proposed symbol records."
          codeRepository: "https://github.com/sonukapoor/npm-vuln-symbols"
          programmingLanguage: "TypeScript"
---

<div class="article-body" markdown="1">

<header class="article-masthead">
  <p class="article-eyebrow">
    <span>Measurement</span>
    <span>OSV npm feed, September 2026</span>
    <span>150 advisories sampled</span>
  </p>
  <h1>The reachability ceiling</h1>
  <p class="article-standfirst">
    Reachability analysis is sold as the cure for vulnerability alert fatigue: it tells you
    whether your code actually calls the broken function. I measured how often an npm advisory
    names a function at all. The answer is about one in six, and when there is nothing to name,
    the tooling does not go quiet. It tells you that you are safe.
  </p>
</header>

## Every scanner answers the easy question

Run `npm audit` on a real project and you get dozens of alerts. Almost all of them are for
packages you pulled in transitively and code you never touch. The scanner knows the vulnerable
version is in your tree. It has no idea whether you go anywhere near the vulnerable part.

Reachability analysis is the answer the industry settled on. Snyk, Endor Labs and Arnica all sell
it. The published research is encouraging: one recent framework reports a
[78 to 89 percent reduction in false positives](https://arxiv.org/pdf/2506.18050v1) once you know
which function is vulnerable.

That result rests on a quiet assumption, which is that the advisory tells you which function. For
Go it does. OSV records it in a structured field, and Rust does the same. For npm, that field is
simply absent, so every vendor rebuilds the mapping in private. I set out to build an open one,
and ran into the assumption instead.

## How often is there a function to name?

<figure class="article-sample">
  <div class="article-grid" id="sample-grid" aria-hidden="true"></div>
  <ul class="article-key">
    <li><span class="article-swatch is-call"></span> 25 name a callable function</li>
    <li><span class="article-swatch is-data"></span> 124 name none</li>
    <li><span class="article-swatch is-unclear"></span> 1 undecidable</li>
  </ul>
  <figcaption>
    Each mark is one advisory. A random sample of 150 drawn from the 7,020 live GHSA npm records
    in the OSV feed, classified on a single question: does this advisory name a function that a
    consumer's own code would call?
  </figcaption>
</figure>

<div class="article-figures">
  <div class="article-figure">
    <span class="article-figure-n">16.7%</span>
    <span class="article-figure-l">name a callable function, the only case reachability can answer</span>
  </div>
  <div class="article-figure">
    <span class="article-figure-n">82.7%</span>
    <span class="article-figure-l">name none, 95% CI 76.7 to 88.7</span>
  </div>
  <div class="article-figure">
    <span class="article-figure-n">0.81</span>
    <span class="article-figure-l">Cohen's kappa between two independent classification rounds</span>
  </div>
</div>

The debate about reachability for JavaScript has been a debate about precision. An
[OpenJS thread](https://github.com/openjs-foundation/security-wg/issues/66) ran for months on how
to name an export unambiguously: packages have zero, one or many entry points, ESM exposes a value
under any number of names, and a package without an `exports` field makes every file reachable.

Those problems are real. They also only arise for the sixth of advisories that name something. For
the other five, no syntax helps, because there is no function in the description to point at.

## What the other five in six look like

<div class="article-specimens">
  <article class="article-specimen">
    <p class="article-specimen-head">
      <span class="article-id">GHSA-35jh-r3h4-6jhm</span>
      <span class="article-pkg">lodash</span>
      <span class="article-verdict is-can">reachability can answer</span>
    </p>
    <blockquote class="article-quote">
      lodash versions prior to 4.17.21 are vulnerable to Command Injection via the
      <mark>template</mark> function.
    </blockquote>
    <p class="article-gloss">A named export. A tool can search your code for calls to it.</p>
  </article>

  <article class="article-specimen">
    <p class="article-specimen-head">
      <span class="article-id">GHSA-hrpp-h998-j3pp</span>
      <span class="article-pkg">qs</span>
      <span class="article-verdict is-cannot">nothing to search for</span>
    </p>
    <blockquote class="article-quote">
      qs before 6.10.3 allows attackers to cause a Node process hang because an
      <mark class="is-no">__proto__</mark> key can be used.
    </blockquote>
    <p class="article-gloss">A key in an object. There is no function called <code>__proto__</code>.</p>
  </article>

  <article class="article-specimen">
    <p class="article-specimen-head">
      <span class="article-id">GHSA-hf5h-hh56-3vrg</span>
      <span class="article-pkg">uws</span>
      <span class="article-verdict is-cannot">nothing to search for</span>
    </p>
    <blockquote class="article-quote">
      Affected versions of uws do not properly handle large websocket messages when
      <mark class="is-no">permessage-deflate</mark> is enabled, which may result in a denial of
      service condition.
    </blockquote>
    <p class="article-gloss">A configuration option. Whether you are affected depends on a setting, not a call.</p>
  </article>

  <article class="article-specimen">
    <p class="article-specimen-head">
      <span class="article-id">GHSA-77q4-m83q-w76v</span>
      <span class="article-pkg">browserify-hmr</span>
      <span class="article-verdict is-cannot">nothing to search for</span>
    </p>
    <blockquote class="article-quote">
      Versions of browserify-hmr prior to 0.4.0 are missing
      <mark class="is-no">origin validation</mark> on the websocket server.
    </blockquote>
    <p class="article-gloss">Runtime behaviour of a service. There is no library API involved at all.</p>
  </article>
</div>

Option keys, query operators, property names, crafted inputs, HTTP headers, and the behaviour of
servers and command line tools with no importable API. Roughly five advisories in six describe one
of these rather than a function you call.

## The failure is silent

A tool that cannot answer could say so. In practice the machinery does something worse. It
searches for a call, finds none, and reports that you are not affected. I know because I built one
and it did exactly that.

<div class="article-failure">
  <h3>A worked example</h3>
  <blockquote class="article-quote">
    <span class="article-src">GHSA-5mrr-rgp6-x4gr, marsdb:</span>
    In the <mark class="is-no">DocumentMatcher</mark> class, selectors on
    <mark class="is-no">$where</mark> clauses are passed to a Function.
  </blockquote>
  <p class="article-gloss">
    My extractor read <code>DocumentMatcher</code> and <code>$where</code> as symbols.
    Linguistically correct, semantically wrong: <code>$where</code> is a key in a query object,
    not something you can call. No call pattern can ever match it.
  </p>
  <p class="article-gloss is-strong">
    Meanwhile, in OWASP Juice Shop, <code>routes/chat.ts</code> line 149:
  </p>
  <pre class="article-pre"><code>db.reviewsCollection.find({ $where: 'this.product == ' + productId })</code></pre>
  <p class="article-gloss">
    Concatenated user input reaching a <code>$where</code> sink. Juice Shop documents a NoSQL
    injection challenge on exactly this code.
  </p>
  <p class="article-verdict-line">
    <span>my tool reported</span>
    <span class="article-stamp">NOT REACHABLE</span>
    <span>and the output was indistinguishable from a win</span>
  </p>
</div>

That is the shape of the problem. A false positive wastes an afternoon. A false negative of this
kind removes a live vulnerability from the queue and looks like the tool working well. Nothing in
the output distinguishes *we checked and you are fine* from *we had nothing to check with*.

## What would fix it

Not a better call graph. The engines are good, and open ones already exist. The gap is in the
advisory data, and it needs two things.

**Symbols where they apply.** Go and Rust already publish them in OSV. Roughly 1,170 npm
advisories could carry the same field today.

**An explicit marker where they do not.** This matters more. An advisory with no function data
currently looks identical to one where no function applies, so every consumer decides for itself
what the absence means, and the convenient reading is that there is nothing to reach. Making that
state nameable is what turns a silent false negative into an honest *cannot determine*.

<div class="article-method">
  <h3>Method and limitations</h3>
  <p>
    150 advisories drawn with a fixed seed from the 7,020 live GHSA npm records in the OSV feed,
    withdrawn records excluded. Each was classified twice, independently, on reshuffled batches.
    Agreement was 92 percent with Cohen's kappa of 0.81.
  </p>
  <ul>
    <li>
      Classification was done by language models reading advisory prose, not by expert
      adjudication. That is why it was run twice, and why every per-advisory call is published
      rather than only the total.
    </li>
    <li>
      Only the first 420 characters of each advisory were read. A longer description might name a
      function the excerpt omits, which would bias the result toward the larger figure.
    </li>
    <li>
      The Juice Shop example was verified by reading the source, not by running the exploit.
    </li>
    <li>
      The first round of classification produced 84.7 percent and was not reliable enough to
      publish: per-batch rates varied from 8 to 18 percent, and two near-identical advisories were
      classified oppositely. The rubric was conflating <em>does this name something callable</em>
      with <em>is calling it sufficient to be exploited</em>. Only the first is a question
      reachability answers.
    </li>
  </ul>
</div>

<footer class="article-endnote">
  <p>
    Sample, both classification rounds, extraction code and 574 proposed symbol records:
    <a href="https://github.com/sonukapoor/npm-vuln-symbols">github.com/sonukapoor/npm-vuln-symbols</a>.
    Everything reproduces from a fixed seed.
  </p>
  <p>
    Related discussion in
    <a href="https://github.com/openjs-foundation/security-wg/issues/66">OpenJS security-wg #66</a>.
  </p>
</footer>

</div>

<script>
  // One mark per advisory in the sample, in the proportions actually measured:
  // 25 naming a callable, 124 naming none, 1 undecidable from the text.
  (function buildSampleGrid() {
    var grid = document.getElementById("sample-grid");
    if (!grid) return;
    var counts = [["is-call", 25], ["is-data", 124], ["is-unclear", 1]];
    var fragment = document.createDocumentFragment();
    counts.forEach(function (entry) {
      for (var i = 0; i < entry[1]; i += 1) {
        var mark = document.createElement("span");
        mark.className = "article-mark " + entry[0];
        fragment.appendChild(mark);
      }
    });
    grid.appendChild(fragment);
  })();
</script>
