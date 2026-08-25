# 🍕 The Pizza Atlas

A free dough calculator, pizza builder, wiki, and personal recipe notebook for seven pizza styles — Neapolitan, New York, Roman Tonda, Roman al Taglio, Detroit, Sicilian, and Chicago Deep-Dish. It lives entirely in a single web page. No app to install, no account to create, no fee.

**Live site:** `https://shatnero.github.io/pizza-atlas/` *(update this link once the site is deployed — see "Putting this online" below)*

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

### 3. Design toppings and get a shopping list (the Builder)
The **Builder** tab has 14 classic pizza builds split into tomato-based ("Rosso") and white ("Bianco") — Margherita, Diavola, Detroit-style ideas, Chris Bianco's famous "Rosa," and more. Amounts scale automatically to whatever size you set on the Calculator. Pick a build, tell it how many of your pizzas get it, and tap **Add to Shopping List** — mix and match multiple builds across one batch. **Copy Full List** gives you a single paste-ready shopping list combining your dough ingredients and every topping you added, ready for Apple Notes, Reminders, or a text to whoever's shopping.

### 4. Read the Wiki
The **Wiki** tab has three sections:
- **General Knowledge** — fermentation timing, flour basics, kneading, sauce, baking science. Applies across all styles.
- **Style Guides** — one page per pizza style: its history, how the dough is handled, how it's assembled, and how it's baked.
- **Sources & Reading** — every book, official standard, and video this app's numbers are based on, so nothing here is a black box. If a claim seems off, you can go check it yourself.

### 5. Save your own recipes (the Notebook)
Found a dough you like? On the Calculator, give it a name and tap **Save to Notebook**. The **Notebook** tab also has a place to jot down your own sauce recipes and general notes.

**Important:** this is saved *on your device, in your browser* — not to an account, and not shared with other visitors to the site. See "How saving works" below.

### 6. Switch units
Top-right corner: toggle between **Metric (g, °C)** and **US (oz, °F)** any time. Everything on the page converts instantly.

### 7. Ask a local AI about the Wiki (optional, advanced)
The **Ask AI** tab can answer questions grounded in this app's own Wiki content — but only if you connect it to a language model running on your own computer first. This is entirely optional and off by default. See "Connecting a local AI" below if you want to set it up.

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

## Connecting a local AI (optional, advanced)

The **Ask AI** tab can chat with you about anything in the Wiki or Style Guides — but it doesn't talk to any cloud AI service, and it doesn't work out of the box. It connects to a language model running on **your own computer**, and nothing else. No data ever leaves your network; nothing passes through Anthropic, Claude, or any cloud service. If you never set this up, the rest of the app works exactly the same without it.

### The one currently supported setup: Mac + LM Studio

1. On your Mac, install and open **[LM Studio](https://lmstudio.ai)**, then load any model.
2. Go to the **Developer** tab → **Server Settings**.
3. Turn on **"Serve on Local Network"** and **"Enable CORS,"** then start the server.
4. Find your Mac's local IP address: **System Settings → Wi-Fi → Details** (looks like `192.168.1.23`).
5. On the device using Pizza Atlas — your iPhone, another computer, anything on the same Wi-Fi — open the **Ask AI** tab and set the Base URL to `http://192.168.1.23:1234/v1` (your actual IP and port). Tap **Test Connection**.
6. If you're using Pizza Atlas on the *same Mac* that's running LM Studio, you can just use `http://localhost:1234/v1` instead — skip steps 3 and 4.

Both devices need to be on the **same Wi-Fi network**. This is not a remote/over-the-internet connection.

**Security note:** turning on "Serve on Local Network" makes LM Studio's server reachable by other devices on your Wi-Fi, not just your Mac. Only do this on networks you trust.

### Why you can't just use the "Locally" iPhone app for this

If you already use LM Studio's own iPhone app, **Locally**, it's natural to expect it to be the shortcut here — it isn't, and it's worth understanding why so it doesn't feel like something's broken. Locally connects to LM Studio through **LM Link**, a closed, account-authenticated tunnel. LM Studio's own documentation states plainly that this link is "designed to connect LM Studio on your computer to Locally on your mobile device, not between two Locally apps" — it doesn't expose any address that Pizza Atlas, or any other third-party app, can reach. Locally is a self-contained chat client, not a local API server other apps can call.

**In short: no Mac-free, Locally-only path exists yet.** If LM Studio ever exposes a reachable local endpoint through Locally, this section — and the app itself — will be updated to support it directly. Until then, the Mac + Wi-Fi method above is the supported route.

### Troubleshooting

- **Test Connection fails:** double-check the server is actually running (LM Studio's Server tab should say so), the IP/port match what LM Studio shows, and "Enable CORS" is on.
- **Still fails in Chrome specifically:** Chrome enforces an extra restriction (Private Network Access) that can block this kind of request even with CORS enabled. Try Safari instead before assuming something's misconfigured.
- **Works on the Mac but not the iPhone:** almost always means the two devices aren't on the same Wi-Fi network, or "Serve on Local Network" wasn't turned on (leaving the server reachable only from the Mac itself).

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

**Does the AI feature send my data anywhere?**
No. It only ever contacts the exact address you type into the Base URL field yourself — by default, nothing is configured, and no cloud fallback exists. See "Connecting a local AI" above.

---

## Putting this online (for whoever owns this repository)

If this repository doesn't have GitHub Pages turned on yet, here's the whole process — no coding, about two minutes:

1. Go to this repository on GitHub and click **Settings**.
2. In the left sidebar, click **Pages**.
3. Under "Build and deployment" → "Source," choose **Deploy from a branch**.
4. Under "Branch," choose **main** (or whichever branch has the code) and folder **/ (root)**, then click **Save**.
5. GitHub will show a green banner with your live URL, usually `https://<your-username>.github.io/<repository-name>/`. It can take a minute or two to go live the first time.
6. Update the "Live site" link at the top of this README with that URL.

That's it — no build step, no server to manage. Any time the `index.html` file in this repo is updated, the live site updates automatically within a minute or two.

---

## For developers

- The entire app is one file: `index.html`. No build step, no package manager, no dependencies except a Google Fonts stylesheet loaded from a CDN.
- Storage is handled by a small abstraction (`storeSet` / `storeGet` / `storeDelete` / `storeList`) that automatically uses Claude.ai's artifact storage when running inside Claude, and falls back to the browser's own `localStorage` everywhere else (including here, self-hosted). No code changes are needed to move between the two.
- All dough math lives in a handful of pure functions (`factor()`, `breakdown()`, `computeTotal()`, `solveFlourFromTotal()`) driven by a single `STYLES` data object — adding a new pizza style means adding an entry to that object and a matching Wiki guide, not rewriting the calculator.
- Contributions: open an Issue to discuss a change first for anything non-trivial; Pull Requests for typo fixes, sourcing corrections, or new styles are welcome. Please keep numeric claims traceable to a real source, in the spirit of the in-app Sources page.
- No license file is included yet — add one (MIT is a common, permissive choice for a project like this) if you want to make reuse terms explicit.

## Credits

Dough ranges and technique notes are drawn from the AVPN Disciplinare, several published baking books, test-kitchen publications, and pizza-making communities — the full, itemized list lives in the app itself under **Wiki → Sources & Reading**, including per-style-guide citations for exactly which source backs which claim.
