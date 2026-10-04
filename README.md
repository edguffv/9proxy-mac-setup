# 9proxy for mac: App Setup, macOS 12+ Requirements, and Which Plan Fits Your Workflow

Most people searching this have one of two problems. Either they want to know whether 9Proxy even has a Mac build, or they already downloaded something and it wouldn't install. So here's the short version: a native macOS client exists, it ships as a `.pkg` installer from inside your account, and it needs macOS 12 Monterey or newer. On macOS 11 Big Sur it simply won't run. There's also a way to use 9Proxy on a Mac with no installation at all, which matters if you're on an older machine or you just don't want another client sitting in your menu bar.

The rest of this covers the install path, what the Mac app can and can't do, how to plug it into the browsers and scripts you already run on macOS, the current package prices, and the handful of limits that tend to surprise people a couple of weeks in.

## Check your macOS version before anything else

The official macOS setup guide is unusually specific about requirements:

- **OS**: macOS 12 Monterey, 13 Ventura or later
- **RAM**: 4 GB minimum
- **Disk space**: 200 MB free
- **Network**: stable Wi-Fi or mobile data

That Mac-specific OS floor is the single most common tripwire. If you're on Big Sur, the app won't launch and it isn't a corrupted download problem. 9Proxy's own FAQ answers it directly: the client is compatible with macOS 12 and above, and macOS 11 users are told to update the system first.

> If you can't or won't upgrade past macOS 11, you don't have to abandon the service. 9Proxy runs residential sessions from its dashboard through Proxy2Web, so the proxying happens on their infrastructure rather than on your Mac — you just paste the host, port, username and password into whatever tool you're using.

## What the Mac client actually does

It isn't a VPN and it doesn't tunnel your whole machine by default. The Mac app is a port-forwarding control panel: you filter a pool of residential IPs, forward individual IPs to local ports, and then point any application at `127.0.0.1:port`. Everything you run through that port leaves from a residential IP somewhere in the pool; everything else on your Mac goes out your normal connection.

The macOS 2.0 release added most of what makes that workflow bearable at scale:

- **Quick Bind** — bind IPs to ports from a saved filter or a specific country in a couple of clicks
- **Auto Refresh Proxy** — if a port drops offline, it swaps in a fresh IP automatically
- **Auto Rotation Proxy** — rotates and refreshes IPs on chosen ports at an interval you set
- **Advanced Port Configuration** — assign ports by country, state, city and ISP, and decide per port whether it uses auto refresh or auto rotation
- **Custom port ranges** — control which ports the app is allowed to assign
- **Saved filters** — store a country/city/ISP search and reapply it in one click
- **Logged-in device management** — see which devices are on your account and remotely sign out of old sessions

There's also proxy authentication, so you can run `username:password` credentials instead of IP whitelisting, and sub-accounts if you want separate credentials per browser profile or per client.

## Installing 9Proxy on macOS, step by step

1. Create your account — 👉 [Open a 9Proxy account and grab the referral discount](https://bit.ly/9-Proxy). Sign-up with a Google account works too, if you'd rather not deal with another password.
2. Pick a package. Nothing in the plan list is Mac-specific; IP-based and GB-based packages behave the same on macOS, Windows and Linux.
3. Download the macOS build from the download section of your dashboard. You're looking for the `9proxy-macos.pkg` file.
4. Run the installer. It's a standard PKG, so the usual macOS Gatekeeper prompts apply.
5. Open 9Proxy from your Applications folder and sign in with your account credentials.
6. Filter the pool — country, state, city, ZIP code or ISP — then right-click an IP and choose to forward it to a port. Any port works; 60000 is a common pick.
7. Open the Port Forwarding List to see the credentials for that port, and copy them.
8. Paste them into your tool of choice. If you use proxy authentication, the username carries your targeting settings rather than the password:


useruser123-country-US-ssid-rhdN1907ma


That string goes in the username field; your sub-account password goes in the password field. Host and port come from the forwarding list. Session IDs (`ssid`) are what keep a given profile on the same IP for the length of the session.

## Wiring it into what you already run on macOS

This is where the Mac version earns its keep, because most of the tools people pair with residential proxies have Mac builds too. 9Proxy publishes step-by-step integration guides for Dolphin{anty}, BitBrowser, MuLogin, ixBrowser and XLogin, plus general proxy-manager documentation — all of their guides follow the same shape: create a sub-user, generate a session, then paste host/port/username/password into the browser profile and hit its "check proxy" button.

Beyond antidetect browsers, a Mac setup usually falls into one of these buckets:

- **Desktop browsers** — Safari doesn't take per-profile proxy settings, but Chrome and Firefox do, and macOS itself accepts a system-wide HTTP/SOCKS5 proxy under Network settings if you want everything routed
- **Scripts and scrapers** — `requests`, Scrapy and Playwright all accept a proxy string, so a forwarded port is all they need
- **SEO and rank-tracking tools** — point them at a forwarded port to check SERPs from a specific city rather than a data-centre IP
- **Multi-account work** — one forwarded IP per profile, with sub-accounts so credentials don't collide

Everything speaks HTTP/HTTPS and SOCKS5, and there's API access plus a team management layer if more than one person is touching the account.

## The limits worth knowing about before you buy

None of these are dealbreakers, but they're the things people complain about after the first bill.

**Residential IPs don't live forever.** On IP-based plans, a forwarded IP stays online for a few hours up to roughly 24 hours — that variance is inherent to real residential connections, not a bug. Auto Refresh replaces dead IPs so sessions don't just silently fail.

**Your IP balance is different from your traffic balance.** IP-based packages deduct an IP only when you actually forward it to a port, and unused IPs sit in your balance indefinitely. Traffic on GB-based packages and bundles, by contrast, is valid for 180 days. Enterprise GB packages drop the expiry entirely.

**There's no self-serve free trial.** Reviews have flagged this — you can register and explore the dashboard for free, but there's no "click here for 2 GB" button on the site. Limited trials for new users do get handed out depending on availability, usually after asking support or through the community threads where the 9Proxy team is active.

**Coverage is 90+ countries, not 195.** For US, UK, Europe and much of Southeast Asia that's fine. For something genuinely obscure, verify before you commit to a big package.

**Don't go hunting for a mobile app.** There is no official Android APK or iOS app, and third-party "9Proxy APK" downloads are repackaged malware — proxy credential stealers at best. If you need residential IPs from a phone, use the browser-based session panel instead.

Support runs 24/7 through email (`support@9proxy.com`), live chat and Telegram if something misbehaves on install.

## Every current 9Proxy package, with prices

The table below covers the full published range: IP-based residential, high-volume business IP packages, GB-based residential, enterprise traffic packages and the IP+GB bundles. Rates are in USD.

| Package | What you're buying | Price | Effective rate | Notes | Get it |
| --- | --- | --- | --- | --- | --- |
| 100 IPs | IP-based, unlimited bandwidth per IP | $24 | $0.24 / IP | IPs never expire | [Buy the 100 IP package](https://bit.ly/9-Proxy) |
| 500 IPs | IP-based | $72 | $0.144 / IP | IPs never expire | [Buy the 500 IP package](https://bit.ly/9-Proxy) |
| 1,000 + 500 IPs | IP-based, includes 500 bonus IPs | $126 | $0.084 / IP | Best entry value for teams | [Buy 1,000 IPs with 500 bonus](https://bit.ly/9-Proxy) |
| 2,500 IPs | IP-based | $210 | $0.084 / IP | Multi-vertical workloads | [Buy the 2,500 IP package](https://bit.ly/9-Proxy) |
| 5,000 IPs | IP-based | $360 | $0.072 / IP | Agency-scale profiles | [Buy the 5,000 IP package](https://bit.ly/9-Proxy) |
| 15,000 IPs | IP-based | $720 | $0.048 / IP | Regional teams | [Buy the 15,000 IP package](https://bit.ly/9-Proxy) |
| 25,000 IPs | IP-based | $863 | $0.035 / IP | Heavy automation | [Buy the 25,000 IP package](https://bit.ly/9-Proxy) |
| 50,000 IPs | IP-based | $1,438 | $0.029 / IP | Reseller volumes | [Buy the 50,000 IP package](https://bit.ly/9-Proxy) |
| 100,000 IPs | Business IP tier | $2,300 | $0.023 / IP | Enterprise allocation | [Buy the 100,000 IP business package](https://bit.ly/9-Proxy) |
| 200,000 IPs | Business IP tier | $4,140 | $0.021 / IP | Enterprise allocation | [Buy the 200,000 IP business package](https://bit.ly/9-Proxy) |
| 500,000 IPs | Business IP tier | $8,625 | $0.018 / IP | Lowest per-IP rate published | [Buy the 500,000 IP business package](https://bit.ly/9-Proxy) |
| 5 GB | GB-based, rotating IPs | $15 | $3.00 / GB | 180-day validity | [Buy the 5 GB traffic pack](https://bit.ly/9-Proxy) |
| 50 + 5 GB | GB-based, includes 5 bonus GB | $105 | $2.10 / GB | 180-day validity | [Buy 50 GB with 5 GB bonus](https://bit.ly/9-Proxy) |
| 100 GB | GB-based | $150 | $1.50 / GB | 180-day validity | [Buy the 100 GB traffic pack](https://bit.ly/9-Proxy) |
| 200 GB | GB-based | $200 | $1.00 / GB | 180-day validity | [Buy the 200 GB traffic pack](https://bit.ly/9-Proxy) |
| 1,000 GB | GB-based | $800 | $0.80 / GB | 180-day validity | [Buy the 1,000 GB traffic pack](https://bit.ly/9-Proxy) |
| 2,000 GB | GB-based | $1,500 | $0.75 / GB | 180-day validity | [Buy the 2,000 GB traffic pack](https://bit.ly/9-Proxy) |
| 3,000 GB | Enterprise GB | $2,160 | $0.72 / GB | Never expires | [Buy the 3,000 GB enterprise pack](https://bit.ly/9-Proxy) |
| 6,000 GB | Enterprise GB | $4,200 | $0.70 / GB | Never expires | [Buy the 6,000 GB enterprise pack](https://bit.ly/9-Proxy) |
| 10,000 GB | Enterprise GB | $6,800 | $0.68 / GB | Never expires | [Buy the 10,000 GB enterprise pack](https://bit.ly/9-Proxy) |
| Starter bundle | 100 IPs + 5 GB | $30 | — | Bundled traffic valid 180 days | [Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Popular bundle | 1,500 IPs + 50 GB | $180 | — | Bundled traffic valid 180 days | [Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Pro bundle | 5,000 IPs + 500 GB | $720 | — | Listed at $860, discounted to $720 | [Buy the Pro bundle](https://bit.ly/9-Proxy) |

A note on those numbers: 9Proxy raised IP-based and bundle prices on 1 June 2026 — its first adjustment in three years — while GB-based pricing stayed put. So if you find older blog posts quoting $20 for 100 IPs or a $600 Pro bundle, that's the pre-adjustment list, not a current promo.

## Which package makes sense for a Mac setup

The platform doesn't change the maths, but the workflow does. A few practical pairings:

**One person, one or two browser profiles, occasional checks** — the 100 IP package at $24, or 5 GB at $15 if your usage is bursty and light. Remember unused IPs don't expire, so the $24 doesn't evaporate if you don't touch it for a month.

**Ongoing multi-account or rank-tracking work** — 500 IPs at $72, or the 50 + 5 GB pack at $105. IP-based wins when each profile needs to sit on the same residential IP for hours; GB-based wins when you're rotating constantly across many short requests.

**Agency running several clients off one Mac** — the 2,500 or 5,000 IP tiers, or the Popular bundle if you need both stable sessions and a traffic allowance.

The bundle logic is simple arithmetic: Starter at $30 is cheaper than buying 100 IPs and 5 GB separately, and Pro at $720 comes in below the $860 list price of its components.

## Signing up, paying, and the referral discount

Registration takes a minute, and the invite link above carries the referral code in the URL — 9Proxy states that referred users get 5% off, on top of whatever package-level bonuses apply. If you already have a share code from a reseller, you can redeem it in the dashboard under Share Code → Use Code and the balance lands on your account immediately.

Payment covers credit cards, bank cards, crypto (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay and Google Pay. There's no subscription lock-in on IP-based packages — it's a balance system, not a monthly renewal you have to remember to cancel.

## Questions Mac users actually ask

**Does 9Proxy have a native Mac app?** Yes, a `.pkg` installer for macOS 12 Monterey and later. It's the same functionality set as the Windows client: filtering, port forwarding, auto refresh, auto rotation and port configuration.

**Will it run on an old Intel MacBook?** The documented requirements are macOS 12+, 4 GB of RAM and 200 MB of free disk. macOS version matters more than the chip here, though 9Proxy hasn't published Apple Silicon-specific guidance, so test with a small package before scaling up.

**Can I use one account across a Mac and a Windows PC?** Yes. The documentation allows the same account on multiple devices but suggests caution with unfamiliar machines — and the logged-in device management screen lets you kick out sessions you don't recognise.

**Do I need the app at all?** No. Proxy2Web runs sessions server-side and hands you host, port, username and password, so you can work from a Mac, a phone browser, or a machine where you can't install software.

**Is there a free trial on Mac?** Not self-serve. Reviews have called that out as a downside compared with providers offering instant test credits. New users can sometimes get a limited trial by asking support, subject to availability.

**How long does a forwarded IP last?** Anywhere from a few hours to about 24 hours on IP-based plans. GB-based traffic rotates through the pool with no fixed IP lifetime, which is why rotation-heavy work usually belongs there.

## The bottom line

9Proxy on Mac is a real, supported setup rather than a Windows tool you're forced to hack around — provided you're on macOS 12 or newer. Install the PKG, sign in, forward IPs to local ports, and paste those ports into Chrome profiles, antidetect browsers or scripts. The one genuine Mac-specific question is the OS version; everything else comes down to whether you want to pay per IP with unlimited bandwidth or per gigabyte with rotation, and the entry tiers at $24 and $15 are cheap enough to answer that empirically rather than by reading comparison tables.
