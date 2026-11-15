FIREGUARD — NETLIFY FRONTEND + AI FUNCTION

Folder structure:
- public/index.html
- netlify/functions/ask.js
- netlify.toml

Recommended deployment:
1. Extract this ZIP on your computer.
2. In Netlify, choose Add new project > Deploy manually (or open https://app.netlify.com/drop).
3. Drag the extracted fireguard_netlify_deploy folder (or its contents as a folder) to the deploy area.
4. Wait for the site to deploy. Open the Netlify site URL. The frontend calls /.netlify/functions/ask on the same Netlify domain.
5. In Netlify: Project configuration > Environment variables. Add:
   Key: OPENAI_API_KEY
   Value: your OpenAI API secret key
   Make sure the variable is available to Functions/runtime.
6. Trigger a new deploy after adding the variable.
7. Test the assistant on the Netlify URL. If the key is missing, the function returns a clear configuration error.
8. Keep the GitHub Pages version as a static fallback, or replace its link in your submission with the working Netlify URL once tested.

Security:
- NEVER put the API key in index.html, GitHub, README, or netlify.toml.
- Add the key only in Netlify's Environment Variables UI.
- API use can incur charges.
- This assistant answers from the curated investigation summaries supplied by the dashboard. It does not fetch NASA PSI live.


AI DIAGNOSTIC CHECK (after deployment):
1. Open https://YOUR-SITE.netlify.app/.netlify/functions/ask in a browser.
2. A healthy function returns JSON with:
   "function": "online"
   "apiKeyConfigured": true
3. If the page is 404, Netlify did not deploy the function. Confirm the deployed folder contains netlify/functions/ask.js and netlify.toml at the project root.
4. If apiKeyConfigured is false, add OPENAI_API_KEY in Netlify Project configuration > Environment variables. Scope it to Functions if Netlify offers scopes, then trigger a new deploy.
5. If apiKeyConfigured is true but the assistant fails, the message shown in the Ask FireGuard panel now includes the provider error. Check Netlify > Logs > Functions > ask for details.
6. Never share the API key in chat, screenshots, source code, or GitHub.
