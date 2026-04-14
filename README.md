# Sentinel — Find security problems in your code and website, in one click

Sentinel is a security scanner built for people, not just security teams. Paste
a GitHub link or a company URL, click **Run analysis**, and Sentinel tells you —
in plain language — what's vulnerable, how serious it is, and gives you a
downloadable report you can send to your developer, vendor, or manager.

If you can copy-paste a link, you can use Sentinel.



## Demo video

[Watch the demo video](https://drive.google.com/file/d/10qqqOr0bzke7iTEmIleBCZcOh6CEkCA2/preview)

---

## What it checks

Sentinel runs two kinds of scans. You can run either one, or both.

### 1. Code vulnerability scan (SCA)

Point Sentinel at a GitHub repository (yours, your company's, or an open-source
project you depend on). It reads the project, figures out which libraries it
uses, and checks every one of them against public vulnerability databases plus
its own AI-driven analysis.

**You get back:**
- A list of known security issues (CVEs) in your dependencies
- Severity labels: Critical / High / Medium / Low
- An architecture map of the project so you can see where each problem lives
- A plain-English explanation of what each issue means and what to do about it

**Typical run time:** a few minutes.

### 2. Live website pen test

Point Sentinel at a live website — your company's marketing site, your
product's login page, an internal tool — and it will act like an attacker
probing the site. It runs well-known security tools (nmap, nuclei, web
crawlers, and about ten more) in parallel, then uses an LLM to reason about
what it finds and try real attack paths.

**You get back:**
- Discovered services, endpoints, and attack surface
- Weaknesses the scanner could confirm (not just guess)
- A Word or PDF report you can download and hand off

**Typical run time:** 15 minutes to a few hours. You can close the tab and come
back later — Sentinel keeps running and you can resume from **Scan History**.

---

## How to use it

### Step 1 — Open Sentinel

Open the Sentinel URL your team gave you in a browser. That's it. No install,
no password, no sign-up prompt. The first time you arrive, Sentinel gives you
a friendly random name (like `calm-fox-1234`) and remembers you via a cookie.

If you want a stable account that survives clearing cookies or switching
devices, type your email in the login box — no password needed, the email is
the identifier.

### Step 2 — Tell Sentinel what to scan

Click **New Scan**. You have two ways to describe the target:

- **For code** → paste a GitHub URL like `https://github.com/your-org/your-repo`,
  or drag-and-drop a project folder from your computer.
- **For a website** → paste the site URL, e.g. `https://your-company.com/`.

Pick what kind of scan you want:

- **SCA (code)** — for GitHub repos and uploaded folders.
- **Pentest (website)** — for live URLs.
- **Both** — if you're scanning a repo that also has a deployed site.

Click **Run analysis**.

### Step 3 — Watch it work (or don't)

Sentinel shows live progress. For pen tests, you'll see the raw stream of
events coming back from each tool — helpful if you're curious, ignorable if
you're not. A yellow banner reminds you that full scans can take a while; this
is normal.

You can close the tab at any time. Your scan keeps running on the server.

### Step 4 — Read the report

When the scan finishes (or whenever you come back), go to **Scan History**.
Each row shows:

- The target (repo or URL)
- What kind of scan it was (SCA or Pentest)
- Status: Progressing, Completed, or Resumable
- Severity badge: the highest severity finding

Click a row to open the result. Click **Download** to get a PDF (or Word
document, if the backend produced one) you can forward to anyone.

### Step 5 — If you already ran a scan for this target

Submit the same URL a second time and Sentinel will ask:

> You already have a running scan for this target.
> **OK** — Resume the existing scan
> **Cancel** — Submit a brand-new scan (duplicate)

This keeps you from accidentally piling up duplicate work.

---

## Things worth knowing

**Only scan things you own or have permission to scan.** Pen testing a website
you don't own is illegal in most places. Stick to your own company's sites,
your own repos, or open-source projects. If in doubt, ask your security team.

**Scans run on a shared backend.** If someone else on your team is already
scanning the same target, Sentinel will offer to show you their scan instead
of duplicating the work. Different users can scan the same URL freely; same
user gets the warning above.

**Reports are links, not secrets.** The download URL for a report contains the
scan's ID. Anyone with that link on your network can download the file.
Treat it the way you'd treat a shared Google Doc link.

**Nothing leaves unless you download it.** Your scan targets, results, and
reports stay on the Sentinel server your team provided. Sentinel does not
forward your URLs to any third-party SaaS.

---

## Quick FAQ

**How long does a pen test take?**
15 minutes to a few hours, depending on the size of the site. The UI will
show you heartbeat ticks from each tool every few seconds so you know it's
alive.

**Can I scan a private GitHub repo?**
Yes, if the Sentinel server has been configured with access (your admin sets
this up once). Otherwise, Sentinel can only see public repos.

**Can I stop a scan?**
Yes — close the tab, or just walk away. The scan keeps running on the server
and shows up in Scan History. There's no "cancel" button today; long pen
tests will end on their own.

**Can I scan something that isn't a URL?**
Upload a project folder directly from the New Scan page. Sentinel will analyse
it the same way it analyses a cloned GitHub repo.

**What's "SCA" and "pen test" in plain English?**
- *SCA* = "Software Composition Analysis" = "which of the open-source pieces
  in this project have known security holes".
- *Pen test* = "penetration test" = "try to break into this live website the
  way a real attacker would".

**The Download button gave me a `.pdf`, but someone said it should be `.docx`?**
Sentinel serves whatever format the backend produced. If the pen test tool
wrote a Word document, you get `.docx`; otherwise you get `.pdf`. Same
content either way.

**Where are the settings pages for?**
*Integrations*, *Rules*, and *Risk Score* are for admins. If you're a regular
user, you can safely ignore them.

---

## Who should I ask for help?

If something looks broken, screenshot the page (including the scan ID if
visible) and send it to whoever operates your Sentinel instance. Most
problems are either "the target was unreachable" or "the scan is still
running, come back later" — both resolve themselves.
