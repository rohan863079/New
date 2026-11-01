Fix Databricks OAuth 403 - Non-Admin Executor Only

The latest diagnostic report shows HTTP 403 during OAuth token generation and an unconfirmed Service Principal identity.

Please investigate and fix the authentication configuration without using any Admin credentials.

A. Verify credentials and identity

- Read DATABRICKS_HOST, DATABRICKS_CLIENT_ID and DATABRICKS_CLIENT_SECRET from the backend environment.
- Confirm the Client ID matches the Application ID of SQL-Practice-Studio-Executor.
- Never print secrets, tokens or credential values.
- Verify that this Service Principal is assigned to the correct Databricks workspace.
- Check for conflicting authentication environment variables such as DATABRICKS_TOKEN.

B. Fix OAuth scope handling

- Inspect the actual OAuth token request implementation.
- Do not send an invented combined scope such as "workspace jobs unity-catalog".
- Prefer the official Databricks SDK unified authentication for OAuth M2M.
- If manual OAuth is used, follow the official Databricks workspace-level M2M token flow.
- Respect the OAuth secret's configured jobs scope.
- Do not use all-apis as a way to bypass the secret's configured restrictions.
- Do not request unity-catalog APIs unless the secret and actual implementation are configured for them.

C. Separate authentication and authorization tests

Run these checks independently:

1. OAuth token issuance.
2. Verify the authenticated identity using an appropriate non-admin identity endpoint.
3. Check Jobs API access.
4. Check Unity Catalog access separately.
5. Check the existing practice_files Volume separately.

Report the exact HTTP status and safe error message for each test.

D. Unity Catalog

- Confirm whether workspace.default.practice_files is a Volume.
- Do not query it as a table.
- Check the correct Volume API and object permissions.
- Do not grant permissions automatically.

E. Security

- Never use the old Admin Principal.
- Never add the new Executor to the admins group.
- Never enable Admin access.
- Do not expose credentials to frontend or logs.
- Do not deploy to production.
- Keep remote execution disabled until all tests pass.

At the end, explain the exact cause of HTTP 403 and the minimum permissions or configuration changes required. Do not claim success without a successful live test.
