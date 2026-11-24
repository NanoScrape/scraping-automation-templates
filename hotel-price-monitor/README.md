# Booking.com hotel price monitor (n8n)

Monitors Booking.com hotel prices for a city and a stay, stores every check in Google Sheets and flags what changed since the last check (first price, price down, price up, no change, sold out, back on sale). It never books or changes anything.

- n8n template library: not published yet
- Workflow file: [workflow.json](./workflow.json) (Import from URL: https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/hotel-price-monitor/workflow.json)

## How it works

1. A schedule (daily at 7 AM by default) or a manual run starts the workflow.
2. The **Settings** node holds destination, dates, guests, rooms, currency and number of hotels.
3. On the first run the workflow creates a Google Sheet with three tabs (Prices, Latest, Runs).
4. [booking-com-scraper](https://apify.com/santamaria-automations/booking-com-scraper?fpr=0khfbz&fp_sid=gh-hotel-price-monitor) is started without waiting and collected when it finishes, so slow runs never block n8n.
5. Each hotel's total stay price is compared with its last row; a history row with flag, previous price, change and percent is added.

## Requirements

- [n8n](https://n8n.partnerlinks.io/rx97o1phofve) (Cloud or self-hosted) with the verified community node `@apify/n8n-nodes-apify`
- An Apify account ([free sign-up](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-hotel-price-monitor))
- A Google account (Sheets)

## How to import

1. Open [n8n](https://n8n.partnerlinks.io/rx97o1phofve) ([n8n Cloud](https://n8n.partnerlinks.io/rx97o1phofve) or self-hosted) and create a new workflow.
2. Use the menu (three dots) > **Import from file** and choose [workflow.json](./workflow.json) from this folder, or **Import from URL** and paste https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/hotel-price-monitor/workflow.json
3. Install the verified community node `@apify/n8n-nodes-apify` (Settings > Community nodes) if n8n asks for it.
4. Create your credentials: an [Apify account](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-hotel-price-monitor) (free sign-up) for the Apify nodes, plus the other services listed under Requirements.
5. Open the **Settings** node, fill in your values, run once with **Test workflow**, then activate.

## Customization

- `destination`, `checkin`, `checkout`, `adults`, `rooms`, `currency`, `sortBy`, `maxHotels`.
- Alert threshold `minPriceChangePercent`; cost cap `maxCostPerRunUsd`; optional `webhookUrl`.
- Add a Gmail, Slack or Telegram node after the Latest tab to be alerted on "price down".

## Cost

0.001 USD per run plus 0.00297 USD per hotel at Apify Store prices (checked 2026-11-23, measured on a live run). 20 hotels is about 0.06 USD per run, about 0.42 USD per week when run daily.

## Notes

Tested end to end on n8n 2.35.7 (self-hosted), including a repeat run on the same Sheet. The workflow stops before any Apify cost if the dates are missing or in the past.

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
