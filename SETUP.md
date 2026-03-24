# Receipt Logger — Setup Guide

## What it does
PWA on your iPhone home screen. Tap a category, pick a photo, it fires an Apple Shortcut that saves the receipt to iCloud Drive → `Obsidian Receipts/<category>/`.

---

## Step 1 — Create the iCloud folders

In the Files app on your iPhone:
1. Go to **iCloud Drive**
2. Create a folder called `Obsidian Receipts`
3. Inside it, create these subfolders:
   - `groceries`
   - `fuel`
   - `bills`
   - `misc`

---

## Step 2 — Build the Shortcuts (one per category)

Do this once for each category. Example for **Groceries** — repeat for fuel, bills, misc.

1. Open the **Shortcuts** app
2. Tap **+** to create a new shortcut
3. Name it exactly: `Receipt - Groceries`
4. Add these actions in order:

   **Action 1: Get Latest Photo**
   - From: Photo Library
   - Count: 1

   **Action 2: Rename File**
   - File: (Shortcut Input — the filename passed from the app)
   - Or just use: `Receipt Input` → use the text passed in

   **Action 3: Save File**
   - File: (result of Get Latest Photo)
   - Destination: iCloud Drive → Obsidian Receipts → groceries
   - Overwrite: ON

5. Repeat for:
   - `Receipt - Fuel` → saves to `fuel/`
   - `Receipt - Bills` → saves to `bills/`
   - `Receipt - Misc` → saves to `misc/`

> For custom categories you add later: create a new Shortcut named `Receipt - Categoryname` saving to a matching subfolder.

---

## Step 3 — Get the PWA on your home screen

The HTML file lives in your vault at:
`06 META/Tools/receipt-logger/index.html`

**Easiest way to host it locally on your phone:**

Option A — Via Obsidian (simplest):
1. Open Obsidian on iPhone
2. Navigate to `06 META/Tools/receipt-logger/index.html`
3. Tap to open — it won't render, but that's OK for now

Option B — Host it on your Mac (recommended):
1. On your Mac run: `python3 -m http.server 8080 --directory "/Users/ne555n/Documents/OBSIDIAN/My Computer/06 META/Tools/receipt-logger"`
2. On your iPhone (same WiFi): open Safari → `http://[your-mac-local-ip]:8080`
3. Tap Share → **Add to Home Screen**
4. Name it `Receipts`

To find your Mac's local IP: System Settings → Wi-Fi → Details → IP Address

> Once added to home screen it works offline — no server needed after that.

---

## Step 4 — How to use it

1. Tap the **Receipts** icon on your home screen
2. Tap a category
3. Tap **Select Photo**
4. Choose your receipt photo from camera roll (or snap one)
5. App opens the matching Shortcut
6. Shortcut saves it to iCloud Drive → right folder
7. App returns, shows ✓ confirmation

---

## Accessing receipts from your Mac

iCloud Drive syncs to: `~/Library/Mobile Documents/com~apple~CloudDocs/Obsidian Receipts/`

During `/budget` check-ins Claude will read from there to update your price log.

