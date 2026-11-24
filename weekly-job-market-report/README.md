# Weekly job market report (n8n)

For every role and city on a list in Google Sheets, counts the new job ads of the last seven days across many job boards and stores the numbers as a history plus a chart-ready summary. Useful for recruiters, sourcers, HR, career coaches and analysts who want to see where hiring grows or slows.

- n8n template library: not published yet
- Workflow file: [workflow.json](./workflow.json) (Import from URL: https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/weekly-job-market-report/workflow.json)

## How it works

1. A schedule (Mondays at 8 AM by default) or a manual run starts the workflow.
2. On the first run the workflow creates a Google Sheet with four tabs: Searches, History, Summary, Runs.
3. For each active role and city [job-feed](https://apify.com/santamaria-automations/job-feed?fpr=0khfbz&fp_sid=gh-weekly-job-market-report) is started without waiting (ads from the last seven days, at most 30 unique ads per search).
4. The workflow reads how many unique ads each run delivered.
5. History gets one row per role, city and week; Summary gets the latest count, previous week, change, percent change and a trend.

## Requirements

- [n8n](https://n8n.partnerlinks.io/rx97o1phofve) (Cloud or self-hosted) with the verified community node `@apify/n8n-nodes-apify`
- An Apify account ([free sign-up](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-weekly-job-market-report))
- A Google account (Sheets)

## How to import

1. Open [n8n](https://n8n.partnerlinks.io/rx97o1phofve) ([n8n Cloud](https://n8n.partnerlinks.io/rx97o1phofve) or self-hosted) and create a new workflow.
2. Use the menu (three dots) > **Import from file** and choose [workflow.json](./workflow.json) from this folder, or **Import from URL** and paste https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/weekly-job-market-report/workflow.json
3. Install the verified community node `@apify/n8n-nodes-apify` (Settings > Community nodes) if n8n asks for it.
4. Create your credentials: an [Apify account](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-weekly-job-market-report) (free sign-up) for the Apify nodes, plus the other services listed under Requirements.
5. Open the **Settings** node, fill in your values, run once with **Test workflow**, then activate.

## Customization

- Edit the Searches tab for your roles, cities and countries (`active` = no skips a row).
- `maxSearchesPerRun`, `maxAdsPerSearch`, `includeGlobalBoards`, `postedWithinDays`, `radiusKm`, `minRelevanceScore`, `maxCostPerRunUsd`.
- Chart the History or Summary tab.

## Cost

job-feed bills 0.0005 USD per unique job plus the job boards it reads, about 0.40 to 0.80 USD per 100 jobs. The default 4 searches x up to 30 ads is about 0.48 to 0.96 USD per week (Apify Store prices, checked 2026-11-23; prices change, see the actor page).

## Notes

Tested end to end on n8n 2.35.7 (self-hosted), including a repeat run on the same Sheet. The count is a sample of the supported boards, not a census.

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
