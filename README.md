# Daily Bible Reading

A simple web app for your church's Bible reading plan. Members can read or listen to daily passages (ESV), track their progress, and switch between multiple plans.

---

## Quick Start (First-Time Setup)

### 1. Get an ESV API Key
- Go to [api.esv.org](https://api.esv.org/)
- Click "Sign Up" and create a free account
- Your API key will be emailed to you (usually same day)

### 2. Create a GitHub Repository
- Go to [github.com/new](https://github.com/new)
- Name it something like `bible-reading` or `daily-reading`
- Set it to **Public** (required for free GitHub Pages hosting)
- Click **Create repository**

### 3. Upload the Files
- On your new repository page, click **"uploading an existing file"**
- Drag and drop ALL of these files/folders:
  - `index.html`
  - `config.js`
  - `manifest.json`
  - `plans/` folder (with the JSON files inside)
  - `README.md`
- Click **Commit changes**

### 4. Add Your API Key
- Click on `config.js` in your repository
- Click the pencil icon (edit) in the top right
- Replace `YOUR_ESV_API_KEY_HERE` with your actual key
- Click **Commit changes**

### 5. Enable GitHub Pages
- Go to your repository **Settings** tab
- In the left sidebar, click **Pages**
- Under "Source", select **Deploy from a branch**
- Under "Branch", select **main** and **/ (root)**
- Click **Save**
- Wait 1-2 minutes, then your site will be live at:
  `https://YOUR-USERNAME.github.io/bible-reading/`

### 6. Share with Your Church
- Send the link to your congregation
- On phones, they can tap "Add to Home Screen" in their browser menu
- It will appear as an app icon on their phone

---

## How to Edit a Reading Plan

Each plan is a simple JSON file in the `plans/` folder. Here's the format:

```json
{
  "name": "Plan Name Shown in the App",
  "description": "A short description of the plan.",
  "readings": [
    { "date": "2026-01-01", "passages": ["Genesis 1–2", "Psalm 1"] },
    { "date": "2026-01-02", "passages": ["Genesis 3–4", "Psalm 2"] }
  ]
}
```

### Rules for the JSON format:
- **Dates** must be in `YYYY-MM-DD` format (e.g., `2026-03-17`)
- **Passages** use standard Bible reference format (e.g., `Genesis 1–3`, `Psalm 119:1-24`, `John 3:16-36`)
- Each day can have **multiple passages** — just add more items to the array
- Use **en-dashes** (–) or regular hyphens (-) for chapter ranges — both work
- Make sure every line ends with a comma EXCEPT the last item in each list

### To edit from your phone:
1. Open your repository on github.com
2. Navigate to `plans/` and tap the file you want to edit
3. Tap the pencil icon
4. Make your changes
5. Tap **Commit changes**
6. The site updates automatically in about 1 minute

### To edit from a computer:
Same process, just easier with a keyboard.

---

## How to Add a New Plan

1. Create a new JSON file in the `plans/` folder
   - In your repository, navigate to `plans/`
   - Click **Add file** > **Create new file**
   - Name it something like `lent-2026.json`
   - Paste in the plan following the format above
   - Click **Commit changes**

2. Register it in `config.js`
   - Open `config.js` and click edit
   - Add the new file path to the `PLAN_FILES` array:
   ```js
   PLAN_FILES: [
     "plans/daily-2026.json",
     "plans/nt-90-days.json",
     "plans/lent-2026.json"     // <-- new plan
   ]
   ```
   - Click **Commit changes**

---

## How to Give Your Team Edit Access

1. Go to your repository **Settings**
2. Click **Collaborators** in the left sidebar
3. Click **Add people**
4. Enter their GitHub username or email
5. They'll get an invitation to accept

Once accepted, they can edit plan files directly from their phone or computer.

---

## File Structure

```
bible-reading/
├── index.html        ← The app (don't edit unless you know HTML/JS)
├── config.js         ← Your API key and list of plan files
├── manifest.json     ← Makes it installable as a home screen app
├── README.md         ← This file
└── plans/
    ├── daily-2026.json    ← A reading plan
    └── nt-90-days.json    ← Another reading plan
```

---

## Features

- **Read**: Tap any passage to load the full ESV text
- **Listen**: Tap the play button to hear the passage read aloud
- **Track**: Check off passages as you complete them (saved on your device)
- **Multiple plans**: Switch between plans from the Plans tab
- **Share**: Share the link with anyone
- **Home screen**: Add to your phone's home screen for app-like access

---

## Limitations

- **Progress is per-device**: Checking off readings on your phone won't show on your laptop (and vice versa). Clearing browser data will reset progress.
- **API limits**: The ESV API allows 5,000 requests per day. For a typical church this is more than enough, but if you have thousands of daily users, contact Crossway about higher limits.
- **Public repository**: Your plan files are publicly visible (but there's no user data in the repository — progress is stored only on each person's own device).

---

## Troubleshooting

**"ESV API key not configured"** → Make sure you replaced `YOUR_ESV_API_KEY_HERE` in `config.js` with your actual key.

**Passage text won't load** → Check that your API key is valid at [api.esv.org](https://api.esv.org/). Also check your browser console for errors.

**Audio won't play** → Some browsers block autoplay. The user may need to tap play again. Also ensure the passage reference is valid.

**Site not updating after edits** → GitHub Pages can take 1-2 minutes to rebuild. Hard-refresh your browser (pull down on mobile, Ctrl+Shift+R on desktop).

**"No reading plans found"** → Make sure your plan JSON files are listed in `config.js` under `PLAN_FILES`, and that the file paths match exactly.
