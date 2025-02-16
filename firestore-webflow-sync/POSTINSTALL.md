### Create webhooks in webflow (One time setup)

1. After the extension installation, find the webhook function's trigger url from function details page (Google Console > Functions > ext-firestore-webflow-sync-webflowHook > Trigger). Trigger url will be in the following format: `https://${location}-${project-id}.cloudfunctions.net/ext-firestore-webflow-sync-webflowHook`
   You can check if the function is deployed correctly using the health endpoint (Trigger url + `/health`): GET `https://${location}-${project-id}.cloudfunctions.net/ext-firestore-webflow-sync-webflowHook/health` should return `{"status": "running"}` as response.

2. Update the Redirect URI of the webflow application from workspace settings page (Workspace Settings > Integrations > Workspace Applications) to `auth-success` endpoint (Trigger url mentioned above + `/auth-success`
3. Authorize the webflow app to create webhook endpoints by opening the authorize endpoint (Trigger url + `/authorize`) on a browser. User will be redirected to webflow oauth page and complete the authorization. Once completed, user will be redirected to `/auth-success` and should see the response `{"status": "success"}`.
4. Verify whether webhooks are created for the site from webflow site settings page (Webflow Site Settings > Integrations > Webhooks)
