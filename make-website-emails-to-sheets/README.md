# Website emails and phones to Google Sheets with Apify (Make)

Paste a list of websites and get the emails and phone numbers they publish into Google Sheets, one row per website, with the contact page, pages crawled and status.

## Template link

- Public Make template: [Website Emails and Phones to Google Sheets with Apify](https://www.make.com/en/integration/25709-website-emails-and-phones-to-google-sheets-with-apify-nanoscrape?templatePublicId=25709) (works now; Make gallery review pending)
- Blueprint file: [blueprint.json](./blueprint.json) (download, then in Make: new scenario > ... > Import blueprint)

## How it works

1. Apify **Run an Actor** starts the [website-email-scraper](https://apify.com/santamaria-automations/website-email-scraper?fpr=0khfbz&fp_sid=gh-make-website-emails-to-sheets) with your website list and waits for the result.
2. Apify **Get Dataset Items** reads one result per website.
3. Google Sheets **Add a Row** writes one row per website.

## Requirements

- A Make account
- An Apify account
- A Google account (Sheets)

## Setup

1. Open the template link above in Make and click **Use template**. Or download [blueprint.json](./blueprint.json), create a new scenario in Make and use **... > Import blueprint**. The file has no connections or spreadsheet; you pick your own in step 2 and 3.
2. Connect your Apify account ([free sign-up](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-make-website-emails-to-sheets)) and your Google account in the wizard.
3. Create the Google spreadsheet with the headers listed below in row 1 and pick it in the wizard.
4. Change the Input JSON, keep **Maximum cost per run** as a safety cap, run once, then schedule it if you want.

## Customization

Spreadsheet headers in row 1 (8): Website, Domain, Emails, Phones, Contact page, Pages crawled, Status, Checked at.

The Input JSON takes your list of sites and `maxPagesPerSite` (default 5). Emails and phones are mapped as plain values; Make joins multiple values with a comma.

In the Apify module the actor is chosen by its id with Map enabled, because Make's actor search does not list it.

## Cost

About 0.001 USD per crawled page at Apify Store prices (measured 2026-11-23): 5 sites with up to 5 pages each cost about 0.02 USD per run, plus Make operations.

## Notes

Tested in Make on 2026-11-23 (5 sites, emails and phones correct for 5 of 5). Only data published on the websites is collected; check your local rules (for example GDPR) before using it for outreach.

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
