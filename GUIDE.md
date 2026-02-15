# 🎮 DSMP AFK Bot Manager — Complete Beginner's Guide

> **Welcome!** This guide will walk you through every single feature of the Bot Control Center dashboard — from your very first launch to advanced features. No prior knowledge needed.

---

## 📑 Table of Contents

1. [What Is This Program?](#1--what-is-this-program)
2. [Getting Started](#2--getting-started)
3. [Understanding the Layout](#3--understanding-the-layout)
4. [The Left Sidebar (Controls)](#4--the-left-sidebar-controls)
   - [Add Account](#41--add-account)
   - [Bot Controls](#42--bot-controls)
   - [Scraping & Data](#43--scraping--data)
   - [Mass Messaging](#44--mass-messaging)
   - [Files & Tools](#45--files--tools)
   - [Footer Buttons](#46--footer-buttons-ui-settings--performance)
5. [The Main Area (Bot Cards)](#5--the-main-area-bot-cards)
   - [Tabs: Online / Disconnected / Starting](#51--tabs)
   - [Bot Card Anatomy](#52--bot-card-anatomy)
   - [Per-Bot Buttons Explained](#53--every-per-bot-button-explained)
   - [Multi-Select & Drag to Page](#54--multi-select--drag-to-page)
6. [The Right Sidebar (Pages)](#6--the-right-sidebar-pages)
7. [Modals & Popups](#7--modals--popups)
   - [Performance Settings Modal](#71--performance-settings-modal)
   - [Proxy Manager](#72--proxy-manager)
   - [Shop Modal](#73--shop-modal)
   - [Stats Modal](#74--stats-modal)
   - [Inventory Modal](#75--inventory-modal)
   - [Live Camera Viewer](#76--live-camera-viewer)
   - [Scrape Mode Selector](#77--scrape-mode-selector)
   - [Long Scrape Tracker](#78--long-scrape-tracker)
   - [File Editor Modals](#79--file-editor-modals)
8. [Configuration Files](#8--configuration-files)
9. [Page-Scoped vs Global Actions](#9--page-scoped-vs-global-actions)
10. [Tips & Troubleshooting](#10--tips--troubleshooting)
11. [Keyboard Shortcuts](#11--keyboard-shortcuts)
12. [Glossary](#12--glossary)

---

## 1. 🧩 What Is This Program?

This is a **web-based control panel** for managing Minecraft bot accounts on DonutSMP. It can:

- ✅ Connect multiple Minecraft accounts (Java & Bedrock) to the server
- ✅ Keep bots AFK (away from keyboard) to farm resources
- ✅ Scrape player names from the server
- ✅ Send mass messages to scraped players
- ✅ Manage money, shards, and in-game shops
- ✅ Use proxies to hide your IP and connect more bots
- ✅ Organize bots into pages for easy management

Think of it as a **mission control center** for all your Minecraft bots.

---

## 2. 🚀 Getting Started

### Step 1: Install Dependencies

Open a terminal in the `main` folder and run:

```
npm install
```

This installs all required packages (Express, Socket.IO, Mineflayer, etc.).

### Step 2: Start the Manager

```
node manager.js
```

You'll see:
```
🚀 DASHBOARD ONLINE: http://localhost:3000
```

### Step 3: Open the Dashboard

Open your browser and go to **http://localhost:3000**. That's it — you'll see the Bot Control Center!

### Step 4: Add Your First Bot

In the left sidebar under **Add Account**:
1. Type your Microsoft email (or `email:password` combo)
2. Type the password (if not included above)
3. Pick an edition (Java, Bedrock, or Both)
4. Click **⚡ Start Auth & Spawn**

The bot will appear in the **Starting** tab, then move to **Online** once connected.

> 💡 **First Time?** A browser window may open asking you to sign into Microsoft. This is normal — it's authenticating your Minecraft account.

---

## 3. 🗺️ Understanding the Layout

The dashboard has three main areas:

```
┌──────────────┬─────────────────────────────┬──────────┐
│              │                             │          │
│   LEFT       │       MAIN AREA             │  RIGHT   │
│   SIDEBAR    │    (Bot Cards Grid)         │  SIDEBAR │
│              │                             │  (Pages) │
│  Controls    │  ┌─────┬──────┬─────────┐   │          │
│  & Actions   │  │ On  │ Disc │ Starting│   │          │
│              │  └─────┴──────┴─────────┘   │          │
│              │                             │          │
│              │  [Bot] [Bot] [Bot]          │          │
│              │  [Bot] [Bot] [Bot]          │          │
│              │                             │          │
└──────────────┴─────────────────────────────┴──────────┘
```

| Area | What It Does |
|------|-------------|
| **Left Sidebar** | All controls: add bots, movement, economy, messaging, scraping, files, settings |
| **Main Area** | Displays your bot cards in a grid, with Online/Disconnected/Starting tabs |
| **Right Sidebar** | Page system for organizing bots into groups |

Both sidebars can be **hidden/shown** using the arrow toggle buttons on their edges.

---

## 4. 📋 The Left Sidebar (Controls)

The sidebar is organized into **collapsible accordion sections**. Click any section header to expand or collapse it. Your open/closed preference is saved automatically.

---

### 4.1 ➕ Add Account

This is where you bring new bots into the system.

#### Single Account

| Field | What to Enter |
|-------|--------------|
| **Email** | Your Microsoft email, OR an `email:password` combo (e.g. `user@mail.com:MyPass123`) |
| **Password** | The password (leave blank if you used the combo format above) |
| **Edition** | ☕ Java, 🔷 Bedrock, or 🎯 Both (creates one of each) |
| **Proxy** | Optional — pick a proxy from the dropdown, or leave as "No Proxy (Direct)" |

Click **⚡ Start Auth & Spawn** to connect.

#### 📦 Bulk Import (Email:Pass)

For adding many accounts at once:
1. Expand this sub-section
2. Paste accounts, one per line: `email:password`
3. Choose the edition (Java/Bedrock/Both)
4. Click **Import All Accounts**

All accounts authenticate and spawn sequentially.

#### 🎫 Bulk Import (JWT Tokens)

If you have raw JWT authentication tokens:
1. Expand this sub-section
2. Paste tokens, one per line (they start with `eyJ...`)
3. Click **Import JWT Tokens**

Each token is imported with a 2-second delay between them.

---

### 4.2 🎮 Bot Controls

These buttons send commands to **all bots on the current page** (unless bots are multi-selected, in which case only selected bots are affected).

#### 🏃 Movement

| Button | What It Does |
|--------|-------------|
| **▶ Start Jump** | All bots begin jumping continuously |
| **⏹ Stop Jump** | Stop the jumping |
| **▶ Auto Move** | All bots walk forward endlessly |
| **⏹ Stop Move** | Stop moving |
| **▶ Start Eat** | All bots eat food from their hotbar |
| **⏹ Stop Eat** | Stop eating |

> 💡 Movement actions keep bots from being kicked for inactivity (AFK).

#### 💰 Economy

| Button | What It Does |
|--------|-------------|
| **💎 Check Shards** | Each bot checks its shard balance (logged in bot console) |
| **💵 Check Money** | Each bot checks its money balance |

**💸 Pay All Bots To:**
1. Type a username in the text field
2. Click **Send All Money**
3. Confirm the popup
4. Every online bot on the current page sends all their money to that player

#### 💬 Communication

| Button | What It Does |
|--------|-------------|
| **💬 Global Chat** | A popup asks for a message → all online bots on the current page send it in-game chat |

#### 👁️ Display

| Button | What It Does |
|--------|-------------|
| **📊 Show All Stats** | Replaces bot card buttons with a stats view (Money, Shards, Playtime, Deaths). Click again to go back to **🎮 Show Controls** |
| **👁️ Show Passwords** | Reveals the password portion of email:password on all bot cards on this page. Click again to **🔒 Hide Passwords** |

> 📌 These are **per-page** — toggling on Page 1 doesn't affect Page 2.

#### 🔌 Connection

| Button | What It Does |
|--------|-------------|
| **🔄 Auto Reconnect All** | Toggles auto-reconnect for all bots on the current page. If ANY bot has it off, it turns all ON. If all are already on, turns all OFF. |
| **⚠️ DISCONNECT ALL** | Immediately disconnects every online bot on this page |

---

### 4.3 🔍 Scraping & Data

Scraping = automatically discovering player usernames from the Minecraft server.

| Button | What It Does |
|--------|-------------|
| **📋 Global Scrape** | Opens the [Scrape Mode Selector](#77--scrape-mode-selector). You can choose Fast/Long/Triple scrape and whether to use All Bots or just Current Page bots. |
| **⛔ Stop Scrape** | Stops any active scrape. Works globally across ALL pages. |
| **🔑 Extract APIs** | Runs `/api` on all online bots on the current page and saves the API keys to `APIs.txt`. |
| **🧹 Dedupe APIs** | Removes duplicate API keys from `APIs.txt` (creates a backup first). |
| **🔍 Filter Players (Online Only)** | Checks which scraped players are actually online right now and removes offline ones from `scraped_players.txt`. |

#### ⏰ Auto Re-Scrape

- Set an interval (in minutes) in the number box
- Click the **⏰ OFF** button to toggle it ON
- When ON, scraping automatically restarts every X minutes
- Works globally (any bot currently scraping, regardless of page)

#### ♾️ Infinite Scrape

- When ON, scraping never stops — it loops back to the beginning when finished
- Works globally for any bot doing scrape

---

### 4.4 📬 Mass Messaging

Send automated messages to scraped player names.

#### ⏱️ Delay

Set the delay (in seconds) between each message. Lower = faster, but higher risk of being rate-limited.

| Button | What It Does |
|--------|-------------|
| **▶ Start Spam** | Begin sending messages from your `messages.txt` to scraped players |
| **⏹ Stop Spam** | Stop all spam immediately |
| **🔄 Auto-Resume: OFF/ON** | If a bot disconnects and reconnects, automatically resume spamming |
| **♾️ Infinite Spam: OFF/ON** | When ON, spam loops back to the start after going through all players |

> 💡 Messages are loaded from `messages.txt`. Scraped targets come from `scraped_players.txt`. Edit both via the **Files & Tools** section.

---

### 4.5 📁 Files & Tools

| Button | What It Opens |
|--------|--------------|
| **📄 Edit Scraped Players** | Text editor for `scraped_players.txt` — the list of player names to message |
| **📄 Edit Messages** | Text editor for `messages.txt` — the messages your bots send |
| **🌐 Proxy Manager** | Full proxy management panel (see [Proxy Manager](#72--proxy-manager)) |
| **🔍 Long Scrape Tracker** | Visual combo tracker showing scrape progress (see [Long Scrape Tracker](#78--long-scrape-tracker)) |

---

### 4.6 🔧 Footer Buttons (UI Settings & Performance)

At the very bottom of the sidebar, you'll find two buttons:

#### 🎨 UI Settings

Click to expand a settings panel with three sliders:

| Slider | What It Controls | Range |
|--------|-----------------|-------|
| **Card Height** | How tall each bot card is | 30 – 200 |
| **Console Height** | How tall the log console area inside each card is | 100 – 600 |
| **Bots Per Row** | How many bot cards fit in one row | 1 – 6 |

> 💡 These settings are saved **per tab** (Online, Disconnected, Starting can have different layouts).

#### ⚡ Performance

Opens a full settings modal — see [Performance Settings Modal](#71--performance-settings-modal).

---

## 5. 🃏 The Main Area (Bot Cards)

---

### 5.1 📑 Tabs

The top of the main area has three tabs:

| Tab | Shows | Dot Color |
|-----|-------|-----------|
| **Online** | Bots currently connected and in-game | 🟢 Green |
| **Disconnected** | Bots that are offline, failed, or banned | 🔴 Red |
| **Starting** | Bots currently in the process of connecting | 🟡 Yellow |

Each tab shows a **count badge** (e.g., `Online 5`) that only counts bots on the **current page**.

---

### 5.2 🃏 Bot Card Anatomy

Each bot is displayed as a card. Here's what each part means:

```
┌─────────────────────────────────────┐
│ ☕ PlayerName123    proxy-label  🟢 │  ← Row 1: Edition icon, Username, Proxy, Status
│ user@email.com  👁 📋 📎           │  ← Row 2: Email, Eye (toggle pass), Copy, Move-to-page
│ Health: ████████████░░ 17/20        │  ← Health bar
├─────────────────────────────────────┤
│ [Bot console log output...]         │  ← Mini console (shows in-game events)
│ > Connected to donutsmp.net         │
│ > Balance: $1,234                   │
├─────────────────────────────────────┤
│ [💬 Chat] [👀 View] [🎒 Inv] ...   │  ← Action buttons (configurable)
└─────────────────────────────────────┘
```

**Row 1 — Header:**
- **Edition Icon**: ☕ = Java, ⛏ = Bedrock
- **Username**: The bot's Minecraft username (click 📋 to copy)
- **Proxy Label**: Shows which proxy this bot uses (if any)
- **Status Badge**: 🟢 Online, 🔴 Disconnected, 🟡 Starting, etc.

**Row 2 — Info:**
- **Email**: The account email (or `email:password` when passwords are visible)
- **👁 Eye Button**: Toggle password visibility for just this bot
- **📋 Copy Username**: Copies the username to clipboard
- **📎 Copy Credentials**: Copies `email` or `email:password` depending on visibility
- **Page Dropdown**: Move this bot to a different page (only shows when you have 2+ pages)

**Console**: A live log showing everything the bot sees in-game — chat messages, money checks, errors, etc.

**Disconnected Cards** show different buttons:
- A proxy dropdown to reassign the bot's proxy
- Auto Reconnect toggle
- ⚡ Retry (reconnect)
- 🔄 Remove (remove from list, keep account)
- 🗑️ Delete (permanently delete account)

---

### 5.3 🎮 Every Per-Bot Button Explained

Online bot cards have a configurable button grid. Here is every possible button:

| Button | What It Does |
|--------|-------------|
| **💬 Chat** | Opens a popup to type a message. The bot sends it in-game chat. |
| **👀 View** | Opens the [Live Camera Viewer](#76--live-camera-viewer) — see through the bot's eyes in 3D |
| **🎒 Inv** | Opens the [Inventory Modal](#75--inventory-modal) showing the bot's items |
| **📋 Scrape** | Opens the Scrape Mode selector for this specific bot only |
| **📧 Spam** | Opens a spam modal to start messaging from this bot |
| **🛑 Stop** | Stops spam messaging for this bot |
| **💰 Money** | Bot runs `/money` and shows its balance in the console |
| **✨ Shards** | Bot runs `/shards` and shows its shard balance |
| **⬆ Jump** | Bot starts jumping |
| **⬇ No Jump** | Bot stops jumping |
| **🏃 Walk** | Bot starts walking forward |
| **🛑 No Walk** | Bot stops walking |
| **🍖 Eat** | Bot starts eating food |
| **🚫 No Eat** | Bot stops eating |
| **📊 Stats** | Opens the [Stats Modal](#74--stats-modal) for this bot |
| **🛑 Disc** | Disconnects this bot (asks for confirmation) |
| **🔄 Restart** | Disconnects and immediately reconnects the bot |
| **🔄 Auto** | Toggle auto-reconnect for this specific bot |
| **🗑️ Delete** | Permanently deletes this account (asks for confirmation) |
| **🟣 E-Chest** | Places an ender chest |
| **📦 Shulker** | Places a shulker box |
| **⛏️ Mine** | Mines a shulker box |
| **❌ Close** | Closes the currently open container/window |
| **🛍️ Shop** | Opens the in-game [Shop Modal](#73--shop-modal) |
| **⚙️ Set** | Opens the bot's in-game settings menu |
| **🔄 Auto Buy** | Toggles automatic purchasing from the shard shop (with item dropdown) |
| **✅ TPAccept** | Accepts a pending teleport request |
| **🚀 TPA** | Asks for a player name, then sends `/tpa <name>` |
| **👇 TPA Here** | Asks for a player name, then sends `/tpahere <name>` |

#### Customizing Buttons

Open **⚡ Performance** (bottom of sidebar) → scroll to **🎨 Bot Buttons**:
- **Click** any button to show/hide it on all cards
- **Drag** buttons to reorder them
- Click **🔄 Reset to Default** to go back to the original layout

Your button configuration is saved server-side and persists across restarts.

---

### 5.4 🖱️ Multi-Select & Drag to Page

#### Selecting Bots

| Action | How |
|--------|-----|
| **Select one bot** | Click its header area (the drag handle) |
| **Add/remove from selection** | **Ctrl + Click** (or **Cmd + Click** on Mac) |
| **Select a range** | Click one bot, then **Shift + Click** another — selects everything in between |
| **Select all on page** | Click **☑ Select All** in the blue selection bar |
| **Clear selection** | Click **✕ Clear** in the selection bar, or click an empty area |

When bots are selected:
- A **blue selection bar** appears below the tabs showing the count
- All sidebar commands (movement, economy, etc.) apply only to **selected bots** instead of all page bots

#### Moving Bots to Another Page

1. Select one or more bots
2. **Drag** a selected bot's header toward the right sidebar
3. **Drop** it onto a page tab in the Pages sidebar
4. All selected bots move to that page

You can also use the **page dropdown** on each card's info row for individual moves.

---

## 6. 📄 The Right Sidebar (Pages)

Pages let you **organize bots into groups** — like folders for your bots.

### How Pages Work

- Every bot starts on the **Main** page
- You can create custom pages (e.g., "AFK Shards", "Spammers", "Money Farm")
- The **current page** determines which bots you see in the main grid
- Sidebar controls like movement, pay, chat, etc. only affect **bots on the current page**

### Page Controls

| Action | How |
|--------|-----|
| **Create a page** | Click the **+** button in the Pages header |
| **Switch page** | Click any page name in the list |
| **Rename a page** | Right-click or use the rename option |
| **Delete a page** | Use the delete option (bots move back to Main) |

The current page name is shown at the bottom of the Pages sidebar.

> 💡 Your last active page is remembered across browser refreshes.

---

## 7. 📦 Modals & Popups

---

### 7.1 ⚡ Performance Settings Modal

Opened via the **⚡ Performance** button at the bottom of the sidebar.

#### ⚡ Performance Toggles

| Setting | What It Does | Recommendation |
|---------|-------------|----------------|
| **🔭 Reduce View Distance** | Limits each bot's vision to 2 chunks. Saves ~60-70% RAM. | ✅ Recommended ON |
| **🎯 Disable Physics** | Skips gravity and movement calculations. Saves ~30% CPU. | ✅ Safe to enable |
| **📦 Web Inventory** | Enables the inventory viewer feature. Disable to save resources. | ⚠️ Reconnect bots after changing |

> 📌 These only apply to **new connections**. You must reconnect bots for changes to take effect.

#### 🔔 Notifications

| Setting | What It Does |
|---------|-------------|
| **🔔 Show Notifications** | Enables/disables the small toast popups that appear in the bottom-right corner |

#### 🚀 Startup

| Setting | What It Does |
|---------|-------------|
| **🔌 Auto-Connect on Startup** | When the manager starts, all saved accounts automatically connect |

#### 🔧 Scraping Tuning

Two sliders to fine-tune scraping performance:

| Slider | What It Controls | Range |
|--------|-----------------|-------|
| **⏱️ Tab-Complete Timeout** | How long to wait for the server to respond to each scrape query | 5s (fast) → 30s (safe) |
| **⏸️ Delay Between Combos** | Pause between each scrape request (prevents rate-limiting) | 500ms (fast) → 3000ms (safe) |

> 💡 Getting timeout errors? **Increase the timeout**. Getting rate-limited? **Increase the delay**.

#### 🎨 Bot Buttons

A visual grid showing all possible per-bot buttons:
- **Click** a button to toggle it on/off
- **Drag** buttons to reorder them
- Changes apply instantly to all bot cards

---

### 7.2 🌐 Proxy Manager

Opened via **Files & Tools → 🌐 Proxy Manager**.

Proxies route bot connections through different IP addresses, which helps avoid bans and lets you connect more bots.

#### Adding Proxies

**Single proxy:**
1. Fill in: Name, Type (SOCKS5/SOCKS4/HTTP/HTTPS), Host, Port
2. Optionally add Username and Password (for authenticated proxies)
3. Click **➕ Add Proxy**

**Bulk add:**
1. Click the **Bulk Add** tab
2. Paste proxies, one per line. Supported formats:
   - `host:port`
   - `host:port:username:password`
   - `type://host:port`
   - `type://username:password@host:port`
3. Click **Import All**

#### Testing Proxies

| Button | What It Does |
|--------|-------------|
| **Test All** | Tests every proxy and shows latency |
| **Test Selected** | Tests only the proxies you've clicked to select |

Working proxies show a ✅ green dot and latency (e.g., `145ms`). Failed ones show ❌ red.

#### Proxy Cards

Each proxy card shows:
- Proxy name and type badge
- Authentication status (🔐 if using username/password)
- **Usage count** — how many bots are currently using this proxy
- Status dot and latency

#### Managing Proxies

- **Click** proxy cards to multi-select them
- **Delete Selected** / **Delete All Failed** / **Delete All** buttons in the top toolbar
- A **Select All** checkbox in the stats bar

#### Assigning Proxies to Bots

- When adding a new bot, pick a proxy from the dropdown in the Add Account section
- For disconnected bots, each card has its own proxy dropdown
- Proxy assignments are saved and persist across restarts

---

### 7.3 🛍️ Shop Modal

Opened via the **🛍️ Shop** button on a bot card.

This lets you buy items from the in-game server shop through the UI.

1. **Main Menu** — Shows shop categories
2. **Category View** — Lists items with their prices
3. **Purchase Menu**:
   - For shard items: Simple confirm/cancel
   - For money items: Quantity selector with ±1, ±10, ±64 buttons, live total cost display, and balance verification

Your current balance is displayed at the top of the modal.

---

### 7.4 📊 Stats Modal

Opened via the **📊 Stats** button on a bot card, or by enabling **Show All Stats** in the sidebar.

Shows four stats in a grid:
- 💰 **Money** — In-game currency balance
- 💎 **Shards** — Shard balance
- ⏱️ **Playtime** — Total time played
- 💀 **Deaths** — Total death count

---

### 7.5 🎒 Inventory Modal

Opened via the **🎒 Inv** button on a bot card.

Shows the bot's current inventory as a visual grid of item slots. You can also open a **separate browser window** with a more detailed web-based inventory view.

> 📌 Requires "Web Inventory" to be enabled in Performance Settings. Bots must be reconnected after enabling.

---

### 7.6 👀 Live Camera Viewer

Opened via the **👀 View** button on a bot card.

A 3D Prismarine Viewer showing a live view of the game world from the bot's perspective.

| Feature | How |
|---------|-----|
| **Toggle Perspective** | Click **🎥 TOGGLE 1ST/3RD** to switch between first and third person |
| **Enable Controls** | Click **🎮 ENABLE CONTROLS** to take manual control |

When controls are enabled:
| Key | Action |
|-----|--------|
| **W** | Move forward |
| **S** | Move backward |
| **A** | Move left |
| **D** | Move right |
| **Space** | Jump |
| **Left Shift** | Sprint |
| **Mouse** | Look around (after clicking to lock cursor) |
| **Left Click** | Attack/mine |
| **Right Click** | Use/place |
| **ESC** | Unlock mouse cursor |

---

### 7.7 🔍 Scrape Mode Selector

Opened when you click **📋 Global Scrape** (sidebar) or **📋 Scrape** (per-bot button).

#### Scope Toggle (Global Scrape only)

When opened from the sidebar, you'll see a **SCRAPE SCOPE** toggle at the top:
- **🌐 All Bots** — Uses any available online bot for scraping
- **📄 Current Page** — Only uses bots on the current page

#### Scrape Modes

| Mode | Combos | Speed | Description |
|------|--------|-------|-------------|
| **⚡ Fast Scrape** | ~38 | ~20 seconds | Checks single characters (a-z, 0-9, _, .) |
| **🔥 Long Scrape** | ~1,444 | Minutes | Checks double characters (aa-zz, a0-z9, etc.) |
| **🔥🔥 Triple Combo** | ~53,503 | Long time | Checks triple characters (abc, xyz, 123, .ab, etc.) |

For Long and Triple scrapes, a second popup asks **how many bots to use** (more bots = faster) and shows an **estimated time** based on your delay setting.

---

### 7.8 🔍 Long Scrape Tracker

Opened via **Files & Tools → 🔍 Long Scrape Tracker**.

A **visual dashboard** for monitoring long/triple scrape progress.

**Stats bar at top:**
- Total combos, Completed ✅, In Progress 🔄, Pending ⏳, Failed ❌, Empty ⚪, Players Found 👥

**Visual grid:**
Each combo is a tiny colored cell:
- ⬜ Gray = Pending (not started)
- 🟨 Yellow = In Progress
- 🟩 Green = Completed (found players)
- 🟥 Red = Failed
- ⬛ Dark gray = Empty (no players found)

For triple combos, cells are **grouped by first character** (A-group, B-group, etc.) and can be expanded/collapsed to prevent performance issues.

---

### 7.9 📝 File Editor Modals

Opened via **Files & Tools → Edit Scraped Players** or **Edit Messages**.

A simple text editor where you can:
1. View the current contents of the file
2. Edit the text
3. Click **💾 Save Changes** to save
4. Click **Cancel** to discard changes

---

## 8. ⚙️ Configuration Files

The program uses several text files in the `main` folder:

| File | Purpose |
|------|---------|
| `config.json` | Master config — all settings, proxy data, page layouts, bot assignments |
| `new_accounts.txt` | List of accounts (email:password) to connect |
| `messages.txt` | Spam messages — one message per line. Use `[random_id]` for random prefixes. |
| `scraped_players.txt` | List of player names found by scraping |
| `scraped_logs.txt` | Raw scrape log — all player names ever found |
| `APIs.txt` | Extracted API keys |
| `filter.txt` | Username filter list |
| `proxies.txt` | Proxy list (managed via the Proxy Manager UI) |
| `deleted_accounts.txt` | Accounts you've deleted (for reference) |

> 💡 You rarely need to edit these manually — the dashboard UI handles everything.

---

## 9. 🎯 Page-Scoped vs Global Actions

Some buttons affect only the **current page's bots**, while others work **globally** across all pages.

### Current Page Only (affect bots on your active page)

| Action | Notes |
|--------|-------|
| All Movement (Jump, Walk, Eat) | Only bots on current page |
| 💬 Global Chat | Only bots on current page |
| 💸 Send All Money | Only bots on current page |
| 📊 Show All Stats | Per-page toggle (independent per page) |
| 👁️ Show Passwords | Per-page toggle (independent per page) |
| 🔄 Auto Reconnect All | Only bots on current page |
| 🔑 Extract APIs | Only bots on current page |
| ⚠️ Disconnect All | Only bots on current page |
| All Economy (Check Shards/Money) | Only bots on current page |
| ▶ Start Spam / ⏹ Stop Spam | Only bots on current page |

### Global (affect all bots regardless of page)

| Action | Notes |
|--------|-------|
| ⛔ Stop Scrape | Stops scraping on ALL bots |
| ⏰ Auto Re-Scrape | Works for any bot doing scrape |
| ♾️ Infinite Scrape | Works for any bot doing scrape |
| 🔄 Auto-Resume Spam | Works for any bot spamming |
| ♾️ Infinite Spam | Works for any bot spamming |

### User's Choice (you pick the scope)

| Action | Notes |
|--------|-------|
| 📋 Global Scrape | Scope toggle: "All Bots" or "Current Page" |

### Multi-Select Override

When you have bots **selected** (blue highlight), all current-page commands target **only the selected bots** instead of all page bots.

---

## 10. 💡 Tips & Troubleshooting

### General Tips

- **Reduce View Distance** is the single biggest performance saver — enable it in Performance Settings
- **Disable Physics** is safe to enable and saves CPU
- Use **pages** to organize bots by purpose (AFK, Spamming, Money farming)
- Keep the **Bots Per Row** at 3-4 for the best balance of visibility and info
- Use **Ctrl+Click** and **Shift+Click** for efficient multi-select

### Common Issues

| Problem | Solution |
|---------|----------|
| Bot stuck on "Starting" | Wait 30 seconds. If still stuck, disconnect and retry. |
| "Already Online" error | The account is logged in elsewhere. Wait a minute and retry. |
| Bots disconnecting frequently | Enable **Auto Reconnect**. Check your proxy if using one. |
| Scrape finding 0 players | Increase the **Tab-Complete Timeout** in Performance Settings |
| Getting rate-limited while scraping | Increase the **Delay Between Combos** slider |
| Spam messages not sending | Make sure `messages.txt` has content and `scraped_players.txt` has target names |
| High RAM usage | Enable **Reduce View Distance** and disable **Web Inventory** |
| Proxy not working | Test it in the Proxy Manager. Red = dead proxy, replace it. |
| Can't see inventory | Enable **Web Inventory** in Performance Settings, then reconnect the bot |
| Dashboard not loading | Make sure `node manager.js` is running. Check http://localhost:3000 |

---

## 11. ⌨️ Keyboard Shortcuts

| Key | Where | Action |
|-----|-------|--------|
| **Ctrl + Click** | Bot card header | Add/remove bot from selection |
| **Shift + Click** | Bot card header | Select range of bots |
| **WASD** | Camera Viewer (controls enabled) | Move bot |
| **Space** | Camera Viewer (controls enabled) | Jump |
| **Left Shift** | Camera Viewer (controls enabled) | Sprint |
| **ESC** | Camera Viewer | Unlock mouse cursor |
| **Mouse Click** | Camera Viewer | Lock cursor for look-around |

---

## 12. 📖 Glossary

| Term | Meaning |
|------|---------|
| **AFK** | Away From Keyboard — keeping bots connected without doing anything manually |
| **Bot** | A Minecraft account controlled automatically by this program |
| **Scraping** | Automatically discovering player usernames on the server via tab-completion |
| **Spam** | Sending automated private messages to scraped players |
| **Proxy** | A middleman server that hides your real IP address |
| **SOCKS5** | A type of proxy protocol (most common for Minecraft) |
| **JWT** | JSON Web Token — a type of authentication token |
| **Shard** | An in-game currency on DonutSMP |
| **Combo** | A character combination used during scraping (e.g., "aa", "ab", "abc") |
| **Tab-Complete** | The Minecraft feature used to discover player names (pressing Tab in chat) |
| **Page** | A named group/folder for organizing your bots |
| **Edition** | Java Edition or Bedrock Edition of Minecraft |
| **Auto Reconnect** | Automatically reconnects a bot if it gets disconnected |
| **Auto Buy** | Automatically purchases a specific item from the shard shop on repeat |
| **Rate-Limited** | When the server blocks your requests because you're sending too many too fast |

---

> **🎉 That's everything!** You now know every feature of the Bot Control Center. Happy botting! 🤖
