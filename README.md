# Pork and Garlic official Winter strategy tool

This is the complete replacement project for a NEW GitHub repository and Vercel project. It uses the supplied revised official Year 1 rules. The official game starts with Sh 100,000 and no assets, debt or tax losses. Pilot results do not carry forward. Year 2 operating rules are not yet provided.

## Open it immediately

Extract the ZIP and double-click **index.html**. The application, styles and calculations are all inside this file. It works without a server, internet connection or installation. Do not open index.html inside the ZIP; extract first. Enable JavaScript in the browser.

The old http://127.0.0.1:4173 link was a temporary local preview, not a published website. It only works while its server runs on that computer. Use your eventual Vercel URL to share the app.

## Upload to a NEW GitHub repository

1. Create a repository in your GitHub account, for example `pork-garlic-winter`.
2. Choose **uploading an existing file**, or **Add file → Upload files**.
3. Drag ALL the extracted contents into GitHub. Do not upload the ZIP or the enclosing folder. Preserve the `tests` folder.
4. Choose **Commit changes**.
5. Check that `index.html`, `package.json`, `build.mjs` and `vercel.json` appear directly on the repository's main page.

Expected structure:

```text
index.html
package.json
vercel.json
build.mjs
server.mjs
README.md
.gitignore
tests/
  model.test.mjs
```

`.gitignore` may be hidden in Windows; it is optional for browser upload. No credentials or environment files are needed.

## Deploy a NEW Vercel project

1. Sign into Vercel with GitHub.
2. Select **Add New → Project** and import your NEW repository. If missing, grant Vercel access to that repository.
3. Use these settings (vercel.json already supplies build settings):

| Setting | Value |
|---|---|
| Framework Preset | Other |
| Root Directory | Repository root (leave default) |
| Build Command | npm run build |
| Output Directory | dist |
| Install Command | Empty; no dependencies |
| Environment Variables | None |

4. Click **Deploy**. Once ready, open the supplied `.vercel.app` URL.
5. Confirm Strategy B shows Sh 15,421 net profit at 60,000 sales. Change B allocation to 50,000: it should show Sh −866. Restore 60,000 afterward.

If deployment fails, read the first build error. A missing package.json or build.mjs normally means files were uploaded inside an extra folder: move them to the root or set Root Directory to that folder. Uploading only the ZIP will not deploy the application. Do not use the old repository's settings or a localhost URL as the public link.

## Model and assumptions

The default recommendation buys Machine 1, rents D, buys three tons of milk, produces and requests 60,000, spends Sh 1,000 on marketing and borrows nothing. This leaves Sh 4,000 after advances. Selling all 60,000 yields Sh 15,421 net profit and Sh 84,796 closing cash. At 50,000 sales the plan loses Sh 866; at 40,000 it loses Sh 18,866. Allocation is conditional on the trainer's market, not guaranteed by marketing.

The alternative reproduces the official Machine 5 / Premise B worked example. The interface contains official tables, calculation formulas, cash checkpoints, machine closing book value, remaining life, closing loan principal, tax loss pool and downside comparison.

Gross profit deducts milk, maintenance and depreciation. Bonus is 5% of positive gross profit. Fixed salaries are Sh 10,000, game tax 10%, and seasonal loan interest 10%. Machine, milk and marketing payments are advances paid by the company; no customer sales advance is received. All other cash items settle at season end. Monetary lines are rounded to whole shekels before subtotals. Requested and allocated sales are 10,000-unit blocks. Percentage downside scenarios round down to that block size.

This tool covers first official Winter only, not a full multi-season ledger. Loan installment rounding remainders must be reconciled in the last installment of a future rolling ledger. Inputs are held only for the current page session and reset on refresh. Use Print comparison to retain decisions.

## Optional developer commands

Use Node.js 22 or newer; no npm install required.

```sh
npm test
npm run build
npm run dev
```

The preview uses http://127.0.0.1:4174. Build validates the embedded JavaScript and writes a single deployable dist/index.html. Tests execute the actual calculation code embedded in index.html, avoiding a separate model copy.
