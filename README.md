# New


Proceed with the following architecture:

- Our learners will have only SQL Practice Studio platform accounts.
- Create a separate least-privilege, non-admin Service Principal for Databricks execution.
- Use Databricks Jobs API with Serverless compute for learner PySpark execution.
- Never execute learner code using workspace admin credentials.
- Native Databricks notebook creation and management will be admin-only.
- Do not require learners to sign in to Databricks.
- Keep the existing Local PySpark Runner fully functional.
- Keep remote execution disabled until the dedicated Service Principal credentials, permissions and Free Edition compatibility are verified.
- Provide clear setup instructions for the required backend environment variables.
- Do not expose secrets to the frontend or commit them to GitHub.

The main learner experience must remain entirely inside SQL Practice Studio.



---------
The initial implementation checks have passed. Now proceed with the Databricks remote execution verification phase.

Requirements:

1. Inspect the current Databricks integration and identify all remaining configuration requirements.
2. Verify the dedicated non-admin Service Principal configuration.
3. Verify OAuth authentication against my Databricks workspace.
4. Verify Jobs API access.
5. Verify Serverless compute compatibility with my Databricks Free Edition workspace.
6. Verify access to workspace.default.practice_files.
7. Submit a minimal safe PySpark test job and capture its actual execution result.
8. Verify error handling, timeout handling and execution logs.
9. Confirm that the Local PySpark Runner remains functional.
10. Keep remote execution gated until all live tests pass.

Do not use workspace admin credentials for learner code execution.

Do not deploy to production or modify existing production environment variables without my explicit approval.

At the end, provide a clear report showing which tests passed, failed, or remain blocked.



---------
Understood. Keep Databricks remote execution disabled.

Please do the following:

1. Preserve all completed security fixes.
2. Do not enable any remote execution readiness flags.
3. Keep the existing Local PySpark Runner available.
4. Keep native notebook creation admin-only.
5. Prepare a clear checklist of the remaining manual Databricks configuration.
6. Identify the exact Service Principal permissions required.
7. Explain how to verify Serverless Jobs API compatibility in my Free Edition workspace.
8. Provide the exact backend environment variable names required, without displaying or exposing secret values.
9. Once I complete the configuration, provide a safe live verification procedure.
10. Do not deploy or enable learner execution without successful verification and my approval.

Provide a final report separating completed work from pending configuration.
++++++++++
+++++++++

Task: Configure and Verify Databricks Non-Admin Service Principal Integration

I have added the new Non-Admin Databricks Service Principal credentials to my local backend ".env" file.

New credentials:

- DATABRICKS_HOST
- DATABRICKS_CLIENT_ID
- DATABRICKS_CLIENT_SECRET

Please perform the following tasks carefully.

1. Inspect Existing Backend Implementation

- Inspect the existing Databricks integration code.
- Identify which environment variable names the backend actually expects.
- Check the OAuth authentication implementation.
- Identify whether the application uses Databricks Jobs API, Databricks Connect, or another execution method.
- Do not assume that the proposed environment variable names or API configuration are correct.

2. Validate Environment Configuration

- Verify that the backend can read the three environment variables.
- Never print Client Secret, OAuth tokens, or other credentials in logs or terminal output.
- Never expose credentials to frontend code.
- Never commit ".env" to Git.
- Check ".gitignore" and ".env.example".
- Keep only placeholder values in ".env.example".

3. Verify OAuth Authentication

- Verify OAuth M2M authentication using the new Non-Admin Service Principal.
- Check whether the configured OAuth scope is sufficient for the actual API calls.
- Do not use the old Admin Service Principal credentials.
- Do not request or use workspace Admin credentials.

4. Verify Permissions

Check whether the new Service Principal has the necessary permissions for:

- Workspace access, if required.
- Databricks Jobs execution.
- Serverless compute execution, if supported.
- Unity Catalog catalog and schema access.
- Reading and writing to the existing Volume:
  /Volumes/workspace/default/practice_files/

Do not grant unnecessary permissions or Admin access.

5. Preserve Existing Functionality

- Keep the existing Local PySpark Runner working.
- Do not break SQL Lab, Python Lab, or existing PySpark functionality.
- Keep local and Databricks execution modes separate.
- Do not expose native Databricks notebook links to learners who do not have workspace access.

6. Security Requirements

- Do not use the Admin Service Principal.
- Do not enable Admin access for the new Principal.
- Do not expose credentials or tokens.
- Implement execution timeout, concurrency limits, safe error handling and log redaction.
- Do not execute learner code with an Admin identity.

7. Testing

Perform safe configuration checks first.

Then report:

1. Environment variable configuration status.
2. OAuth authentication status.
3. Service Principal identity verification.
4. Jobs API availability.
5. Serverless compute compatibility with Databricks Free Edition.
6. Unity Catalog permissions.
7. Volume access status.
8. Local PySpark Runner status.

Do not claim that remote execution works unless a real test job successfully executes.

8. Important Restrictions

- Do not deploy to production.
- Do not modify Render production environment variables.
- Do not enable remote execution automatically.
- Keep DATABRICKS_ENABLED or equivalent readiness flags disabled until all required security and live execution tests pass.
- Do not delete or modify existing Admin Service Principal credentials.

At the end, provide a detailed report of completed checks, failures, missing permissions, and the exact next steps.

Do not make assumptions about Databricks Free Edition capabilities. Verify compatibility before implementing remote execution.
