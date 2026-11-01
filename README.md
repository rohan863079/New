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
