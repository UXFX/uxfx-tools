# Getting Started with UXFX Plugins

This guide takes you from nothing installed to using the UXFX plugins in Claude. No technical background needed — every step is point-and-click.

You'll set up three things:

1. **Claude Desktop** — the Claude app on your computer
2. **The UXFX marketplace** — the catalog this repository provides
3. **The plugins** — Premise and Context Engineering Training

---

## Before you start

- **A paid Claude plan.** Plugins require a paid plan (Pro, Max, Team, or Enterprise). A free account won't show the plugin features used in this guide.
- **A computer that can run Claude Desktop.** macOS 11 (Big Sur) or higher, or Windows 10 or higher.
- **A Claude account.** If you don't have one, create it at [claude.ai](https://claude.ai) before installing.

---

## Step 1: Install Claude Desktop

1. Go to the [Claude downloads page](https://claude.ai/download).
2. Click **macOS** or **Windows** to download the installer.
3. Open the downloaded file and follow the prompts to install.
4. Launch Claude — from your **Applications** folder on Mac, or the **Start menu** on Windows.
5. Sign in with your Claude account.

That's the app itself done. Now connect it to the UXFX plugins.

---

## Step 2: Add the UXFX marketplace

Plugins come from marketplaces — catalogs you connect to Claude. This repository is one. Add it once and both plugins become available to install.

1. In Claude Desktop, open the **Customize** menu in the left sidebar.
2. Open the **Plugins** tab.
3. In the **Personal plugins** section, click the **+** button, then select **Add marketplace**.
4. Choose **Add from a repository** and enter:

   ```
   https://github.com/UXFX/uxfx-tools
   ```

5. Confirm. The UXFX marketplace now appears in your plugins list.

---

## Step 3: Install the plugins

1. Still in the **Plugins** tab, click **Browse plugins**.
2. Find the UXFX plugins and click **Install** on each one you want:
   - **premise** — a thinking partner for work you've been handed
   - **context-engineering-training** — a 9-session course on working with Claude

You can install one or both. Each is independent.

---

## Step 4: Your first session with Premise

Premise helps when someone hands you a piece of work — a project, a deliverable, an assignment — and you don't yet understand why it exists or where to begin. It separates what you actually know from what you're assuming, then produces a **Launch Brief**: your understanding of the work plus a plan to attack it.

To try it:

1. Start a new conversation.
2. Type **/** and select **premise** from the menu — or just describe your situation in plain words:

   > "I was handed a project at work and I'm not sure what it's really for. Help me make sense of it before I start."

3. Answer the questions it asks. It will challenge your assumptions — that's the point.
4. You'll finish with a Launch Brief: what the work is, why it exists, and how you'd attack it.

Premise is a launch tool, not a run tool. It gets you to the starting line with a plan, then hands off.

---

## Step 5: Your first session with Context Engineering Training

This is a hands-on course, taught by Claude, on getting real work out of Claude — from first principles through a fully productionized workflow of your own. Nine sessions, each building on the last. You don't read about the concepts; you use them on a real workflow you choose in Session 1.

To begin:

1. Start a new conversation.
2. Type:

   > start training

3. The course welcomes you, sets up your workspace, and walks you through Session 0 (settings and orientation).

Useful phrases as you go:

- **"continue"** — pick up where you left off (sessions are designed to span multiple conversations)
- **"status"** — see your progress and current position
- **"show portal"** — generate a visual progress page

The course will tell you when a session needs **Cowork** — Claude Desktop's mode for working with files and multi-step tasks (you'll find it as the Cowork tab in the app). Early sessions run in regular chat; you don't need to set up anything extra on day one.

---

## Updating plugins to new versions

These plugins improve over time. When a new version ships, your installed copy doesn't update by itself — you refresh the marketplace to pull it in.

1. In Claude Desktop, open **Customize** → **Plugins**.
2. Find the **uxfx-tools** marketplace in your Personal plugins section.
3. Open its menu and choose **Update**. This re-syncs the marketplace with the latest published version from this repository.
4. Check the plugin's version number to confirm it changed (current versions are listed on each plugin's page).

If the update doesn't seem to take effect, the reliable fallback is: remove the marketplace (menu → **Remove**), then add it again following Step 2, and reinstall the plugins. Your conversations are not affected — removing a plugin only removes the tool, never your chat history.

**Tip:** when an update announcement mentions a version number (for example, premise 1.2.0), compare it against what your Plugins tab shows after updating. If they match, you're current.

---

## Troubleshooting

- **No Plugins tab or Customize menu?** Check that you're signed in with a paid plan account. Plugins aren't available on the free plan.
- **Marketplace won't add?** Re-check the URL — it must be exactly `https://github.com/UXFX/uxfx-tools`.
- **A skill doesn't appear when typing "/"?** Confirm the plugin shows as installed under Customize → Plugins, and start a fresh conversation.

Questions or problems with the plugins themselves: **dale@uxfx.io**
