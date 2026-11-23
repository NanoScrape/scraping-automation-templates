# Google Maps leads to Google Sheets with Apify (Make)

Turn any Google Maps search into a lead list in Google Sheets. Enter searches like "dentists in Chicago" or "plumbers in Berlin". The scenario runs the Google Maps Scraper on Apify, waits for it to finish and adds one row per business to your sheet.

## Template link

Public Make template: pending approval

## How it works

1. Apify **Run an Actor** starts the [google-maps-scraper](https://apify.com/santamaria-automations/google-maps-scraper?fpr=0khfbz&fp_sid=gh-make-google-maps-leads-to-sheets) with your searches and waits for the result (synchronous run).
2. Apify **Get Dataset Items** reads the places it found.
3. Google Sheets **Add a Row** writes one row per place: name, category, address, city, phone, website, rating, review count, search query and Google Maps link.

## Requirements

- A Make account
- An Apify account
- A Google account (Sheets)

## Setup

1. Open the template link above in Make and click **Use template** (no blueprint file is included in this folder, the template lives in Make's public gallery).
2. Connect your Apify account ([free sign-up](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-make-google-maps-leads-to-sheets)) and your Google account in the wizard.
3. Create the Google spreadsheet with the headers listed below in row 1 and pick it in the wizard.
4. Change the Input JSON, keep **Maximum cost per run** as a safety cap, run once, then schedule it if you want.

## Customization

Spreadsheet headers in row 1 (10): Name, Category, Address, City, Phone, Website, Rating, Reviews, Search query, Google Maps link.

Change `searchStrings` and `maxResultsPerQuery` in the Input JSON. For large lists (thousands of places), start the actor without waiting and use **Watch Actor Runs** in a second scenario so the run is not limited by Make's scenario timeout.

## Cost

About 1 USD per 1,000 places at Apify Store prices (measured 2026-11-23), so the default 20 places cost about 0.02 USD per run, plus Make operations (about 1 per row).

## Notes

Tested in Make on 2026-11-23 (20 places per run). Phone numbers are written with a leading apostrophe so Sheets keeps them as text.

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
