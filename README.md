# UxFold Lab

**Design in real code, without writing it.**

UxFold Lab is a free Mac app for designers. You open a real website or web app, see it running live, and change it by pointing at things and saying what you want. A coding agent you already use (Claude Code, Codex or OpenCode) writes the code. You stay in charge of the design: every change goes through your agent's chat, where you can read it first, and any change can be undone.

**[Download UxFold Lab for Mac](https://github.com/uxfold/UxFold-Lab-Latest/releases/latest/download/UxFold-Lab.dmg)** (version 1.1.0, Apple Silicon and Intel, macOS 13 or later)

---

## Contents

- [Why UxFold Lab](#why-uxfold-lab)
- [What you need](#what-you-need)
- [Install](#install)
- [Your first 5 minutes](#your-first-5-minutes)
- [The workspace at a glance](#the-workspace-at-a-glance)
- [Three ways to change a design](#three-ways-to-change-a-design)
- [Undo and token cleanup](#undo-and-token-cleanup)
- [Starting a project](#starting-a-project)
- [More tools](#more-tools)
- [Keyboard shortcuts](#keyboard-shortcuts)
- [Where your files live](#where-your-files-live)
- [Privacy](#privacy)
- [Troubleshooting](#troubleshooting)
- [Known issues](#known-issues)
- [Feedback](#feedback)
- [Credits and licenses](#credits-and-licenses)

---

## Why UxFold Lab

Design tools draw pictures of a product. Code is the product. UxFold Lab puts you in front of the real thing, so what you change is what ships.

- **See it live.** Your project runs inside the app, at any screen size, exactly as a browser shows it.
- **Change the whole look in seconds.** Type or nudge colours, spacing, sizes and corner radius in the Tokens panel, for every use of a token or for one element. No AI, no waiting.
- **Point and describe.** Click a button and type "make this bigger and friendlier". Your agent edits the right file and you watch the result appear.
- **Change many things at once.** Pick several elements, and Lab puts them in your agent's chat for one instruction, such as "make these cards match".
- **Nothing is final.** Undo (Cmd+Z) steps back the last change, and Lab keeps a list of your token edits for your agent to tidy up.
- **Your agent, your account.** Lab drives the coding agent you already have. It does not resell AI or need another subscription.

---

## What you need

| | |
|---|---|
| **A Mac** | macOS 13 (Ventura) or later, Apple Silicon or Intel |
| **Node.js** | Version 20.9 or later. Download it from [nodejs.org](https://nodejs.org). To check, open Terminal and type `node --version`. |
| **A coding agent** | At least one of these, installed and signed in: [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Codex](https://github.com/openai/codex) or [OpenCode](https://opencode.ai). Run it once in Terminal (`claude`, `codex` or `opencode`) and sign in. |
| **Git** | macOS offers to install it the first time anything uses `git`. |

If Lab cannot find a signed-in agent, it shows a short note on the home screen with a link back to this page.

---

## Install

1. Download **[UxFold-Lab.dmg](https://github.com/uxfold/UxFold-Lab-Latest/releases/latest/download/UxFold-Lab.dmg)** from the [latest release](https://github.com/uxfold/UxFold-Lab-Latest/releases/latest) and open it.
2. In the window that appears, drag **UxFold Lab** onto the **Applications** folder.
3. Open UxFold Lab from your Applications folder.

### The first time you open it

UxFold Lab is not signed with an Apple Developer account, so macOS blocks it the first time. This is normal for independent apps, and you only do it once.

1. Open the app once. When macOS says it cannot be opened, click **Done**.
2. Open **System Settings > Privacy & Security**.
3. Scroll down to **Security**. Next to the message about UxFold Lab, click **Open Anyway**.
4. Confirm with your password (or Touch ID), then click **Open Anyway** again.

If you do not see **Open Anyway**, open the **Terminal** app, paste this line and press Return. It removes the "downloaded from the internet" flag from the app:

```bash
xattr -dr com.apple.quarantine "/Applications/UxFold Lab.app"
```

Then open the app normally.

### Check the download (optional)

Each release also has a file called `UxFold-Lab.dmg.sha256`. Download it into the same folder as the DMG, then run this in Terminal from that folder:

```bash
shasum -a 256 -c UxFold-Lab.dmg.sha256
```

It should print `UxFold-Lab.dmg: OK`. Anything else means the download is damaged; download it again.

---

## Your first 5 minutes

1. **Create a project.** On the home screen click **New Project**, give it a name and keep the defaults (Next.js and shadcn/ui). Click **Create**. Lab copies the Welcome starter and installs it, which takes about a minute.
2. **Look around.** The preview opens on a page called "Welcome to UxFold". Use the sidebar inside the page to visit Dashboard and Settings. These pages are there for you to practise on.
3. **Try Tokens.** Turn **Select** on in the preview toolbar, choose **Tokens** and click a card. Type a new padding or pick another spacing token, and the page updates.
4. **Try Describe.** Choose **Describe**, click two or three elements, then click **Confirm** in the tray. Lab puts them in your agent's chat, ready for you to finish the "Change:" line and press Enter. Press **Esc** to stop selecting.
5. **Undo it.** Press **Cmd+Z** (or Undo in the preview toolbar) to step back the last change.

Then try **Tune**: click one element and type what you want; it goes straight to your agent.

---

## The workspace at a glance

When you open a project, you see:

- **The preview** in the middle: your project running live. The toolbar above it holds the **Select** button, the page picker, screen sizes and refresh.
- **The agent** on one side: a terminal running your coding agent inside the project. You can also talk to it directly here.
- **Panels** such as Tokens, Edit and Elements. Drag any panel by its header to put it on either side of the preview, stack it with another panel, or float it as its own window. Lab remembers your layout for each project.
- **The sidebar** on the left: your projects, so you can jump between them. Projects you leave keep running in the background, so coming back is instant.

---

## Three ways to change a design

All three start from the **Select** button in the preview toolbar. When Select is off, the preview behaves like a normal browser: links, menus and forms work. Turn Select on to pick elements instead. Press **Esc** at any time to turn it off.

### Tokens: an inspector for the selected element

Design tokens are the named values a project uses everywhere: its colours, fonts, text sizes, spacing and corner radius. Choose **Tokens** under Select and click an element. The **Tokens** panel shows:

- **The element's path** at the top, for example `body › main › div.card › div.card-body`. Click any part to select that element instead (handy when a click lands on an inner box).
- **One toggle: All uses | This element only.** All uses changes the token itself, so everything built on it follows. This element only changes just the selected element, in its own source file.
- **Element tab:** the element's values in sections (Spacing, Typography, Fill, Border), one line each: the property, the token it uses, and its value.
- **All tokens tab:** the tokens this element uses, then every token in the project, by type and file.

On each row you can:

- **Type a value** and press Enter (Esc cancels). Up and Down nudge it by 1, Shift by 10, keeping its unit.
- **Pick another token** from the token field. It only offers tokens of the same type (spacing for padding, colours for backgrounds), each with its value.
- **Use the nearest token**: after a value that is no token, "Nearest: spacing-3 · 12px" offers the closest one.

Values set by a library (for example daisyUI's own variables) show a small lock: changes to them always apply to this element only. Search finds rows by property, token name or value, and in All tokens also by purpose ("padding" finds spacing tokens). No AI is involved, so this is instant and costs nothing.

In the Welcome starter, every colour, font, size, space and radius is a token in `src/tokens/tokens.css`, with a light theme and a dark theme. Change a token and the whole app follows.

### Describe: pick elements, then write in your agent's chat

**Describe** is the default mode. Click elements and each one is added to a small tray at the top right of the preview, showing its component and file. Click **Confirm** and Lab puts a short list of them in your agent's chat ("I'm talking about these elements: … Change:"). It does not send: you finish the instruction there and press Enter, so you always see what goes to the agent.

### Tune: click one element, describe a change

Choose **Tune** under Select, click one element and type what you want: "make this button bigger", "use the accent colour here", "add a subtitle under this heading". Lab sends it to your agent's chat with the element's component, file and line, so the agent edits the right place instead of guessing.

---

## Undo and token cleanup

- **Undo** (Cmd+Z, or the Undo button in the preview toolbar and at the bottom of the Agent panel) steps back the last change.
- **Token cleanup.** Lab records every edit you make in the Tokens panel. Custom values (like `13px` instead of a token) are marked, with the nearest token. When you close Tokens, Lab offers to **Send to chat**: it puts a cleanup brief in your agent's input asking it to turn custom values into tokens or existing token classes without changing how anything looks. **Later** keeps the list; a reminder appears when you open Tokens or the project again, with **Discard** if you don't want it. The list lives in `.uxfold/pending-token-changes.json`, which Lab keeps out of git.

---

## Starting a project---

## Starting a project

### New Project

Click **New Project** on the home screen and choose:

- **Framework:** Next.js.
- **UI library:**
  - **shadcn/ui** (the default) starts from the **Welcome starter**: a calm, modern design with neutral greys and one accent colour, the Inter font, and a light and dark theme. Every style is a token. It includes a how-to page, a Dashboard with stat cards and a table, and a Settings form.
  - **daisyUI** starts from a daisyUI demo project.
  - **Other library:** type any other library you plan to use. Your agent is told about it, and the project starts from the shadcn/ui starter.
- **Skills:** small instruction packs that teach your agent how to work on a design project. The UxFold house skills are ticked by default (house rules, design principles, developer handoff notes). You can add others, such as accessibility guidelines, UX writing, or the ux-designer skill with the topics you pick.

Lab also writes an `AGENTS.md` file into the project. It tells every agent which framework, UI library, tokens file and skills the project uses, so the agent follows your setup from its first message.

### Bring your own project

You can also open a project that already exists on your Mac, or clone one from GitHub, from the home screen. Plain HTML sites work too: Lab serves them with its own built-in server, so they do not need Node.

The first time you open a project Lab did not create, it offers **Add UxFold skills**. It detects the framework, UI library, tokens files and preview command, lets you correct them, and adds the skills and `AGENTS.md`. It never overwrites a file that is already there.

---

## More tools

UxFold Lab is built on the open-source Ship Studio app, so it also includes a full set of everyday tools:

- **Screen sizes and every breakpoint.** Switch the preview between phone, tablet and desktop, or show every breakpoint side by side, each at its real height.
- **Visual editor.** Toggle Edit mode (**Cmd+E**) to adjust an element's styles and text directly, and browse the page's structure in the **Elements** tree.
- **Comments.** Pin comments on the preview and send them to your agent as a to-do list.
- **Branches and pull requests.** Create and switch git branches, push your work, and open a pull request with a title and description your agent writes from the changes. A visual tool helps you resolve merge conflicts.
- **Backups.** Take a snapshot of a project and roll back to it later.
- **Team.** See what teammates changed and why, who is on which branch, and the comments on the project, straight from your repository. No account needed.
- **Workflows and Inbox.** Save instructions for your agent to run on a schedule or on demand, such as "check every page for broken links each Monday". Findings arrive in your Inbox. Workflows only read your project; they never change it.
- **Languages.** For multilingual sites, switch the preview between languages and ask your agent to translate.
- **Assets.** Upload, view and delete images and other files in your project.
- **Command palette.** Press **Cmd+K** to search for any action in the app.

---

## Keyboard shortcuts

| Shortcut | What it does |
|---|---|
| **Cmd+K** | Command palette: find any action |
| **Esc** | Stop selecting elements in the preview |
| **Cmd+E** | Toggle the visual editor |
| **Cmd+I** | Toggle the inspector |
| **Cmd+Shift+S** | Screenshot the preview |
| **Cmd+N** | New window |
| **Cmd+1** to **Cmd+9** | Jump to a project in the sidebar |
| **Cmd+W** | Close the current tab |

---

## Where your files live

- **Your projects:** `~/UxFoldLab` (a folder called UxFoldLab in your home folder). Projects you open from elsewhere stay where they are.
- **Lab's notes about a project:** a hidden `.uxfold-lab` folder inside the project (layout, settings, thumbnails). Lab adds it to the project's `.gitignore`, so it is never committed.
- **App logs:** `~/Library/Logs/UxFoldLab`. Attach the newest file when you report a problem.

Your projects are ordinary folders of code. You can open them in any editor, and they work without Lab.

---

## Privacy

- UxFold Lab sends no analytics and no telemetry. Errors and crashes are written to the log folder on your Mac only.
- Your code stays on your Mac. When you ask for a change, Lab hands the request to your coding agent, which talks to its own provider (for example Anthropic for Claude Code) under your own account and that provider's terms.
- Lab only contacts the internet when you ask it to: installing a project's packages, cloning from GitHub, pushing your work, or installing skills.

---

## Troubleshooting

**macOS says the app "cannot be opened" or "is damaged".** Follow [The first time you open it](#the-first-time-you-open-it). If it still will not open, run the `xattr` command in that section.

**"No coding agent found".** Install Claude Code, Codex or OpenCode, then open Terminal, run it once (`claude`, `codex` or `opencode`) and sign in. Quit and reopen Lab.

**New Project stops while installing.** Check Node.js is installed and recent: `node --version` should print 20.9 or higher. Then try again.

**The preview stays blank.** Click refresh in the preview toolbar. If the project's dev server failed to start, its output appears in the dev server panel with the error.

**My agent changed the wrong thing.** Press **Cmd+Z** to undo, then try again with a more specific request, or pick the exact element with the path at the top of the Tokens panel or with Tune.

---

## Known issues

- **Unsigned app.** macOS asks once before opening it (see [Install](#install)). There are no automatic updates yet; download new versions from the [releases page](https://github.com/uxfold/UxFold-Lab-Latest/releases).
- **Mac only.** There is no Windows or Linux version yet.
- **Lists in the visual editor.** Copying or duplicating an element that sits inside a repeated list (for example a table row) can write broken code. Describing a change on those elements with Tune works.
- **This element only** works on elements that have their own ID in source. An element rendered inside a component is refused; pick its parent in the path instead. Repeated elements (items in a list) share one ID, so they change together.
- **Tokens limits.** The Tokens panel only reads `.css` files. Variables set in JavaScript, Sass, Less or `<style>` blocks are not listed, and a token value must fit on one line. When the same token is defined in several files or inside a media query, Tokens can pick the wrong definition to edit.
- **Team comments** travel on a git branch named `shipstudio-team`, from the app UxFold Lab is based on.
- **OpenCode users of earlier builds** may see an old `shipstudio-preview` tool next to `uxfold-preview`. Remove the old one from OpenCode's config.
- Some templates under New Project's Zip and From a URL tabs start from public Ship Studio starter repos.

---

## Feedback

Found a bug or have an idea? [Open an issue](https://github.com/uxfold/UxFold-Lab-Latest/issues) and include:

- what you did, what you expected, and what happened,
- a screenshot or screen recording if you can,
- your macOS version and whether your Mac is Apple Silicon or Intel,
- if something broke, the newest log file: in Finder press **Cmd+Shift+G**, go to `~/Library/Logs/UxFoldLab/` and attach the newest file.

---

## Credits and licenses

Made by **Karan Dhiman**. UxFold Lab is released under the MIT License (see `LICENSE`).

UxFold Lab stands on the shoulders of open-source work:

- The desktop app is based on [Ship Studio](https://github.com/ship-studio/ship-studio) by Julian Galluzzo and contributors (MIT).
- Element-scoped prompting is adapted from [Airship](https://github.com/0xnyn/airship) by Nayan Kumar (MIT).
- Element ID logic is adapted from [Onlook](https://github.com/onlook-dev/onlook), Copyright 2024 On Off, Inc. (Apache-2.0).
- The terminal uses a fork of [tauri-plugin-pty](https://crates.io/crates/tauri-plugin-pty) by Tnze (MIT).

Full license texts are in `THIRD-PARTY-LICENSES` next to this README, and in the app under **UxFold Lab > Credits and Licenses**.
