# n8n Workflows

A collection of automation workflows built with n8n and the Gemini API.

## 1. Text Summarizer

A form where you paste text and get back a short summary written by an AI model.

![Workflow canvas](text-summarizer.png)

**How it works**

1. An n8n Form Trigger collects the text (and optionally the number of sentences).
2. A Google Gemini node sends the text to the model with a summarizing prompt.
3. The summary is returned as the result.

**How to use it**

1. In n8n, open the menu and choose Import from file, then select `text-summarizer.json`.
2. Open the Gemini node and add your own Gemini API credential (free keys are available from Google AI Studio).
3. Click Execute workflow, fill in the form, and check the output.

## 2. Remote Jobs Digest

Every morning, this workflow fetches new remote programming jobs from the We Work Remotely RSS feed, summarizes each posting with the Gemini API, and emails me one digest with a link to apply for each job.

![Jobs digest canvas](<The Daily Digest.png>)

**Nodes:** Schedule Trigger, RSS Read, Limit, Google Gemini, Edit Fields, Aggregate, Gmail

**Setup**

1. Import `The Daily Digest.json` in n8n (menu, then Import from file).
2. Add your own Gemini and Gmail credentials.
3. Set the schedule time and the recipient address.

Job listings come from We Work Remotely's public RSS feed. Each email links back to the original posting.

## 3. Error Alert

A small workflow that emails me when a scheduled workflow fails. It uses n8n's Error Trigger node and is linked to the jobs digest in its settings.

![Error alert canvas](<Error Alert.png>)

**Setup:** import `Error Alert.json`, add a Gmail credential, publish it, then select it as the error workflow in your other workflow's settings.

## Notes

- No API keys or passwords are stored in this repository. You need your own credentials.
- Model names change often. If the Gemini node reports that a model isn't found, pick a current one from the node's dropdown.