[README.md](https://github.com/user-attachments/files/34815472/README.md)
# Sync Quote Request

A single-page web app that turns a sync licensing request into a clean, one-page quote request summary. A music supervisor, filmmaker or ad agency fills in a form, and the app lists anything a publisher would still need to know, then produces a PDF to send to the publisher.

The app covers the **composition (sync) license only**. It never calculates or suggests a fee, never assumes rights are cleared, and does not cover master use.

## What it does

- Collects requester, song, project, usage and terms details (25 fields).
- Shows a live one-page US Letter preview that updates as you type.
- Checks the entries against a published list of rules: required fields (errors), recommended fields and consistency questions (warnings), and notes.
- Downloads the summary as a one-page PDF, copies it as plain text, or prints it.
- Includes a "Load example" button (fictional data) and a "Clear form" button.
- Includes a "How this works" page that lists every rule and its exact wording. It is generated from the same rule list the app uses.

## What it does not do

- It does not calculate, estimate or suggest license fees.
- It does not look up songs, artists or publishers, and it uses no music database.
- It does not send email. You attach the PDF to your own email.
- It has no backend, no accounts and no saved data. Refreshing the page clears the form.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `README.md` | This file |
| `USER_MANUAL.md` | Step-by-step guide for people filling in the form |

## Run it on your computer

Open `index.html` in a web browser. That is all. The page needs an internet connection when it opens, because the PDF library (jsPDF 2.5.1) loads from cdnjs.cloudflare.com. Without it, everything works except Download PDF.

## Put it online for free (GitHub Pages)

These steps follow GitHub's Pages quickstart (https://docs.github.com/en/pages/quickstart). GitHub's screens change from time to time, so follow its page if a label differs.

1. Create a free account at github.com.
2. In the upper-right corner, open the create menu and choose **New repository**.
3. Name the repository `YOURUSERNAME.github.io`, replacing `YOURUSERNAME` with your GitHub username. Choose public visibility and create it.
4. In the repository, choose **Add file**, then **Upload files**. Drag in `index.html` and commit it. It must sit at the top level of the repository, not inside a folder.
5. Open the repository's **Settings** tab, then **Pages** in the sidebar.
6. Under "Build and deployment", set **Source** to **Deploy from a branch**. Choose your main branch and the root folder, then save.
7. Wait a few minutes (GitHub says changes can take up to 10 minutes). Your app is then at `https://YOURUSERNAME.github.io`. Send that link to your professor.

To update the app later, upload a new `index.html` to the same repository.

## How it is built

- One HTML file with inline CSS and JavaScript. No build step, no frameworks.
- PDF export uses jsPDF 2.5.1, loaded from cdnjs. The PDF is drawn directly at US Letter size (612 x 792 points) in Helvetica.
- All rules live in one list in the script. The warnings, the PDF, the copied text and the "How this works" tables all read from it.
- Entries stay in the browser. Nothing is sent anywhere.

## Known limitations

- PDF text supports Latin letters and accents only. Other scripts print as "?", and the app warns when that will happen.
- The PDF is always one page. The project description and scene description are limited to 300 characters each, and the text shrinks slightly (down to 60 percent) if the content would not otherwise fit.
- Download PDF and Print stay off until every required field is complete. Copy summary always works and starts with "INCOMPLETE" when required fields are missing.
- The only number-based rule is C4, which asks the publisher to confirm any duration over 300 seconds.

## Testing status

During development, the layout, rules, copy summary, Load example and Clear form were tested in an automated browser run. The PDF drawing code was tested against a stand-in for the PDF library, because the test environment could not reach the library's host. **The first real PDF download on your hosted copy is the first full end-to-end test, so please try it once before sharing the link.**

## Credits and notes

Built with Claude as a vibe coding assignment. The tool provides no legal advice. Actual license terms are set by the publisher.
