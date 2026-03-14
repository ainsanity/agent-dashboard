# 📊 Agent Performance Dashboard

A live, shareable dashboard for monitoring call center agent performance.  
**Admin uploads CSV → Dashboard auto-updates → Associates view via shared link.**

---

## 🚀 One-Time Setup (10 minutes)

### Step 1 — Create your GitHub repo

1. Go to [github.com](https://github.com) and sign in (or create a free account)
2. Click **"New repository"**
3. Name it: `agent-dashboard`
4. Set visibility to **Public**
5. Click **Create repository**

### Step 2 — Upload these project files

1. In your new repo, click **"uploading an existing file"**
2. Drag and drop **all files and folders** from this project zip
3. Click **Commit changes**

### Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under **Source**, select: **GitHub Actions**
3. Save — your dashboard will be live at:
   ```
   https://YOUR_USERNAME.github.io/agent-dashboard/
   ```

### Step 4 — Generate a GitHub Token (for admin uploads)

1. Go to: [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Give it a name like `dashboard-upload`
3. Set expiration as needed
4. Check the **`repo`** scope checkbox
5. Click **Generate token** — **copy it immediately** (shown only once)

### Step 5 — Share the links

| Link | Who uses it |
|------|------------|
| `https://YOUR_USERNAME.github.io/agent-dashboard/` | Associates (read-only) |
| `https://YOUR_USERNAME.github.io/agent-dashboard/admin/` | Admin only (upload) |

---

## 📤 Daily Usage (Admin)

1. Open the **Admin Panel**: `…/admin/`
2. Paste your GitHub token (saved in browser after first time)
3. Enter your repo: `your-username/agent-dashboard`
4. **Drag & drop** the daily CSV/Excel report
5. Click **Upload & Publish** — done in seconds!

Associates see the updated dashboard automatically (refreshes every 5 min).

---

## ⚡ Flagging Rules

| Metric | Threshold | Flag |
|--------|-----------|------|
| Total Calls | < 150 | 🔴 Red |
| TB (Tea Break) | > 30 min | 🔴 Red |
| LB (Lunch Break) | > 30 min | 🔴 Red |
| RRB | > 10 min | 🔴 Red |
| PD | ≥ 2 hours | 🔴 Red |
| Outbound | ≥ PD time | 🟡 Amber |
| Inactive agents | 0 calls | Hidden |

---

## 📁 Project Structure

```
agent-dashboard/
├── index.html              ← Main dashboard (shareable link)
├── admin/
│   └── index.html          ← Admin upload panel
├── data/
│   ├── latest.json         ← Latest uploaded data (auto-updated)
│   └── history.json        ← Upload snapshot history
├── .github/
│   └── workflows/
│       └── deploy.yml      ← Auto-deploy to GitHub Pages
└── README.md
```

---

## ❓ FAQ

**Q: Do associates need a GitHub account?**  
No. The dashboard link is fully public — anyone with the link can view.

**Q: Is the token safe?**  
The token is stored only in the admin's browser (localStorage). It is never sent anywhere except directly to GitHub's API.

**Q: How often does the dashboard refresh?**  
It auto-refreshes every 5 minutes for associates. They can also click the **↻ Refresh** button.

**Q: Can I upload multiple times a day?**  
Yes! Each upload overwrites the live data and adds a snapshot to the history tab.
