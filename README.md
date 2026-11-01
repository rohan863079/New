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
