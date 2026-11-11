# NVConsult — Google Growth Audit and 10 Visa News Post Plans

Date: 2026-11-11
Scope: live site `https://nvconsult.eu` (WordPress, Elementor, Site Kit) and the legacy `www.nvconsult.eu` host.

---

## 0. Read first: what I could and could not check

* [x] Live site crawled via Firecrawl: homepage, `/guides/`, `/guides/germany-opportunity-card/`, `/countries/germany/`, `robots.txt`, `sitemap_index.xml`, post/category sitemaps.
* [x] Legacy static site in git history (`nvsion _public_html.zip`, commit `9b41caa`) inspected. **It is not the live site.** The repo's static Travisa-based pages are a separate, older build.
* [ ] **Search Console and GA4 data: not accessible.** Frase trial has expired; OpenSEO has no projects; Ahrefs returns "Insufficient plan" for site metrics. I have **no traffic, impression, or ranking numbers**, so this audit is about crawlability, indexing signals, and content, not measured decline.
* [ ] Sandbox cannot reach `nvconsult.eu` directly (curl returns 000). All live checks used Firecrawl.

---

## 1. Growth blockers (evidence-based)

### P0 — fix first

| # | Finding | Evidence | Why it matters |
|---|---|---|---|
| 1 | **`/guides/` hub is `robots: noindex, follow`** | Scraped metadata on `https://nvconsult.eu/guides/` | The Guides hub is the main index for all guide pages. Google is told not to index it. Individual guides are `index, follow`. |
| 2 | **Two hosts, duplicate legacy URLs** | `site:nvconsult.eu visa news` returned `https://www.nvconsult.eu/blog.html` and `https://www.nvconsult.eu/privacy-policy.html` (legacy `.html` URLs on `www`) | Old URLs are still indexed. Need a site-wide 301 from `www` and `*.html` to clean WordPress URLs, plus one canonical host. |
| 3 | **Almost no news/blog content** | `post-sitemap.xml` lists **3 posts**, all dated 6 Nov 2026 (Italy jobs and Decreto Flussi). `category-sitemap.xml` lists only `uncategorized`. No Visa News category exists. | Google and AdSense reviewers see a thin news section. Publishing 10 posts at once does not fix this on its own (see section 3). |
| 4 | **Unverified dates shown as fact on the homepage** | Homepage banner: "Austria opens 16 Nov", "France closes 18 Nov". Dates section lists the same. | My checks found no official source for either date (see section 2). Stating unverified deadlines damages trust and conflicts with your own rule "verify before publication". |

### P1 — fix this month

| # | Finding | Evidence |
|---|---|---|
| 5 | Guide and country pages carry "Verified against official sources" statements | Germany guide: "Checked against official sources on 29 October 2026". Good for E-E-A-T, but I could not confirm the underlying claims for all pages. Keep only what you can re-check. |
| 6 | Homepage is an interactive finder with little crawlable prose | Homepage markdown is mostly UI labels and step text. Google indexes the country and guide pages better than the homepage. Make sure each country page has a plain-text intro and a visible list of routes. |
| 7 | Consent-gated analytics | Cookie banner says GA and Meta Pixel "stay off unless you allow them". Analytics will under-count, so GSC is your only reliable Google source. |
| 8 | No `sitemap` coverage check done | `robots.txt` is correct (Yoast, sitemap declared). I did not verify GSC index coverage, which I cannot access. Check "Pages" report in GSC for "Crawled, currently not indexed" and "Discovered, currently not indexed". |

### Working as intended (no action)
* `robots.txt` allows all crawling and declares the sitemap.
* Country and guide pages checked (`/countries/germany/`, `/guides/germany-opportunity-card/`) are `index, follow`, with canonical-style URLs, Open Graph, and descriptions.
* Structured sitemaps exist for posts, pages, countries, guides, jobs, scholarships, pathways.

---

## 2. Date verification status (used for the post plans)

| Claim | Status | Source checked |
|---|---|---|
| Italy Decreto Flussi 2027: pre-fill 23 Oct to 7 Dec 2026 | Supported by secondary sources; primary circular not opened | Secondary: [Fiscal Focus](https://www.fiscal-focus.it/quotidiano/il-quotidiano/articoli-lavoro/decreto-flussi-2027-domande-precompilate-dal-23-ottobre,3,188605), [ECNews](https://www.ecnews.it/lavoro/mondo-professione/sintesi-ai/flussi-2027-precompilazione-istanze-al-via-dal-23-ottobre/). Official: [lavoro.gov.it](https://www.lavoro.gov.it/priorita/pagine/decreto-flussi-2027-pubblicata-la-circolare-con-le-indicazioni-operative) (not read in full) |
| Italy click days 12 Jan, 9 Feb, 16 Feb, 18 Feb 2027 | Supported by secondary sources; sources disagree on circular date (1 vs 2 Oct 2026) | [Envoy Global](https://www.envoyglobal.com/news-alert/italy-opens-2027-decreto-flussi-work-permit-application-process/), [Quifinanza](https://quifinanza.it/lavoro/decreto-flussi-2027-date-click-day-quote-ingresso-stranieri/1017988/) |
| Austria Summer 2027 applications open 16 Nov 2026 | **NOT VERIFIED.** Only a commercial consultancy gives this window. Universities set their own dates. | [Kadamb Overseas](https://kadamboverseas.com/austria/). Remove from banner until checked against each university. |
| France "closes 18 Nov" (Campus France) | **NOT VERIFIED / likely wrong.** Found 18 Dec 2026 for Campus France Tunisia degree applications, and 20 Nov for ENS Lyon Eiffel. Deadlines depend on country and institution. | [ENS Lyon Eiffel 2027-28](https://www.ens-lyon.fr/en/article/about-us/eiffel-excellence-scholarship-program-application-2027-2028), [Campus France Tunisia via search](https://www.mastere.tn/?p=12790) (secondary). Fix banner. |
| Germany "closes 15 Jan 2027" | **NOT VERIFIED.** Varies by university and programme. | None checked. |
| Czechia "closes 28 Feb 2027" | **NOT VERIFIED.** | None checked. |
| Germany Opportunity Card: €13,092 for 12 months, 6 points | Site states it is checked against Make it in Germany (29 Oct 2026). I did not re-open the source. | [Make it in Germany](https://www.make-it-in-germany.com/en/visa-recognition/opportunity-card/job-search) (listed on the site; re-check before reuse) |
| German minimum wage €14.60 from 1 Jan 2027 | Stated on the Germany page; I did not verify. | [German Customs](https://www.zoll.de/EN/Businesses/Work/Foreign-domiciled-employers-posting/Minimum-conditions-of-employment/Minimum-pay-pursuant-Minimum-Wage-Act/minimum-pay-pursuant-minimum-wage-act_node.html) (listed on the site; re-check) |

**Rule for every post below:** do not publish a date until it is confirmed on an official page you link to, with a "Last verified" date.

---

## 3. AdSense and "post aggressively" — a constraint

* AdSense review looks for original, useful content. **Ten short, similar news posts published in a few days** is the pattern most likely to be rejected as thin or scaled content. The posts would also be the ones carrying the verification risk in section 2.
* **Recommended cadence:** one post every 2–3 days, each 900+ words, each with an official source list, a "Last verified" date, and a link to the matching country page. Ten posts over about four weeks is safer and more useful.
* Put the posts in a **Visa News** category and link them from `/guides/` (after fixing the noindex) and from the country pages.
* Ads need cookie consent to show in the EU/UK. Check that your consent setup supports AdSense before applying.

---

## 4. Ten post plans

Target keyword and search volume: **not validated.** I could not pull keyword data (Ahrefs plan limit, Frase trial expired). Validate each keyword before drafting.

### Post 1 — Italy Decreto Flussi 2027: pre-fill and click day calendar
* **Slug:** `/news/italy-decreto-flussi-2027-calendar/`
* **Angle:** Full calendar: pre-fill from 23 Oct to 7 Dec 2026, reopening 9–13 Dec, click days 12 Jan, 9 Feb, 16 Feb, 18 Feb 2027.
* **Sources to cite:** lavoro.gov.it circular (read it directly first), Ministry of the Interior pages.
* **Status:** Mostly supported. Confirm circular date (1 or 2 Oct 2026) and the reopening window.
* **Internal links:** `/guides/italy-decreto-flussi-2027/`, `/jobs/?country=Italy`

### Post 2 — Which Decreto Flussi click day applies to you
* **Slug:** `/news/italy-click-day-which-category/`
* **Angle:** Map of the four click days to job categories (seasonal agriculture, seasonal tourism, non-seasonal, family care). Warn that only employers can apply.
* **Status:** Category mapping from secondary sources. Verify against the circular before publishing.

### Post 3 — Germany minimum wage rises to €14.60 from 1 Jan 2027
* **Slug:** `/news/germany-minimum-wage-2027/`
* **Angle:** What it means for job seekers and Opportunity Card holders who plan to work part-time (20 h/week limit).
* **Sources to cite:** German Customs / Minimum Wage Act; Destatis.
* **Status:** Needs verification (figure is on the site, not checked by me).

### Post 4 — EU Blue Card Germany: salary thresholds 2026 and what changes for 2027
* **Slug:** `/news/germany-blue-card-thresholds/`
* **Angle:** €50,700 standard threshold and €45,934.20 for shortage occupations and recent graduates (2026 figures as on the site). Say the 2027 figure is pending until published.
* **Sources to cite:** Make it in Germany; Federal Foreign Office.
* **Status:** 2026 figures need re-checking. Do not state a 2027 figure until officially published.

### Post 5 — Germany Opportunity Card: 6-point check after the 2026 rules
* **Slug:** `/news/germany-opportunity-card-points-check/`
* **Angle:** News hook is the points check and proof-of-funds amount. Use a worked example with the official calculator link.
* **Sources to cite:** Make it in Germany self-check; Consular Services Portal (digital.diplo.de); §20a AufenthG.
* **Status:** Core content exists in the guide. Post should be a dated update, not a copy.
* **Internal links:** `/guides/germany-opportunity-card/`, `/check-your-eligibility/`

### Post 6 — Austria 2027 university applications: how to find the real deadline
* **Slug:** `/news/austria-university-deadlines-2027/`
* **Angle:** Austria has no single national application window. Show how to check each university. Name the commercial 16 Nov date only as an unverified claim, or drop it.
* **Sources to cite:** Individual university admission pages; the Austrian residence permit guidance from the BMI/relevant consulate.
* **Status:** **Blocked.** Do not publish a 16 Nov date until a university or official page confirms it. Remove the homepage banner claim now.

### Post 7 — France 2027: Campus France and Eiffel scholarship deadlines (verify by institution)
* **Slug:** `/news/france-study-2027-deadlines/`
* **Angle:** Campus France deadlines vary by country and institution. Use the Eiffel scholarship as a verifiable example: ENS Lyon 20 Nov 2026, University of Poitiers 23 Nov 2026 (per its page), Toulouse 15 Nov pre-application.
* **Sources to cite:** Each university's Eiffel page; Campus France official site for your country.
* **Status:** Eiffel dates supported by institution pages in search results. The general "18 Nov" banner claim is **not** supported. Fix it.

### Post 8 — Czech work permit: how to check an employer before you pay anyone
* **Slug:** `/news/czech-work-permit-scam-warning/`
* **Angle:** News hook: scam "work permit" offers. Explain the real Employee Card process and the six checks. Link the existing guide.
* **Sources to cite:** Czech Ministry of Interior / Labour Office official pages (to be confirmed).
* **Status:** Needs official Czech source before publishing.
* **Internal links:** `/guides/czech-work-permit-check/`

### Post 9 — Czechia 2027/28 study and residence deadlines (check by university)
* **Slug:** `/news/czechia-study-deadlines-2027/`
* **Angle:** Replace the 28 Feb 2027 banner claim with a checklist of how each Czech public university sets deadlines.
* **Status:** **Blocked.** No source checked for 28 Feb. Verify with 2–3 named universities before drafting.

### Post 10 — Germany Summer 2027 study deadlines: how to check your university
* **Slug:** `/news/germany-study-deadlines-summer-2027/`
* **Angle:** Germany has no national uni deadline. "15 Jan" depends on the university and programme. Show a short table of how to check, with examples only where confirmed.
* **Status:** **Blocked** for the 15 Jan claim. Build the post around the method first.
* **Internal links:** `/countries/germany/`, `/pathways/study/#germany`

---

## 5. Immediate action list

* [ ] Fix `/guides/` noindex (WordPress SEO plugin, Reading settings, or the template). Re-check with a fresh scrape.
* [ ] Remove or correct the unverified homepage banner dates: Austria 16 Nov, France 18 Nov, Germany 15 Jan, Czechia 28 Feb.
* [ ] Set a site-wide 301 from `www.nvconsult.eu/*` and from legacy `*.html` URLs to the WordPress URLs. Choose one canonical host.
* [ ] Create a Visa News category and draft Post 1 first (best-supported).
* [ ] Connect Google Search Console for `nvconsult.eu` (domain property) and export 90 days of queries and pages. Share the CSV so I can rank posts by real demand.
* [ ] Add a "Last verified" date and an official-sources block to every news post.

---

## 6. Clarifying questions (needed before drafting)

* [ ] Do you have WordPress admin or REST API access (username and application password, stored outside the repo), so posts can be created as drafts?
* [ ] Can you export Search Console data (90 days, queries and pages) or grant access to OpenSEO or Ahrefs for `nvconsult.eu`?
* [ ] Should the 10 posts be published as drafts for your review, or go live on a schedule (recommended: one every 2–3 days)?
* [ ] Which country should lead the news section: Italy and Germany (best-verified now) or the full list of 15 countries?

---

_Limits: this report used only live pages, the legacy zip in git history, and secondary web search results. No Search Console, GA4, or keyword volume data was available. Every date marked "not verified" must be confirmed on an official source before publication. This is education and application guidance, not legal advice._
