# Notion ATS with AI CV scoring (n8n)

Turns a Notion candidate database into a lightweight applicant tracking system. Move a candidate to the status "CV Scoring (AI)" and the workflow downloads the CV (a PDF attached to the Notion page), compares it with the job requirements stored in Notion and writes a 0-100 score, a summary, strengths, gaps and an internal note back to the page. Optional Gmail drafts to the candidate and your team (never sent).

- n8n template library: not published yet
- Workflow file: [workflow.json](./workflow.json) (Import from URL: https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/notion-ats-cv-scoring/workflow.json)

## How it works

1. A Notion trigger watches your candidate database for updated pages.
2. An IF node continues only for pages with the trigger status and a CV file.
3. The CV PDF is downloaded and its text extracted.
4. Job requirements come from the Notion page. Optionally [job-feed](https://apify.com/santamaria-automations/job-feed?fpr=0khfbz&fp_sid=gh-notion-ats-cv-scoring) fetches the full text of a job ad URL (off by default).
5. An AI chat model through OpenRouter scores five criteria; your `minScore` setting decides proceed or reject.
6. The Notion page is updated with score, summary, note and the new status.

## Requirements

- [n8n](https://n8n.partnerlinks.io/rx97o1phofve) (Cloud or self-hosted)
- A Notion integration with access to your candidate database (the sticky note lists the properties)
- An OpenRouter API key (default model `qwen/qwen3-235b-a22b-2507`)
- Optional: Gmail (drafts) and an [Apify account](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-notion-ats-cv-scoring) (job ad fetch)

## How to import

1. Open [n8n](https://n8n.partnerlinks.io/rx97o1phofve) ([n8n Cloud](https://n8n.partnerlinks.io/rx97o1phofve) or self-hosted) and create a new workflow.
2. Use the menu (three dots) > **Import from file** and choose [workflow.json](./workflow.json) from this folder, or **Import from URL** and paste https://raw.githubusercontent.com/NanoScrape/scraping-automation-templates/main/notion-ats-cv-scoring/workflow.json
3. Install the verified community node `@apify/n8n-nodes-apify` (Settings > Community nodes) if n8n asks for it.
4. Create your credentials: an [Apify account](https://console.apify.com/sign-up?fpr=0khfbz&fp_sid=gh-notion-ats-cv-scoring) (free sign-up) for the Apify nodes, plus the other services listed under Requirements.
5. Open the **Settings** node, fill in your values, run once with **Test workflow**, then activate.

## Customization

- Pass mark, output language, signature, scheduling link and extra criteria in the **Settings** node.
- Notion status names: `triggerStatus`, `statusIfProceed`, `statusIfReject`.
- Swap the AI model node or type another OpenRouter model id.

## Cost

About 0.001 USD per CV with the default model (OpenRouter usage). The optional job ad fetch is billed at Apify Store prices (checked 2026-11-23).

## Notes

Tested end to end on n8n 2.35.7 (self-hosted) with the default model, including the Notion write-back and the Gmail drafts. Nothing is ever sent automatically: a person reviews every draft and decision. Re-scoring a candidate creates a new pair of drafts.

## Contact

contact@nanoscrape.com

---

Links to apify.com and n8n contain our affiliate IDs. Prices are unchanged for you.
