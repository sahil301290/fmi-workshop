# FMI Workshop 2027 — website

A responsive, accessible, static website for the **1st Future Medicines Institute Workshop**, provisionally titled **Rapid Prototyping in Medical AI: From Multi-Sensor Data to Clinical Impact**, hosted at **Ulster University Belfast** on **Tuesday 25 May 2027, 08:00–16:00 BST (venue access planned until 16:30 for informal discussions and close-down, subject to room booking)**.

## Repository contents

- `index.html` — the entire webpage: HTML, CSS, accessible navigation, agenda, speaker placeholders, organiser details and official Ulster staff profile, a static speaker expression-of-interest form (via email), refreshments, registration tiers, partners, a linked MDPI *Sensors* Special Issue, and FAQs. No build step required.
- `assets/favicon.svg` — original minimal favicon, not an official university mark.
- `event.ics` — downloadable calendar event in the Europe/London time zone.
- `CNAME` — prefilled with **`www.fmiworkshop.io`**. You must still configure this in GitHub Pages settings and point your domain’s DNS to GitHub.

## Publish at https://www.fmiworkshop.io (custom domain)

**Important:** You must register or already own `fmiworkshop.io` at a domain registrar (domain availability has not been checked). GitHub Pages can serve the website and handle HTTPS, but does **not** register the domain. This is a static website; registration payments and speaker interest forms are separate services.

### 1 — Upload the site

1. In GitHub, create a **public** repository, for example `fmi-workshop` (or use an organisation account if appropriate). The repository name does **not** determine the public custom domain.
2. Extract this ZIP on your computer. Open the repository and choose **Add file → Upload files**. Upload `index.html`, `CNAME`, `event.ics`, and the `assets/` directory **directly into the repository root**. GitHub's drag-and-drop upload normally preserves `assets/favicon.svg`; verify the folder structure in the repository afterward. You may also upload `README.md`.
3. Commit the files to the `main` branch.
4. In the repository, open **Settings → Pages → Build and deployment**. Set **Source: Deploy from a branch**, **Branch: main**, **Folder: /(root)**, then **Save**.

### 2 — Set the single preferred address in GitHub

1. At GitHub **Settings → Pages → Custom domain**, enter **`www.fmiworkshop.io`** (not `fmiworkshop.io`) and click **Save**.
2. The prefilled root `CNAME` file contains exactly `www.fmiworkshop.io`. If GitHub regenerates it when you save the custom domain, that is expected. Do not add extra domains to that file.
3. For security, consider first verifying domain ownership in **GitHub account avatar → Settings → Pages → Add a domain**. GitHub will give you a unique TXT record value for the domain. Keep that TXT record in DNS after verification.

### 3 — Configure DNS with the domain registrar or DNS provider

For `www.fmiworkshop.io`:

| Record | Host/name | Value/target |
|---|---|---|
| `CNAME` | `www` | `YOUR-GITHUB-USERNAME.github.io` |

Replace `YOUR-GITHUB-USERNAME` with the exact GitHub account or organisation that owns the repository. **Never include the repository name or `https://`** in the CNAME record value. Remove any conflicting existing DNS record for `www` (some registrars add parking records automatically).

For `fmiworkshop.io` **without `www`**, add all four of GitHub Pages' official IPv4 `A` records so GitHub Pages redirects the bare domain to the configured `www` address:

| Record | Host/name | Value |
|---|---|---|
| `A` | `@` | `185.199.108.153` |
| `A` | `@` | `185.199.109.153` |
| `A` | `@` | `185.199.110.153` |
| `A` | `@` | `185.199.111.153` |

If your provider supports an `ALIAS`/`ANAME` record at `@`, the official GitHub docs describe that as an alternative. Do not add wildcard DNS records; do not use ordinary URL forwarding in place of the `www` CNAME. Keep any existing MX/email DNS records if the domain has mailboxes.

### 4 — Enforce HTTPS and test

Return to **GitHub repository → Settings → Pages**. Wait for DNS verification and the TLS certificate, then enable **Enforce HTTPS**. GitHub warns DNS changes can take up to 24 hours; the HTTPS toggle can also take time to become available.

Test all three addresses:

- **Canonical/public:** `https://www.fmiworkshop.io/` — should show your workshop.
- **Bare domain:** `https://fmiworkshop.io/` — should redirect to `https://www.fmiworkshop.io/`.
- **Default GitHub Pages site:** `https://YOUR-GITHUB-USERNAME.github.io/fmi-workshop/` (if the repository is named `fmi-workshop`) — should redirect to the custom domain once GitHub Pages has configured it. The repository itself still exists on GitHub; the custom URL is your public website address.

Share only `https://www.fmiworkshop.io/` in emails, flyers, QR codes, and official communications. Metadata in `index.html` specifies this as the website's canonical URL.

Official documentation:
- Publishing from `main`: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- Custom domain setup and DNS: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Domain verification: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

## Must-check items before public launch

1. **Approve the event date and room** — Tuesday 25 May 2027 is entered as requested, but room booking and university approval need confirmation.
2. **Agree on pricing** — £20 students / £30 academics & staff / £30 industry are explicitly labelled proposed rates until approved.
3. **Confirm sponsors and any logo use** — the website lists **External funding partners: MDPI Sensors and MDPI AI Sensors** per the organiser's briefing; financial contributions are not disclosed. Seek permission before adding official logos.
4. **Speaker expressions of interest** — the page includes an email-based form for the academic, industry, and PhD/early-career streams. It does not store applications or send emails automatically. Test the workflow with an email client before launch; for tracked submissions, choose an approved hosted form and replace the workflow. Committee selection and invitations are explicit.
5. **Confirm room access** — the public programme ends 16:00 BST. Afternoon tea and snacks are in the draft schedule; onsite access to 16:30 is planned, not a confirmed booking.
6. **Confirm the committee titles and names** — Dr. Sahil Sharma is shown as Workshop Chair, with Prof. Christopher Nugent and Prof. James McLaughlin as Academic Co-Chairs. Two support coordinator roles are unnamed.
7. **Speaker invitations/programme** — all speaker entries are placeholders; the agenda is clearly labelled draft.
8. **Registration platform** — no payments are accepted through GitHub Pages. Once a sanctioned booking system is approved, replace the non-clickable registration status in `#registration` with an actual external link and update the FAQs.
9. **Public contact** — the site uses `s.sharma@ulster.ac.uk`, as listed by Ulster University in its staff directory. Replace if a central workshop mailbox is preferred.
10. **MDPI *Sensors* Special Issue** — the site includes a distinct editorial/research opportunity for *Artificial Intelligence in Multi-Sensor Systems* (https://www.mdpi.com/journal/sensors/special_issues/VAYF36M731), edited by Dr. Sahil Sharma and Dr Nazmul Siddique. MDPI currently displays a **31 March 2027** submission deadline, which is **before** the 25 May workshop. This is a separate journal call, not a workshop proceedings or publication pathway. Check MDPI for any future deadline changes; the site does not claim that presenting at the workshop affects journal acceptance. A small date-aware notice changes after the deadline. No MDPI artwork/logos have been used.
11. **Institutional sign-off** — verify the wording about Future Medicines Institute and Ulster University, consent to display sponsor names, accessibility, and institutional web/brand guidelines.

## How to update

Edit text directly in `index.html`. For example:
- Workshop title: search for `Rapid Prototyping`.
- Schedule: search for `<section class="section" id="programme">`.
- Speaker cards: search for `id="speakers"`.
- Speaker expressions of interest: search for `id="propose-talk"` and `id="speaker-interest-form"`. The form sends drafts to `s.sharma@ulster.ac.uk` using the visitor’s email app; no server-side storage.
- Public chair profile: https://www.ulster.ac.uk/staff/s-sharma
- Prices and live booking URL: search for `id="registration"`.
- Sponsorship acknowledgements: search for `id="partners"`.
- MDPI special issue information: search for `id="special-issue"` and verify deadline changes against the MDPI page before public announcements.
- Committee and two support positions: search for `id="organisers"`.

For **future editions**, change the year, date, calendar event, metadata, committee, prices, and programme. A more sustainable multi-year setup could introduce a `/2027/` archive and use the root URL for the latest edition.

## Design notes

Colour palette: the initial green/teal theme has been intentionally retained pending the organisers’ preferred colours and university brand approval.

The uploaded GLOW@ICDE'27 HTML served as a structural reference (hero, about, topics, programme, organisers, sponsors). This website uses entirely original layouts, CSS, and artwork and does not reuse that site's Bootstrap template or assets.

Sources used to verify publicly listed facts:
- Ulster University official FMI project: https://pure.ulster.ac.uk/en/projects/future-medicines-institute/
- Ulster staff pages for Prof. Nugent and Prof. McLaughlin: https://www.ulster.ac.uk/staff/cd-nugent and https://www.ulster.ac.uk/staff/jad-mclaughlin
- Ulster University official Belfast campus address: https://www.ulster.ac.uk/about/contact-us
- MDPI journals: https://www.mdpi.com/journal/sensors and https://www.mdpi.com/journal/aisens

- MDPI *Sensors* Special Issue *Artificial Intelligence in Multi-Sensor Systems*: https://www.mdpi.com/journal/sensors/special_issues/VAYF36M731
- Dr Nazmul Siddique, official Ulster profile: https://www.ulster.ac.uk/staff/nh-siddique
