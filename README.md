# Dedicated server with RDP: what it costs, how many users can connect at once, and when bare metal beats a $5 seat (plan table inside)

A bare-metal Windows machine you reach over Remote Desktop starts at **€85.00/month** at Ava Hosting, the provider behind the link at the top of this page, billed monthly in EUR with Windows licensed and DDoS protection included. A shared RDP seat on someone else's Windows box starts at **$4.99/month**. Both get sold under the phrase "dedicated RDP", and that roughly 17-fold gap is the first thing to sort out before comparing CPU cores.

What follows covers the three product types hiding behind the keyword, the licensing detail that decides whether five people can log in at once or only one, and which configuration fits a one-person trading desk versus a small team running an ERP.

> **Short answer for most small teams:** the AMD Ryzen 5 4650G bare-metal configuration at €85.00/mo is the entry point worth pricing first. It suits two to five people sharing a single Windows machine, or one person who needs a box that never waits on a neighbour. If you need one desktop to run one Windows program, a shared seat costs a fraction of that and the bare metal is wasted money.
> 👉 [Check the current Ryzen 5 configuration and price](https://my.ava.hosting/aff.php?aff=15562)

## Ava Hosting's dedicated RDP line, plan by plan

Ava Hosting provisions a physical Windows server in Chișinău, Moldova, and hands the whole machine to one tenant. CPU, RAM, disks and the network interface belong to your account alone, which is the point: no other customer's workload can take cycles away from yours. Setup takes up to 24 hours, often less, and the order page states the timeline before you pay.

The published price range runs from €85.00 to €149.00 per month across AMD Ryzen and dual Intel Xeon E5 platforms. RAM and disk size are set per SKU, so the table below gives the price anchors and the platform; the live configuration for each SKU sits in the plan selector.

| Configuration | What's on the machine | Price | Billing | Order |
| --- | --- | --- | --- | --- |
| AMD Ryzen 5 4650G | Bare metal, single tenant, licensed Windows, DDoS protection included; RAM and disk confirmed per SKU | €85.00/mo | Monthly, EUR | [See this plan](https://my.ava.hosting/aff.php?aff=15562) |
| Dual Intel Xeon E5 v2 / v3 SKUs | Configurations between the two price anchors; CPU pair, RAM and disk differ by SKU | €85.00–€149.00/mo | Monthly, EUR | [Compare these SKUs](https://my.ava.hosting/aff.php?aff=15562) |
| 2× Intel Xeon E5-2699 v3 | Top of the published range, dual socket | €149.00/mo | Monthly, EUR | [See the top configuration](https://my.ava.hosting/aff.php?aff=15562) |

Treat €85.00 and €149.00 as the provider's published anchors rather than a fixed quote; the selector shows the live figure for the SKU you pick, and disk type and capacity change from one configuration to the next.

The terms around the hardware matter as much as the hardware:

| Parameter | Detail |
| --- | --- |
| Location | Chișinău, Moldova (single datacenter) |
| Provisioning | Up to 24 hours, often faster |
| Uptime SLA | 99.9%, covering power and network |
| DDoS protection | Included on all plans |
| Management | Unmanaged by default; optional managed support at €20/hour |
| OS | Licensed Windows environment; confirm the edition at order |
| Storage redundancy | RAID mirroring on selected configurations |
| Payment | Visa, Mastercard, PayPal, bank transfer, WebMoney, 20+ cryptocurrencies |
| Currency and cycle | EUR, monthly |

## Three different products are sold under the same name

Search the phrase and you get prices from $4.99 to $289.95 a month in the same list. Those numbers come from different products, and putting them side by side produces a wrong answer. Here is what each tier actually is.

| What is sold as "dedicated RDP" | What you get | Verified example |
| --- | --- | --- |
| Shared RDP seat | One account on a multi-tenant Windows machine; admin access usually withheld | MaxRDP, from $4.99/mo |
| RDP desktop plan | A dedicated Windows 11 desktop environment, often on a 100 Mbps port | ServerGigabit, $89.95–$289.95/mo (prices listed January 2025) |
| Bare-metal Windows server | The entire physical machine, full administrator rights | RDPextra $166.99/mo; Ava Hosting from €85.00/mo |

RDPextra states plainly that its shared RDP plans do not include admin access. That single line disqualifies the shared tier for anyone who needs to install software, change Windows settings or run a service. For a hosted desktop where you only use applications, it's fine and cheap.

A VPS sits between the two. It's a virtual slice of a host, with a fixed vCPU allocation and a RAM ceiling, and Fornex's own comparison pitches dedicated Windows hardware at 32–256 GB of RAM against a VPS as the smaller option. VPS pricing is a fraction of bare metal, and so is the headroom when a neighbouring slice bursts.

## Windows licensing and concurrent users decide your real bill

This is where a €85 server can turn into a different number.

Ava Hosting states the machine ships with a licensed Windows environment, which removes the work of sourcing a licence separately. The public page doesn't spell out which Windows Server edition applies to each SKU, and it doesn't say how many RDS CALs come with it. Both matter the moment a second person needs to work on the desktop at the same time.

For comparison on how providers usually phrase this: Fornex lists Windows Server 2019, 2022 and 2025 as licensed on its Windows RDP servers, states that standard RDS CALs are included, and adds that the number of concurrent users depends on the server configuration and the type of RDS licensing. That's the honest version of the answer, and it's the question to put to any provider before paying.

Two practical rules follow. One person connecting to run software needs no concurrency planning. Two or more people working at once needs a stated CAL count in writing, because adding user licences after the fact is the most common surprise on this product type.

On sizing, RDPextra's guidance is to estimate from peak concurrent users, transaction rates and storage I/O, then add 20–30% headroom for spikes. For a five-person team on a database-backed application, that means sizing for the busiest hour of the month rather than the average day.

👉 [Confirm the Windows edition and licence terms on the order page](https://my.ava.hosting/aff.php?aff=15562)

## Port 3389 and what isolation does not fix

RDP listens on TCP and UDP port 3389 by default. Every automated scanner on the internet knows this, and brute-force attempts against that port are constant background noise on any Windows host with a public IP.

Changing the listening port reduces automated scanning. It does not replace strong passwords, firewall rules, a VPN or RD Gateway, multi-factor authentication and careful logging. Fornex says the same thing from the provider side and recommends moving off the default port while configuring firewall rules.

Renting a whole machine removes noisy neighbours and gives you control over the network stack. It does not remove credential attacks, because those arrive over the same port whether the box is shared or yours alone. Budget an hour for the initial hardening pass, or use the managed option if nobody on the team has done it before.

## Unlimited bandwidth is not the same as port speed

Two numbers get confused in every listing. Bandwidth is the monthly transfer cap; port speed is the rate of the network interface, typically 1 Gbps or 10 Gbps. A server with unmetered transfer on a 1 Gbps port can still saturate that port during a backup window.

For a Windows desktop workload this rarely bites. For anything serving traffic to the public, check the port capacity, not just the word "unlimited". Ava Hosting publishes DDoS protection as included across plans but doesn't state the port rate per SKU on the page, so ask what interface your configuration gets before you commit.

## What the first invoice does not show

**Management is hourly, not a retainer.** Ava Hosting sells the server unmanaged by default, with optional managed support at €20/hour. Patching, Windows updates, hardening and incident response are yours unless you buy time. A team without a Windows administrator should price a few hours a month into the budget rather than assume support is included.

**The SLA covers power and network.** 99.9% uptime on a dedicated server means the machine has electricity and connectivity. It says nothing about your application staying up, which is your side of the line.

**Reviews are mixed and worth reading.** A verified customer review from mid-2025 rated the host 2.5 out of 5, citing slow ticket replies and uneven load times. That review covers the hosting service generally rather than the dedicated RDP line, and it's one data point, but slow support on an unmanaged box is exactly the failure mode the €20/hour managed option exists to cover.

**Check for setup fees and currency conversion.** At least one provider in this market quotes a one-time setup charge on selected configurations, and Ava Hosting bills in EUR on a monthly cycle. If your card is in another currency, the conversion sits on top of the sticker price.

## Which configuration fits your workload

**One person, one desktop, one Windows program.** Take a shared RDP seat at $4.99–$15/month or a Windows VPS. You get a desktop, you save the difference, and you lose admin rights. Accept that trade or move up a tier.

**One person who needs administrator rights and predictable performance.** The Ryzen 5 4650G at €85.00/mo is the smallest bare-metal option here. Fine for a trading terminal, a single ERP client or an automation script that runs all day and cannot afford a stolen CPU cycle.

**Three to five people on the same machine.** Same entry configuration if the workload is light, but get the concurrent-user question answered first. If everyone runs a heavy application at once, or a database sits behind the desktop, step up to the dual Xeon E5 range.

**Database or trading infrastructure with sustained I/O.** The dual-socket Xeon E5-2699 v3 configuration at €149.00/mo is where more cores and memory headroom live. Fornex lists 1C with SQL, trading terminals and multi-user remote desktops as the workloads that justify physical hardware over a VPS, and that list matches what this tier is for.

**Compliance or jurisdiction reasons.** Moldova is the only location Ava Hosting publishes for this line. Check the latency from where your users sit before ordering, and check whether the jurisdiction suits your data.

## FAQ

**Can several people log in at the same time?**
Only with the right Windows edition and enough RDS CALs. Ask the provider to confirm both in writing for the SKU you're buying. One person needs no CAL planning; two or more do.

**Do I have to buy a Windows licence separately?**
Ava Hosting states the server is provisioned with a licensed Windows environment. Confirm the edition during ordering, since it affects both concurrency and which applications will run.

**How long until the server is usable?**
Up to 24 hours from order confirmation, often faster, with the timeline stated at order. Compare that with desktop-plan providers quoting 24–72 hours.

**Can I install my own software?**
Yes on the bare-metal line. You get full administrative control, and the server is unmanaged by default, which means nobody else will install it for you.

**Should I change the RDP port?**
Yes, and then finish the rest of the hardening: strong passwords, firewall rules, MFA, a VPN or RD Gateway, and logging. The port change alone stops scanners and nothing more.

## How to decide

Match the tier to the number of people before you match it to the price. One user without admin needs a shared seat. One user with admin needs the €85.00 Ryzen configuration. Three or more concurrent users, or a database behind the desktop, needs a stated CAL count and probably the dual Xeon range at €149.00.

Before you pay, confirm two things in writing: which Windows edition comes with your SKU and how many simultaneous users it supports, and the current price for the exact configuration you selected, since RAM and disk vary per SKU. Then check whether €20/hour managed support belongs in your first month.

👉 [Start with the entry bare-metal configuration at Ava Hosting](https://my.ava.hosting/aff.php?aff=15562)
