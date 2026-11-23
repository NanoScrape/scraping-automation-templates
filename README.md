# Scraping automation templates

Ready-to-import workflow templates for [n8n](https://n8n.partnerlinks.io/rx97o1phofve) and Make that use [Apify](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-readme) actors to collect leads, jobs, prices and contact data into Google Sheets, Notion and Gmail drafts. Each folder has the workflow file (n8n) or setup notes (Make), a README with requirements and customization, and cost estimates. Nothing in these templates sends emails on its own.

## Templates

| Template | What it does | Platform | Apify actors used | Typical cost per run | Links |
|---|---|---|---|---|---|
| Daily outreach drafts from Google Maps | Finds new local businesses daily, picks a role inbox from their website, logs them in Sheets and creates Gmail drafts (never sent) | n8n | [google-maps-scraper](https://apify.com/santamaria-automations/google-maps-scraper?fpr=0khfbz&fp_sid=gh-daily-outreach-drafts-google-maps), [website-contact-extractor](https://apify.com/santamaria-automations/website-contact-extractor?fpr=0khfbz&fp_sid=gh-daily-outreach-drafts-google-maps), [website-email-scraper](https://apify.com/santamaria-automations/website-email-scraper?fpr=0khfbz&fp_sid=gh-daily-outreach-drafts-google-maps) | about 0.15-0.20 USD per day (10 new companies), checked 2026-11-16 | [folder](./daily-outreach-drafts-google-maps), [n8n.io](https://n8n.io/workflows/22983-create-daily-outreach-leads-and-gmail-drafts-from-google-maps-with-apify-and-sheets/) |
| Job matches and cover letters | Collects new jobs from many sources, scores them against your CV, drafts cover letters, tracks status in Sheets | n8n | [job-feed](https://apify.com/santamaria-automations/job-feed?fpr=0khfbz&fp_sid=gh-job-matches-cover-letters) | about 0.004 USD per job plus your AI usage, checked 2026-11-16 | [folder](./job-matches-cover-letters), n8n.io page pending review |
| Notion ATS with AI CV scoring | Scores CVs of Notion candidates 0-100 with AI and writes results back, optional Gmail drafts | n8n | [job-feed](https://apify.com/santamaria-automations/job-feed?fpr=0khfbz&fp_sid=gh-notion-ats-cv-scoring) (optional) | about 0.001 USD per CV (OpenRouter), checked 2026-11-23 | [folder](./notion-ats-cv-scoring), not published |
| Weekly hiring signals | LinkedIn job posts grouped by company, agencies removed, Slack digest and Sheets log | n8n | [linkedin-scraper](https://apify.com/santamaria-automations/linkedin-scraper?fpr=0khfbz&fp_sid=gh-weekly-hiring-signals) | about 0.30 USD per week (3 searches x 100 posts), checked 2026-11-16 | [folder](./weekly-hiring-signals), not published |
| Booking.com hotel price monitor | Tracks hotel prices for a stay in Sheets and flags price changes | n8n | [booking-com-scraper](https://apify.com/santamaria-automations/booking-com-scraper?fpr=0khfbz&fp_sid=gh-hotel-price-monitor) | about 0.06 USD per run (20 hotels), checked 2026-11-23 | [folder](./hotel-price-monitor), not published |
| Weekly job market report | Counts new job ads per role and city each week into History and Summary tabs | n8n | [job-feed](https://apify.com/santamaria-automations/job-feed?fpr=0khfbz&fp_sid=gh-weekly-job-market-report) | about 0.48-0.96 USD per week (4 searches), checked 2026-11-23 | [folder](./weekly-job-market-report), not published |
| Google Maps leads to Google Sheets | Google Maps searches to one Sheet row per business | Make | [google-maps-scraper](https://apify.com/santamaria-automations/google-maps-scraper?fpr=0khfbz&fp_sid=gh-make-google-maps-leads-to-sheets) | about 0.02 USD per run (20 places), checked 2026-11-23 | [folder](./make-google-maps-leads-to-sheets), on Make: pending approval |
| Website emails and phones to Google Sheets | Websites to emails and phones, one Sheet row per site | Make | [website-email-scraper](https://apify.com/santamaria-automations/website-email-scraper?fpr=0khfbz&fp_sid=gh-make-website-emails-to-sheets) | about 0.02 USD per run (5 sites), checked 2026-11-23 | [folder](./make-website-emails-to-sheets), on Make: pending approval |

Costs are estimates at Apify Store prices on the check date shown; actor prices can change, see each actor page. Your AI provider, Make operations and other services are billed separately.

## Import into n8n

1. Open [n8n](https://n8n.partnerlinks.io/rx97o1phofve) ([n8n Cloud](https://n8n.partnerlinks.io/rx97o1phofve) or self-hosted) and create a workflow.
2. Menu (three dots) > **Import from file** > pick `workflow.json` from a template folder.
3. Install the verified community node `@apify/n8n-nodes-apify` if n8n asks for it, then create your Apify, Google and other credentials.
4. Fill in the **Settings** node, run **Test workflow** once, then activate.

## Import into Make

Make templates are shared as public templates. Open the template link in the table and click **Use template**, then connect your Apify and Google accounts in the wizard. Each Make folder lists the sheet headers and setup.

## License

MIT, see [LICENSE](./LICENSE).

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
