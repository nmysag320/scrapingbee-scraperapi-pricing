# scrapingbee api: credit costs, all plan prices explained, and how ScraperAPI compares

Most people searching scrapingbee api are evaluating ScrapingBee as their web scraping API: what it can actually do, how its credit billing works, and what a month really costs. The short answers: it returns rendered HTML or structured data from a single API call, entry pricing starts at $19/month for 75,000 credits, and one request can cost anywhere from 1 to 75 credits depending on how hard the target site fights back. That last number is the one most comparison posts skip, and it decides your real cost per page. This article walks through ScrapingBee's billing mechanics and every plan on its pricing page, then covers ScraperAPI — the tool that shows up next to it in almost every related search — because the two bill quite differently, and the difference changes which one is cheaper for your specific targets.

## Quick answer: which one should you pick

> - **ScrapingBee**: entry plan at $19/mo for 75,000 credits, 1,000 free credits on signup with no credit card, cancel anytime. Best fit if most of your targets are ordinary sites without heavy anti-bot protection.
> - **ScraperAPI**: free plan with 1,000 credits and 5 concurrent threads, plus a 7-day trial with 5,000 credits. Publishes per-site credit costs (Amazon 5, Google 25, LinkedIn 30), which makes budgeting predictable. Best fit if you scrape Amazon, Google, or LinkedIn at scale and want parsed JSON back.
> - If structured e-commerce and SERP data is your main use case, [👉 check ScraperAPI's full plan list and start the free trial](https://www.scraperapi.com/pricing/?fp_ref=coupons).

## What ScrapingBee's API actually does

You hand it a URL, it hands back the page. Every ScrapingBee plan includes JavaScript rendering through headless Chrome (with wait-for-selector, browser events, custom viewport and headers, and screenshots for debugging), rotating and premium proxies, stealth proxies for the hardest anti-bot environments, country-level geotargeting, screenshots, extraction rules, a Google search API, and a set of dedicated scraping APIs. What changes between plans is the credit pool, concurrency, and the support tier.

ScrapingBee advertises over 200 million IPs and claims a 99% success rate based on 100+ reviews from more than 4,500 developers. On the compliance side it states SOC 2 Type 2 certification covering GDPR, infrastructure security, access control, and endpoint security.

Integration is straightforward: official SDKs for Python, Node, Go, Java, PHP, Ruby, and a CLI, with the Python and Node packages on PyPI and npm. API methods retry automatically on 5XX responses. Beyond raw HTML, you can define extraction rules in JSON or describe what you want in natural language with AI Query and get structured JSON or Markdown back. There's also Fast Search for real-time SERP data, advertised at under one second per request, and the CLI plugs into AI coding tools like ChatGPT, Claude, Cursor, and Gemini.

## ScrapingBee's five paid plans

Here is the full set of plans currently shown on ScrapingBee's pricing page:

| Plan | Monthly price | API credits/mo | Concurrent requests |
| --- | --- | --- | --- |
| Hobby | $19 | 75,000 | 25 |
| Freelance | $49 | 250,000 | 50 |
| Startup | $99 | 1,000,000 | 100 |
| Business | $249 | 3,000,000 | 200 |
| Business+ | $599 | 8,000,000 | 400 |

Three things the table doesn't show. First, all prices exclude VAT, and the pricing page currently only lists monthly billing — no annual discount is displayed there. Second, new accounts get 1,000 free credits with no credit card required, and the page states you can cancel anytime, no questions asked. Third, priority email support, a dedicated account manager, and team management only kick in from Business upward; below that you get standard support.

## Where ScrapingBee's credits actually go

This is the part most roundup articles gloss over, and it's where budgets break. ScrapingBee's credits are not "one credit per page" — consumption depends on the mode:

| HTML API request | Credits |
| --- | --- |
| Classic proxy, no JavaScript | 1 |
| Classic proxy, JavaScript rendering (default) | 5 |
| Premium proxy, no JavaScript | 10 |
| Stealth mode (hardest targets), top of the range | up to 75 |

JavaScript rendering is on by default, so the "default request" already costs 5 credits unless you turn it off. The gap between modes is enormous: the same $49 Freelance plan buys 250,000 plain requests, or roughly 3,333 stealth-mode ones. That's a 75x difference on one subscription.

Two billing details only visible in the docs: ScrapingBee counts a request as successful — and bills it — when the server returns 200, 404, or 410. Blocks and timeouts cost nothing. So if your URL list includes delisted products, every dead link still takes its credits. And you don't fully choose your mode: the usual flow is start cheap, get blocked, step up to premium or stealth until the page comes back. The target site effectively picks your price, which is why you should budget against real per-page cost rather than the credit count on the pricing page.

## Why ScraperAPI keeps coming up in the same searches

ScrapingBee comparisons almost always surface ScraperAPI, and the reason is worth understanding: it's also a credit-based scraping API, but it prices by target-site difficulty instead of by request mode. Per its official documentation, a standard page costs 1 credit, Amazon costs 5, Google and Bing (including subdomains) cost 25, LinkedIn costs 30, and sites behind Cloudflare, Datadome, or PerimeterX protection add 10 credits per request when bypassed. You can look up the exact credit cost of any URL with the Domain Cost Estimator in the dashboard, and set a `max_cost` parameter so a single scrape can't blow past your limit. You know the price of a page before you fetch it.

Failed requests get their credits refunded, which matters a lot at scale. On the product side, ScraperAPI runs a blended pool advertised at 40 million-plus IPs across residential, datacenter, and mobile, in over 50 countries. Its structured data endpoints return parsed JSON directly — Amazon Search, Google Search, Google Shopping, Walmart Search, eBay Product and more — so you skip writing and maintaining HTML selectors entirely. Other confirmed parameters: `render` for JS rendering, `country_code` for geotargeting, `device_type` for desktop or mobile, `autoparse` (off by default, works on supported domains), `session_number` for sticky sessions (a session expires 15 minutes after last use), an async scraper for million-request batches without holding connections open, and DataPipeline, a low-code layer for scheduling jobs and pushing results to a webhook. Every plan includes JS rendering, premium proxies, automatic retries, unlimited bandwidth, CAPTCHA handling, and a 99.9% uptime guarantee.

## ScraperAPI's full plan list

All plans on the official pricing page, monthly and annual-equivalent prices:

| Plan | Monthly | Annual (per mo) | Credits/mo | Threads | Get started |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 | 5 | [ Sign up free](https://www.scraperapi.com/?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 | [ See Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [ See Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [ See Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [ See Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [ See Professional](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [ See Advanced](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | [ Contact sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Annual billing is 10% off the monthly rate across the board. The 7-day trial with 5,000 credits needs no credit card, and after it expires your account drops to the free 1,000-credit plan. Credits don't have to be tested blind, either — [👉 start the 5,000-credit trial and run your real URLs through the Domain Cost Estimator](https://www.scraperapi.com/signup?fp_ref=coupons) before committing to a tier.

Limits worth knowing before you pick a tier, because they're easy to miss:

- **Geotargeting**: Hobby and Startup are US and EU only. The full country list unlocks at Business.
- **Analytics history**: 30 days on Hobby and Startup, unlimited from Business up.
- **Concurrency overflow**: exceeding your thread limit returns a 429 and asks you to retry within your cap — requests are refused, not queued, and it costs nothing extra.
- **Running out of credits**: scraping pauses until renewal by default. Hobby through Professional can opt into auto-upgrade to the next plan; Scaling and above can use pay-as-you-go at a fixed per-credit rate up to a monthly cap you set. Annual plans can renew early for a fresh batch of credits.
- **Support**: plans below Scaling get priority email support; Scaling and above add a dedicated support team and Slack support.

## What the real cost gap looks like

Take a common scenario: 20,000 Amazon product pages a month.

On ScraperAPI's Hobby plan, Amazon costs 5 credits per page, so 20,000 pages consume exactly the plan's 100,000 credits — about $2.45 per 1,000 pages, and the number is knowable in advance. The same plan's 100,000 credits also cover around 4,000 Google queries at 25 credits each.

On ScrapingBee, that same Amazon job needs JavaScript rendering plus premium or stealth proxies, so credits multiply per the table above and consumption is harder to forecast upfront. Where ScrapingBee wins is plain requests on unprotected sites: the $19 Hobby plan's 75,000 credits at 1 credit per plain request works out to roughly $0.25 per 1,000 pages, and at $49 the Freelance plan carries 250,000 credits — two and a half times ScraperAPI's Hobby pool.

The general pattern: the harder your targets, the more ScraperAPI's published per-site pricing helps you plan, and the more ScrapingBee's mode-based multiplier can inflate costs. The easier your targets, the more ScrapingBee's low entry price and large credit pools matter.

## FAQ

**Does ScrapingBee offer annual billing discounts?** Its pricing page currently lists monthly prices only, stated as excluding VAT. No annual discount is displayed there, so budget on monthly pricing.

**What are ScrapingBee's credit gotchas?** Two main ones: 404 and 410 responses still count as successful and bill credits, and stealth mode costs up to 75 credits per request. Test with your real URL list before sizing a plan. Blocked requests and timeouts, on the other hand, are free.

**Does ScraperAPI have a free tier?** Yes — 1,000 credits with 5 concurrent threads, no card required, plus a 7-day trial with 5,000 credits for new accounts. If you need more test credits, support can grant them.

**How does ScraperAPI's credit math work on protected sites?** A Cloudflare- or Datadome-protected site adds 10 credits on top of the base cost. Combined with `render=true` at 10 credits, a single scrape of a protected page can run 20+ credits, so check the Domain Cost Estimator first.

## Picking between them

Match the tool to your targets and budget:

- Mostly small, unprotected sites, high volume, price-sensitive → ScrapingBee's $19 entry is the lower floor of the two, with 1,000 free credits to validate with first.
- Heavy on Amazon, Google, or LinkedIn scraping, and you want structured JSON plus predictable per-page costs → ScraperAPI is the more honest tool about what a page will cost you.
- Split between both → run your target domains through ScraperAPI's Domain Cost Estimator, convert the monthly consumption, and compare it against ScrapingBee's credits at the mode your targets force you into. Five minutes of math beats ten more review articles. [👉 Compare both side by side on ScraperAPI's pricing page](https://www.scraperapi.com/pricing/?fp_ref=coupons) and let the estimator settle it.
