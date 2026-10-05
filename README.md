# shifter review: what the ex-Microleaves proxy network actually costs, where its coverage thins out, and the pay-as-you-go option worth testing first

Type "shifter review" into Google and you get two completely different products: sim-racing gear shifters, and a proxy network called Shifter. If you're here for the Logitech or MOZA kind, this isn't that article. What follows is about the proxy provider at shifter.io — the company that spent a decade as Microleaves before rebranding — and whether its monthly plans are worth committing to when pay-as-you-go pricing now starts at a dollar a gigabyte.

That last part matters. Shifter's pitch has always been pool size: 205M+ residential IPs across 195+ countries. The catch is that pool size is an advertised figure, not a live one, and the network only moved to bandwidth-based pricing relatively recently. So the honest question isn't "is Shifter good" — it's "which parts of Shifter hold up under a real workload, and when does a cheaper metered provider do the same job."

## What Shifter is, and what changed recently

Shifter has been selling rotating residential proxies since 2012, which makes it one of the older backconnect providers still operating. Its history is worth knowing because a lot of reviews online describe a product that no longer exists — the old Shifter sold unmetered, port-based plans, which meant you bought access to a set of ports and used as much traffic as you could push through them.

In May 2026 the company replaced that with a gateway model: you buy a bandwidth allocation, route through a rotating gateway, and pay for the data you actually move. No port limits, no per-request charges, unlimited concurrent connections. If you've read a Shifter review that talks about port counts and per-port pricing, it's describing the old system.

The current product line is straightforward:

- **Rotating residential proxies** — 205M+ advertised IPs, 195+ countries, city-level targeting, per-request rotation plus sticky sessions, HTTP(S) and SOCKS5.
- **Two cheaper pools** — a "Country Geo" pool and a "Non-Geo" pool running on a separate 31M+ IP network with the same rotation and protocols. No city targeting on the first, no targeting at all on the second.
- **Static residential / ISP proxies** — a separate product line that third-party directories price per IP rather than per GB.

No free trial. Every plan carries a 3-day money-back guarantee, which is the closest thing to a test run you'll get.

## Shifter pricing: a real ladder, plus heavy promotional discounts

Here's Shifter's published standard rate card for the Full Geo rotating residential pool, straight from its documentation:

| Plan | Bandwidth | Standard monthly price | Per GB |
| --- | --- | --- | --- |
| Spark | 5 GB | $25 | $5.00 |
| Launch | 10 GB | $50 | $5.00 |
| Boost | 20 GB | $80 | $4.00 |
| Surge | 32 GB | $128 | $4.00 |
| Starter | 50 GB | $175 | $3.50 |
| Basic | 100 GB | $300 | $3.00 |
| Business | 200 GB | $500 | $2.50 |
| Growth | 400 GB | $800 | $2.00 |
| Scale | 800 GB | $1,280 | $1.60 |
| Advanced | 2 TB | $2,800 | $1.40 |
| Pro | 6 TB | $7,200 | $1.20 |
| Max | 10 TB | $10,000 | $1.00 |

Those are list rates. What you'll actually be quoted on the pricing page right now looks very different, because Shifter runs standing discounts in the 63%–71% range. Its own comparison pages quote $10 for a 5 GB entry pack ($2.00/GB), $100 for 100 GB, and $149 for a 200 GB month — which works out to roughly $1.00/GB at the 50 GB tier and $0.75/GB at 200 GB. The Country Geo and Non-Geo pools go lower still, with headline entry rates of $0.48/GB and $0.10/GB respectively.

> Two numbers for the same plan on the same website is a normal thing in proxy marketing, but it's worth doing the maths on the checkout total rather than the "from" rate before you commit to a monthly allocation.

The shape of the ladder is the real information here. Below 200 GB a month, Shifter is expensive relative to the market — $3.50/GB for the 50 GB plan even after the discount math is not competitive with metered providers. The economics only start working at 200 GB and above, where the price per GB falls into the $0.75–$1.00 range.

## Where Shifter's numbers get softer

The 205M+ IP figure is Shifter's own marketing number, and it's the number that gets repeated in most comparison articles. Independent sampling tells a different story. ProxyLook's directory entry describes Shifter as advertising 205M+ residential IPs with roughly 235K independently sampled, and rates the provider 3.8 out of 5, with a 6.8 out of 10 trust score, a 98.43% success rate, and an average response of 880 ms.

That's not a disaster — 98.43% is a workable success rate, and 880 ms is faster than plenty of residential networks. But it does mean the "205M IPs" headline is doing more work in the sales pitch than it can support in production. Your crawl only ever sees the addresses that are online at the moment your request fires.

Directory "starting price" figures for Shifter are also a mess. ProxyLook lists an entry of $99.98/GB, Caproxy quotes from $0.60/GB, and other sites cite $0.30/GB. When a directory's entry price varies by a factor of 300, it's telling you the directories are recording different SKUs — static residential, rotating, or legacy plans. Treat the official ladder as the only price list worth planning against.

One more thing worth knowing if you're evaluating Shifter for the first time: it's a monthly commitment, not a wallet. Overages roll onto pay-as-you-go pricing from your account balance rather than forcing a mid-month upgrade, which is sensible. But the entry point is a subscription, and unused allocation doesn't get the "never expires" treatment that has become the standard selling point elsewhere in this market.

## What Shifter genuinely does well

Strip out the marketing and a few things stand out.

City-level targeting across 195+ countries on the main pool is genuinely useful if your work is local — scraping store-level pricing, checking regional ad placements, or reading SERPs as a specific city. Unlimited concurrency with no port caps removes a headache that used to define this provider. And Shifter publishes its own benchmark methodology, including the countries where a competitor beat it, which is more than most proxy vendors do.

The rest is standard: SOCKS5 and HTTP(S), sticky or rotating sessions, API access, and 24/7 support from the Starter tier up.

## The pay-as-you-go alternative: DataImpulse

The reason Shifter's monthly model gets compared so often to DataImpulse is arithmetic, not marketing. DataImpulse sells residential traffic from $1.00/GB on a pay-as-you-go basis — no subscription, and purchased bandwidth doesn't expire. For anyone whose usage is spiky, seasonal, or simply unknown, that structure removes the main risk of a monthly allocation: paying $175 for 50 GB and using nine.

The network side is a 90M+ IP pool across 195 countries, with HTTP(S) and SOCKS5 support. Rotating connections run on port 823 (HTTP) and 824 (SOCKS5) through the `gw.dataimpulse.com` gateway; sticky sessions use ports in the 10000–20000 range and hold an IP for one to 120 minutes, defaulting to 30. Country targeting is included in the base rate, and you can pass it in the username rather than clicking through a dashboard.

Setup is a couple of minutes: create an account, take the $5 intro pack, drop the gateway credentials into whatever client you use. If you're wiring it into Python, `proxy="http://login__cr.us:password@gw.dataimpulse.com:823"` is the whole integration.

Where it's weaker, be clear-eyed about it:

- **Advanced targeting costs double.** Per AIMultiple's write-up, state, city, ZIP, and ASN selection on residential plans are billed at 2× the standard per-GB rate. Country selection is free. If hyper-local targeting is your entire use case, that multiplier changes the maths, and it's worth confirming with support before you budget.
- **There's no scraping API.** TechRadar's review notes that DataImpulse is deliberately developer-first: you get raw proxy connections, and you handle requests, parsing, retries, and CAPTCHAs yourself. If you wanted a managed scraper, this isn't it.
- **The pool is smaller on paper.** 90M+ IPs versus Shifter's advertised 205M+. Advertised counts are unreliable on both sides, but the gap is large enough to mention rather than wave away.

On performance, an independent Proxyway benchmark from April 2025 counted over 300,000 unique proxies in DataImpulse's US pool alone, and TechRadar's testing reported a consistently high scraping success rate on the residential pool. Third-party directories list success rates around 99.3% for DataImpulse against 98.43% for Shifter. Those margins are small enough that target selection will matter more than the provider difference.

👉 [See DataImpulse's current per-GB rates and the $5 intro pack](https://bit.ly/dataimPulse)

## DataImpulse's full plan list

Four proxy types, all pay-as-you-go, all with non-expiring traffic and no subscription:

| Proxy type | Plan | Traffic | Price | Per GB | Purchase |
| --- | --- | --- | --- | --- | --- |
| Residential | Intro | 5 GB | $5 | $1.00 | [Start with the 5 GB intro](https://bit.ly/dataimPulse) |
| Residential | Basic | 50 GB | $50 | $1.00 | [Get the 50 GB pack](https://bit.ly/dataimPulse) |
| Residential | Advanced | 1 TB | $800 | $0.80 | [Take the 1 TB tier](https://bit.ly/dataimPulse) |
| Residential | Custom+ | 5 TB+ | From $4,000 | Custom | [Request a 5 TB+ quote](https://bit.ly/dataimPulse) |
| Datacenter | Intro | 10 GB | $5 | $0.50 | [Start with 10 GB](https://bit.ly/dataimPulse) |
| Datacenter | Basic | 100 GB | $50 | $0.50 | [Get the 100 GB pack](https://bit.ly/dataimPulse) |
| Datacenter | Advanced | 1 TB | $450 | $0.45 | [Take the 1 TB tier](https://bit.ly/dataimPulse) |
| Datacenter | Custom+ | 5 TB+ | From $2,250 | Custom | [Request a 5 TB+ quote](https://bit.ly/dataimPulse) |
| Mobile | Intro | 2.5 GB | $5 | $2.00 | [Start with 2.5 GB mobile](https://bit.ly/dataimPulse) |
| Mobile | Basic | 25 GB | $50 | $2.00 | [Get the 25 GB mobile pack](https://bit.ly/dataimPulse) |
| Mobile | Advanced | 1 TB | $1,600 | $1.60 | [Take the mobile 1 TB tier](https://bit.ly/dataimPulse) |
| Mobile | Custom+ | 5 TB+ | From $8,000 | Custom | [Request a mobile quote](https://bit.ly/dataimPulse) |
| Premium residential | Intro | 1 GB | $5 | $5.00 | [Test the premium pool](https://bit.ly/dataimPulse) |
| Premium residential | Basic | 10 GB | $50 | $5.00 | [Get the premium 10 GB pack](https://bit.ly/dataimPulse) |
| Premium residential | Custom+ | 5 TB+ | From $20,000 | Custom | [Request a premium quote](https://bit.ly/dataimPulse) |

The pattern to notice: the datacenter pool at $0.50/GB undercuts Shifter's residential rate by half, and the mobile pool at $2.00/GB is priced below the usual $3+ floor for 4G/5G traffic. If your targets don't require residential IPs, you were never Shifter's customer in the first place — a datacenter gateway at $0.50/GB will do the same job for a fraction of a monthly allocation.

## Shifter vs DataImpulse, side by side

|  | Shifter | DataImpulse |
| --- | --- | --- |
| Model | Monthly plan with included bandwidth | Pay-as-you-go, top up any time |
| Residential entry | $10 for 5 GB ($2.00/GB) | $5 for 5 GB ($1.00/GB) |
| Best residential rate | ~$0.75/GB at 200 GB+ | $0.80/GB at 1 TB |
| Advertised pool | 205M+ IPs, 195+ countries | 90M+ IPs, 195 countries |
| Targeting | Full Geo from $0.75/GB; cheaper Country Geo and Non-Geo pools | Country included; city/ZIP/ASN billed at 2× |
| Protocol support | HTTP(S), SOCKS5 | HTTP(S), SOCKS5 |
| Session control | Per-request rotation + sticky | Per-request rotation + sticky, 1–120 min |
| Traffic expiry | Monthly allocation | Never expires |
| Refunds | 3-day money-back guarantee | Refund window for new users per AIMultiple's write-up |
| Scraping API | Available | Not offered — raw proxy connections only |

The crossover point is roughly 200 GB a month. Below that, Shifter's discounted tier is competitive but its entry prices are high, and you're buying an allocation you might not finish. Above it, Shifter's volume rates pull ahead on paper — with the caveat that DataImpulse's 1 TB tier lands at $0.80/GB, so the gap is smaller than the marketing pages suggest.

## Which one fits your workload

**Stay with (or move to) Shifter if** you're running sustained monthly volumes above 200 GB, you need city-level targeting as a default rather than an add-on, or you specifically want the 205M+ network's spread. The bandwidth model with unlimited concurrency suits high-request-rate crawls where you'd otherwise be counting ports.

**Go pay-as-you-go instead if** your usage is unpredictable, you're testing multiple data sources before committing budget, or you just can't justify a 50 GB minimum when your realistic month is 12 GB. A $5 entry that never expires is a much cheaper way to find out whether a proxy pool works on your targets than a $175 monthly plan with a three-day window to change your mind.

👉 [Test DataImpulse on your own targets with the $5 pack](https://bit.ly/dataimPulse)

## FAQ

**Does Shifter still offer unmetered port-based plans?**
No. The port-based model was replaced by the bandwidth-based gateway, which charges per GB moved rather than per port. Reviews describing unmetered ports are referencing the legacy product.

**Is there a Shifter free trial?**
Not a free one. All plans come with a 3-day money-back guarantee.

**Can I use either provider with Puppeteer, Playwright, or httpx?**
Both are standard HTTP(S)/SOCKS5 gateways, so yes — you point the client at the gateway and authenticate with credentials. Neither one solves anti-bot detection for you. DataImpulse explicitly doesn't ship a scraping API, so request handling and CAPTCHA logic stay on your side.

**What's the actual difference between residential, datacenter, and mobile IPs?**
Residential addresses come from home connections and look like ordinary users, which is why they cost more. Datacenter addresses are fast and cheap but easier to flag. Mobile addresses come from cellular carriers and survive stricter anti-bot systems because blocking one would cut off thousands of legitimate users on the same tower. If your targets are aggressive about bot detection, mobile is the tier that keeps working.

**Does DataImpulse's traffic really never expire?**
That's the core of the pitch, and it's repeated across the provider's own product pages and in third-party write-ups: what you buy stays in your balance until you consume it. For intermittent projects, it's the single most useful structural difference from a monthly plan.

## Verdict

Shifter isn't a bad network — 98.43% success rates from an independent directory and unlimited concurrency on a 205M+ advertised pool is a legitimate offering. What makes the review complicated is the pricing curve. The 5 GB plan costs $2.00/GB and the 50 GB plan's discounted rate still sits near $1.00/GB, which is a lot to pay for a pool whose live address count is a fraction of the advertised one. The value only shows up above 200 GB a month.

So the honest recommendation splits by volume. If you're moving hundreds of gigabytes monthly and need city-level targeting by default, Shifter's ladder is worth negotiating with. If you're still figuring out which targets you can crack, spending $5 on traffic that doesn't expire beats committing $175 to a plan with a three-day exit.

👉 [Compare DataImpulse's pay-as-you-go plans and start small](https://bit.ly/dataimPulse)
