# La Sparkle — SEO and AIO Guidelines

This document outlines the Search Engine Optimization (SEO) and Artificial Intelligence Optimization (AIO) patterns established for the La Sparkle Aesthetic & Wellness Clinic codebase. Maintain these patterns during any edits or additions.

---

## 1. Search Engine Optimization (SEO) Patterns

All pages in this repository must implement the following local, technical, and semantic SEO strategies:

### A. Local / Geo SEO
To capture local searches (Bhuj, Gandhidham, Kutch), always keep the local meta headers updated and accurate:
* **Region & Place:** `<meta name="geo.region" content="IN-GJ" />` and `<meta name="geo.placename" content="Bhuj & Gandhidham, Kutch, Gujarat" />`
* **Geo Position & ICBM:** Specify exact latitude and longitude:
  ```html
  <meta name="geo.position" content="23.0796;70.1336" />
  <meta name="ICBM" content="23.0796, 70.1336" />
  ```

### B. Structured Data (JSON-LD Graph)
Ensure the JSON-LD schemas validate correctly and connect matching entity nodes:
* **Entity Graphing:** Use `@graph` arrays to map relationships. Specifically:
  - The main Organization `https://lasparkle.in/#org` representing the clinic brand.
  - Separate branches as `MedicalClinic` / `HealthAndBeautyBusiness` nodes (e.g., `https://lasparkle.in/#clinic-bhuj`, `https://lasparkle.in/#clinic-gandhidham`).
  - Explicitly link branches to the organization using `"branchOf": { "@id": "https://lasparkle.in/#org" }`.
* **Offers & Procedures:** Update Organization `"makesOffer"` whenever new treatments are added.
* **FAQ Schema:** Maintain the `FAQPage` schema parallel to any questions modified/added in the visible FAQ accordion section.

### C. Meta & Open Graph Tags
Maintain matching page metadata across all standard, Open Graph, and Twitter channels:
* Keep title structures descriptive and keyword-rich: `La Sparkle Aesthetic & Wellness Clinic | Skin, Laser, HIFU & Hair Clinic in Bhuj & Gandhidham, Kutch`.
* Keep the canonical link tags pointing to the secure base URL: `<link rel="canonical" href="https://lasparkle.in/" />`.

---

## 2. Artificial Intelligence Optimization (AIO) Patterns

AIO ensures search engines powered by LLMs (e.g., Google Gemini, ChatGPT Search, Perplexity) crawl, comprehend, and prioritize the site's content.

### A. The `llms.txt` Interface
A plain text `llms.txt` file must be maintained at the workspace root to serve as a clean, high-density reference sheet for AI crawlers and developer tools:
* Keep a structured markdown format.
* Include summaries of the founder (Dr. Nidhi Thacker), qualifications, physical branch addresses, primary booking coordinates (WhatsApp links), and treatment offerings.
* Whenever a location details or phone number changes in `index.html`, **always** update the corresponding information in `llms.txt`.

### B. Inclusive Bots Policy (`robots.txt`)
Explicitly authorize AI and LLM user-agents to crawl the full site. Maintain standard search accessibility plus explicit permissions:
```
# AI / LLM crawlers — explicitly welcomed for visibility
User-agent: GPTBot
Allow: /
User-agent: ClaudeBot
Allow: /
User-agent: PerplexityBot
Allow: /
User-agent: Google-Extended
Allow: /
```

### C. Clean DOM Structure & Accessibility (A11y)
AI user-agents navigate HTML structurally. Ensure:
* Single high-level `<h1>` representing the primary keyword goal.
* Sequential and nested heading hierarchy (`h2` for key sections, `h3` for cards/questions).
* Fully accessible skip links (`.skip`) and descriptive text labels on links or buttons.
* Inline descriptive `alt` attributes on images describing the scene (e.g. `alt="Dr. Nidhi Thacker with the advanced VENUS energy-based device"`).
