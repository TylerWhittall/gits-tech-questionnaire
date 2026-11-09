# GITS Technology Questionnaire

A lightweight GitHub Pages entry point for the Get IT Sense Technology Service Review questionnaire.

Website address: **https://tylerwhittall.github.io/gits-tech-questionnaire/**

## Website files

The website source lives in `websites/gits-tech-questionnaire/`:

- `index.html` embeds the published Google Apps Script questionnaire and provides a permanent link to open it directly.
- `.nojekyll` tells GitHub Pages to serve the files as a plain static website.

The questionnaire continues to save responses in Google Sheets and PDFs in Google Drive through its existing Google Apps Script application. This repository contains only the public website wrapper; it does not contain response data, credentials, or the application's backend code.

## Publishing

Publish the contents of `websites/gits-tech-questionnaire/` to the root of the `gh-pages` branch. In the repository's **Settings → Pages**, select **Deploy from a branch**, then **gh-pages / (root)**. No build tools or GitHub Actions workflow are needed.

After committing website changes to the main source branch, publish them with:

```sh
git subtree push --prefix websites/gits-tech-questionnaire origin gh-pages
```

## Questionnaire connection

The iframe and direct link in `index.html` must point to the same published Apps Script `/exec` URL. The Apps Script `doGet()` response must allow embedding with `HtmlService.XFrameOptionsMode.ALLOWALL`, and the web app's access settings must permit the intended respondents.

Update the existing Apps Script deployment when changing questionnaire behavior so its URL remains stable. If the deployment URL ever changes, update both occurrences in `index.html` and republish this website.

The direct link remains available if a visitor's browser or Google sign-in settings prevent the embedded form from displaying.
