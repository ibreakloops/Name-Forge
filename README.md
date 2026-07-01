# Name Forge

A single-file browser tool that generates brandable SaaS names and checks whether the domains are actually free — running live DNS lookups in your browser so you get real availability signals instead of guesses.

Built for naming an AI social-media scheduler, but it works for any software product.

## Why this exists

In crowded SaaS categories, almost every obvious name (real words, easy compounds like *PostFlow*, *LoopPilot*) is already registered. Checking names one at a time is slow, and eyeballing a search engine only catches names that already have a website — it can't tell you a name is *free*. Name Forge flips that: it generates many candidates at once and checks each domain against public DNS, so you see green/red in seconds.

## What it does

- Generates 24 names per batch from your seed words using four strategies: invented/coined, real word + twist, two words blended, and AI-flavored.
- Checks each name across the endings you select (`.com`, `.ai`, `.io`, `.app`, `.co`) live.
- Lights each domain **green (likely available)**, **red (registered)**, or flags it for a manual check.
- Filters to show only names whose `.com` is open.
- Links every available domain straight to a registrar to confirm and buy.

## How to use it

1. Open `name-forge.html` in any modern browser (double-click it, or drag it into a browser tab). Nothing to install.
2. In **Seeds**, type root words or vibes, comma-separated. These get twisted, blended, and suffixed.
3. Under **Naming styles**, toggle the approaches you want.
4. Under **Check these endings**, pick the TLDs to test.
5. Click **Forge 24 names**. Watch the domain lights resolve.
6. Click **Show only fully-open .com** to narrow to names where the `.com` is free — these get a green border.
7. Click any **available ✓** link to jump to a registrar and confirm.

Tip: if every twist on a word comes back red, that word's territory is exhausted — lean harder on the coined/invented style, which is where open domains still live.

## How the availability check works

The tool queries Google's public DNS-over-HTTPS resolver (`dns.google`) for each domain's **NS (nameserver) records**:

- **NXDOMAIN** (no such domain) → no delegation exists → very likely unregistered → shown green.
- **NOERROR with records** → the domain is delegated → registered → shown red.

Everything runs client-side. No data is saved, and nothing is sent anywhere except the DNS queries themselves.

## Important limits — read before you buy

- **Green is a strong signal, not proof.** A registered domain can sit with no DNS records, and some open domains are premium-priced or reserved. Always purchase-check a finalist at a registrar (e.g. Instant Domain Search, Namecheap) before committing.
- **DNS says nothing about trademarks.** An open domain can still collide with an existing trademark. Search the [USPTO database](https://tmsearch.uspto.gov) — or your country's registry — for conflicts in your class.
- **Social handles are separate.** Check availability on the platforms you care about (Instagram, X, etc.) independently.
- **Generated names are raw material.** Some will be awkward to say or spell. Read the winners out loud before you fall in love.

## Requirements

A modern browser with internet access (for the DNS lookups). No build step, no dependencies, no accounts.

## Files

- `name-forge.html` — the complete tool. Self-contained; share or archive this one file.
- `README.md` — this document.
