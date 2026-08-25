# 🍕 The Pizza Atlas

A free dough calculator, wiki, and personal recipe notebook for seven pizza styles — Neapolitan, New York, Roman Tonda, Roman al Taglio, Detroit, Sicilian, and Chicago Deep-Dish. It lives entirely in a single web page. No app to install, no account to create, no fee.

**Live site:** https://shatnero.github.io/pizza-atlas/

---

## What this actually is

It's one file — `index.html` — that runs entirely in your browser. There's no server behind it and nothing to install. Open the link above on a phone, tablet, or computer and it just works, the same way a normal website does.

## How to use it (no technical knowledge required)

### 1. Pick a pizza style
Open the **Calculator** tab. At the top is a row of style cards — tap one (Neapolitan, New York, Detroit, etc.) and every setting below updates to that style's typical starting point.

### 2. Adjust the dough recipe
Every number on the page is editable and they all talk to each other automatically:
- Change **how many pizzas** you want, or **how big** each one is, and the flour/water/salt amounts recalculate.
- Drag a slider (hydration, salt, oil) and the recipe updates live.
- Type a number directly into any box on the recipe ticket (the card on the right) — finish typing and either tap elsewhere or press **Enter/Done** to lock it in.

There's no wrong order to do this in — start from whichever number you actually know (e.g. "I have a 10×14 inch pan") and everything else follows.

### 3. Read the Wiki
The **Wiki** tab has three sections:
- **General Knowledge** — fermentation timing, flour basics, kneading, sauce, baking science. Applies across all styles.
- **Style Guides** — one page per pizza style: its history, how the dough is handled, how it's assembled, and how it's baked.
- **Sources & Reading** — every book, official standard, and video this app's numbers are based on, so nothing here is a black box. If a claim seems off, you can go check it yourself.

### 4. Save your own recipes (the Notebook)
Found a dough you like? On the Calculator, give it a name and tap **Save to Notebook**. The **Notebook** tab also has a place to jot down your own sauce recipes and general notes.

**Important:** this is saved *on your device, in your browser* — not to an account, and not shared with other visitors to the site. See "How saving works" below.

### 5. Switch units
Top-right corner: toggle between **Metric (g, °C)** and **US (oz, °F)** any time. Everything on the page converts instantly.

---

## How saving works (please read this one)

This site has no database and no login. When you save a dough, sauce, or note, it's stored in your web browser's own local memory for this site — similar to how a website might remember you're logged in.

That means:
- ✅ It'll still be there next time you visit *on the same device, in the same browser*.
- ❌ It will **not** show up if you open the site on a different phone/computer, or in a different browser on the same device.
- ❌ Clearing your browser's site data/cookies for this site will erase it.
- ❌ Other people who visit the site do **not** see your saved recipes — everyone's Notebook is private to their own browser.

**To actually share a recipe with someone:** open it in the Notebook and tap **Share** — it copies a short text summary you can paste into a message, text, or email. That's the intended way to pass a recipe to a friend.

---

## Frequently asked questions

**Do I need to install anything?**
No. It's a normal webpage. Works in any modern browser — Safari, Chrome, Firefox, etc.

**Is there a mobile app?**
No, and it doesn't need to be — the website itself works fine on a phone screen.

**Will my saved recipes ever disappear?**
Only if you clear your browser's data for this site, uninstall/reset the browser, or switch devices. If you want a recipe to survive any of that, tap **Share** and paste the text somewhere safe (notes app, message to yourself, etc.).

**I found a mistake, or want a feature added — what do I do?**
Open an **Issue** on this repository (see below) describing it. If you know how to code, Pull Requests are welcome too.

**Is this "official" pizza information?**
Only for Neapolitan, which has one real official standard (the AVPN). Every other style here is a best-effort, well-sourced home-kitchen adaptation of published books, test kitchens, and long-running pizza-making communities — see the in-app **Sources & Reading** page for exactly what backs each number.


## For developers

- The entire app is one file: `index.html`. No build step, no package manager, no dependencies except a Google Fonts stylesheet loaded from a CDN.
- Storage is handled by a small abstraction (`storeSet` / `storeGet` / `storeDelete` / `storeList`) that automatically uses Claude.ai's artifact storage when running inside Claude, and falls back to the browser's own `localStorage` everywhere else (including here, self-hosted). No code changes are needed to move between the two.
- All dough math lives in a handful of pure functions (`factor()`, `breakdown()`, `computeTotal()`, `solveFlourFromTotal()`) driven by a single `STYLES` data object — adding a new pizza style means adding an entry to that object and a matching Wiki guide, not rewriting the calculator.
- Contributions: open an Issue to discuss a change first for anything non-trivial; Pull Requests for typo fixes, sourcing corrections, or new styles are welcome. Please keep numeric claims traceable to a real source, in the spirit of the in-app Sources page.
- No license file is included yet — add one (MIT is a common, permissive choice for a project like this) if you want to make reuse terms explicit.

## Credits

Dough ranges and technique notes are drawn from the AVPN Disciplinare, several published baking books, test-kitchen publications, and pizza-making communities — the full, itemized list lives in the app itself under **Wiki → Sources & Reading**, including per-style-guide citations for exactly which source backs which claim.
