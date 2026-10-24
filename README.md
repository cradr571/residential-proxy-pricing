# best residential proxies: What Providers Actually Charge, When a Scraping API Makes More Sense, and ScraperAPI's Real Cost Per Page

Most "best residential proxies" comparisons rank the same ten providers by per-GB price and call it a day. That's useful if you've already decided to manage proxies yourself. But there's a fork in the road those rankings rarely address: if your end goal is scraped data from Amazon, Google, or e-commerce sites, a scraping API that handles rotation, retries, and CAPTCHAs for you can beat a raw proxy plan on both cost and setup time. This guide covers both paths — verified 2026 per-GB prices from the major residential providers, plus a full breakdown of ScraperAPI, the API-first alternative, including its credit system that most reviews don't calculate honestly.

> **Quick verdict:** If you're a developer scraping standard e-commerce or search targets at 20,000–200,000 pages a month, ScraperAPI's Hobby plan ($49/month, 100,000 credits, 20 concurrent threads) is the simplest entry point, and a 7-day trial with 5,000 credits lets you test your actual target URLs before paying anything. 👉 [Start the 7-day free trial and check current plan prices](https://www.scraperapi.com/signup?fp_ref=coupons)

If you need raw proxy endpoints to plug into your own browser stack, third-party tools, or account-management workflows, skip to the provider price comparison below — a scraping API will fight you the whole way.

## Two paths to the same goal: proxy lists vs. scraping APIs

The choice between providers comes down to what you actually want to buy. Residential proxy providers sell IP access: you get endpoints (or gateway URLs), pick a rotation and session policy, and handle everything else — retries, headers, CAPTCHAs, parsing — in your own code. A scraping API like ScraperAPI sells the finished result. You send a URL plus an API key, and the service handles proxy rotation, CAPTCHA solving, optional JavaScript rendering, and retries on its side, returning HTML or, for some sites, parsed JSON.

ScraperAPI runs a blended pool it advertises as more than 40 million IPs across residential, datacenter, and mobile networks, spanning over 50 countries. You control behavior through parameters: `country_code` for geo-targeting, `render=true` for a headless browser, `premium=true` or `ultra_premium=true` for harder targets, and `session_number` to hold the same IP across a request sequence. There are also structured data endpoints for Amazon product and search pages, Google Search and Shopping, and Walmart that return JSON instead of raw HTML, so a site redesign doesn't break your parser.

The trade-off is control. All traffic flows through a single endpoint; there's no dashboard for picking specific IPs, ASNs, or subnets. You trust the rotation logic or you don't use the service. Proxy providers give you that granular control — at the price of building and maintaining the retry and unblocking logic yourself.

## What residential proxy providers charge right now

Per-GB pricing dominates this market, and the spread is wide: from $6/GB at low volumes down to $0.49/GB at scale. Proxyway's benchmark testing — millions of connection requests run against unfiltered pools — gives current success rates and response times alongside standardized pricing at different volume tiers:

| Provider | 5GB tier | 100GB tier | 1TB tier | Success rate (test) | Advertised pool |
| --- | --- | --- | --- | --- | --- |
| Bright Data | $4 | $4 | $2.50 | – | 400M+ IPs |
| Oxylabs | $6 | $4.50 | $2.50 | 99.93% / 0.60s | 175M+ IPs |
| Decodo (ex-Smartproxy) | $3.75 | $2.75 | $2 | 99.92% / 0.53s | 125M+ IPs |
| Webshare | $3.50 | $2.25 | $1.50 | 99.28% / 0.86s | 80M+ IPs |
| SOAX | – | $2.42 | $1.22 | 99.78% / 0.89s | 195+ locations, city/ISP targeting |
| Evomi | – | $0.49 | $0.49 | 99.58% / 0.79s | flat rate from 50GB |
| DataImpulse | – | $1 | $1 | 99.74% / 0.97s | budget tier |
| IPRoyal | $5.95 | – | – | 96.11% / 1.24s | plans up to 50GB |

A few things the numbers hide. The market average for a 100GB commitment sits around $3–4/GB, so Evomi's flat $0.49 and DataImpulse's $1 are genuine outliers rather than the norm. SOAX prices by region tier — its Tier 1 (US, Western Europe) costs about 2.5 times its third tier — so the headline $2.42/GB only applies to certain geographies. And entry prices matter less than volume pricing if your usage is predictable: Oxylabs drops from $6 to $2.50/GB between the 5GB and 1TB tiers.

Free access exists, but it's modest. Webshare offers the most usable free tier — 10 proxies and 1GB per month, no credit card. Decodo gives 100MB of residential mobile proxy traffic as a trial with a 14-day refund window; Oxylabs offers $5 in credit toward any product.

These providers make sense when you need what a scraping API doesn't offer: SOCKS5 support (several offer it alongside HTTP/HTTPS), sessions lasting up to 24 hours or even 7 days, ISP or ASN-level targeting, or proxies for tools outside your own code. Oxylabs, for instance, supports SOCKS5 with UDP and MASQUE, and Decodo sessions can run a full day.

## ScraperAPI: full plan and pricing breakdown

ScraperAPI prices by API credits instead of bandwidth. Every paid plan includes unlimited bandwidth, JS rendering, premium residential and mobile IPs, CAPTCHA and anti-bot handling, automatic retries, custom session support, and a 99.9% uptime guarantee — the plans differ in credit volume, concurrency, and geo-targeting depth. Here's the full lineup from the official pricing page:

| Plan | Monthly price | Credits | Concurrent requests | Targeting |
| --- | --- | --- | --- | --- |
| Hobby | $49 | 100,000 | 20 | US & EU only |
| Startup | $149 | 1,000,000 | 50 | US & EU only |
| Business | $299 | 3,000,000 | 100 | Country-level |
| Scaling (most popular) | $475 | 5,000,000 | 200 | Country-level |
| Professional | $975 | 10,500,000 | 300 | Country-level |
| Advanced | $1,975 | 21,500,000 | 500 | Country-level |
| Enterprise | Custom | 22,000,000+ | 500+ | Country-level |

👉 [See all current plan prices and annual discounts on ScraperAPI's pricing page](https://www.scraperapi.com/pricing?fp_ref=coupons)

Annual billing takes 10% off every plan — Hobby drops to $44.10/month, Startup to $134.10, Business to $269.10, Scaling to $427.50, Professional to $877.50, and Advanced to $1,777.50. Two things worth knowing before you pick a tier:

- **Analytics history differs more than you'd expect.** Hobby and Startup plans keep 30 days of dashboard analytics; Business and above get unlimited history. For ongoing monitoring projects, that alone can justify the jump to Business.
- **Geo-targeting widens at Business.** The two cheapest plans cover US and EU locations only. If you need to target Japan, Brazil, or other markets at the country level, you're at $299/month minimum.

You can test everything without a credit card: a 7-day trial comes with 5,000 API credits, and there's also a permanent free plan with 1,000 credits (capped at 5 concurrent connections) if you need more testing quota than the trial allows.

## The real cost of a credit: what the pricing page doesn't foreground

Here's the part most reviews gloss over, and it changes your budget math entirely. One credit equals one standard page request — but plenty of pages aren't standard. ScraperAPI's own documentation lays out the multiplier: a standard page costs 1 credit, Amazon costs 5, Google and Bing (including their subdomains) cost 25, and LinkedIn costs 30. Requests that bypass protection systems like Cloudflare, Datadome, or PerimeterX add 10 credits each, and enabling JS rendering pushes a request to roughly 10 credits on its own.

Stack those on a hard target and the effective cost per successful page can reach 20–30 times the plan's headline per-credit price. One third-party assessment ran the numbers on Amazon search pages with JS rendering enabled: a Startup plan's 1,000,000 credits might cover only 40,000–100,000 actual pages, not a million.

Three official tools keep this manageable:

1. **Domain Cost Estimator** — in the dashboard, it shows the exact credit cost for any URL before you run it at scale.
2. **`max_cost` parameter** — caps how many credits any single scrape can consume, so a surprise render-plus-bypass chain can't drain your account.
3. **Auto-upgrade and pay-as-you-go** — by default, scraping pauses when credits run out. Auto-upgrade (opt-in, available on Hobby through Professional) bumps you to the next plan automatically; pay-as-you-go (Scaling and above) continues at a fixed per-credit rate up to a monthly cap you set.

Budget against your real per-page cost, measured with the estimator, rather than the credit count on the pricing page. A cheap-looking plan on hard targets costs more than an expensive-looking plan on easy ones.

## Limits you'll only find in the docs

Concurrency overages get rejected, not queued. Exceed your plan's thread limit — 20 on Hobby, up to 500 on Advanced — and ScraperAPI returns a 429 asking you to retry within your quota. Nothing bills extra, but nothing waits either, so bursts need client-side throttling.

Sessions last about an hour. Custom session support holds an IP across a request sequence, but the stickiness is designed for single scrape jobs. If you need the same IP for days — ad verification, long-running account workflows — a dedicated residential or mobile provider with 24-hour-plus sessions fits better.

Support thins out at the bottom. Hobby and Startup include email and ticket support only; no live chat, no phone. Live-chat and priority support arrive on the higher tiers. For a solo developer that's usually fine; for a production pipeline that breaks at 2am when a target changes its anti-bot rules, it's worth factoring in.

One independent test put ScraperAPI's success rate on the most heavily protected sites around 62–64% — behind providers specializing in those targets. On standard e-commerce and search pages without heavy bot management, the default pool clears most requests without premium add-ons, which is exactly the profile the Hobby and Startup plans are built for.

👉 [Open the free trial and run the Domain Cost Estimator on your actual targets](https://www.scraperapi.com/signup?fp_ref=coupons)

## Who should pick a proxy provider instead

Raw residential proxies win in four specific situations. If your targets are LinkedIn, Instagram, or heavily protected e-commerce at real volume, a bandwidth-billed residential plan from Oxylabs or Decodo will usually cost less than paying ScraperAPI's premium credit multipliers on every request. If you need sessions longer than an hour, providers with 24-hour to 7-day session limits exist for exactly that. If you want to plug proxies into someone else's software — a botting tool, a browser stack, an antidetect setup — you need raw endpoints, which an API can't give you. And if you need protocol flexibility like SOCKS5 with UDP, most major providers support it while ScraperAPI's endpoint is HTTP-based.

The reverse is also true. If you're building a price monitor, SERP tracker, or lead-gen scraper in your own code, a scraping API replaces a meaningful chunk of engineering — rotation logic, retry queues, CAPTCHA handling — that would otherwise eat your development time. For many solo developers, that's worth more than a dollar or two per GB.

## FAQ

**How many pages does ScraperAPI's Hobby plan actually cover?**
It depends entirely on the target. 100,000 credits covers 100,000 standard pages, 20,000 Amazon pages (5 credits each), or about 4,000 Google pages (25 credits each). JS rendering and bot-protection bypasses multiply costs further. Run the Domain Cost Estimator on your URLs before committing.

**Is there a free option?**
Yes. A permanent free plan gives 1,000 credits with 5 concurrent connections, and a 7-day trial provides 5,000 credits without requiring a credit card. Either is enough to test real targets against the estimator before paying.

**What happens when I run out of credits?**
Scraping pauses until your credits renew. You can opt into auto-upgrade (Hobby through Professional), which moves you to the next plan automatically, or pay-as-you-go (Scaling and above), which continues at a fixed rate up to a cap you set. Annual plans can also renew early for a fresh batch of credits.

**Can I use ScraperAPI as a regular proxy in other tools?**
No. It's an HTTP API endpoint you call from code, with no proxy-list output, no SOCKS5, and no way to select specific IPs or subnets. Tools that expect proxy credentials won't work with it.

## Final decision, by situation

- **Building a scraper for Amazon, Google, or standard e-commerce in your own code, under ~200k pages/month** → ScraperAPI Hobby at $49/month, tested first with the free 5,000-credit trial.
- **Same job but scaling past 3 million credits or needing country-level targeting outside US/EU** → Business at $299/month, and turn auto-upgrade on so a traffic spike doesn't pause your pipeline.
- **Hard targets (LinkedIn-scale protection), long sessions, SOCKS5, or proxy endpoints for external tools** → a residential provider billed per GB; Oxylabs and Decodo lead on measured performance, Evomi and DataImpulse on price.
- **Annual billing** saves 10% on any ScraperAPI plan — worth it once you've confirmed your monthly volume is stable.

One last check before you commit anywhere: run two or three of your real target URLs through the trial, note the per-page credit cost, and multiply by your monthly volume. That number, more than any pricing table, tells you which plan — and which provider type — you actually need. 👉 [Check ScraperAPI's current plans and start the free trial](https://www.scraperapi.com/?fp_ref=coupons)
