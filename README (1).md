# Cadence

A demand gen sequence builder. Enter what you sell, who you are targeting, and the goal. It writes a full multi touch outbound cadence with A/B subject lines and merge tokens, then exports to CSV for your sequencer.

## What is in here

- `index.html` the app, served as a static page
- `api/generate.js` a serverless function that holds your API key and talks to Claude

The page never sees your key. The browser calls `/api/generate`, and the function adds the key on the server.

## Put it on GitHub (website, no terminal)

1. Go to github.com and click New to create a repository. Name it `cadence`. Leave it empty.
2. On the repo page, click Add file, then Create new file.
3. In the filename box type `index.html`. Paste the full contents of index.html. Click Commit changes.
4. Click Add file, then Create new file again. In the filename box type `api/generate.js` exactly. Typing the slash creates the api folder for you. Paste the contents of api/generate.js. Click Commit changes.
5. Optional. Add this README the same way, named `README.md`.

Your repo now has `index.html` and `api/generate.js`.

## Deploy on Vercel

1. In Vercel click Add New, then Project, and import the `cadence` repo.
2. Framework Preset: choose Other. There is no build step.
3. Before or after the first deploy, open Project Settings, then Environment Variables.
4. Add one variable. Name it `ANTHROPIC_API_KEY`. Paste your key from console.anthropic.com as the value. Save.
5. If you added the variable after deploying, go to Deployments and redeploy so it picks up the key.
6. Open the live URL and click Build cadence. It writes the sequence live.

## Notes

- The key lives only in Vercel as an environment variable. It is never in the code and never sent to the browser.
- Load a sample works without any key, so the page is demoable even before the key is set.
- Model and length are set in `api/generate.js` if you ever want to change them.
