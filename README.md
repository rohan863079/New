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
