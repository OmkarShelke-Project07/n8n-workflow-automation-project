# Testing Strategy

The repository includes lightweight automated checks and manual test checklists. The checks validate the files in Git; they do not run the workflows against live integrations.

## 1. Repository checks

The GitHub Actions workflow checks:

- Workflow JSON syntax.
- Basic workflow structure (`name`, `nodes`, and `connections`).
- That exported workflows are inactive.
- That each workflow folder contains a README.
- Several common hard-coded secret and personal-email patterns.

These checks do not prove that a workflow imports cleanly in every n8n version, that credentials work, or that a complete execution succeeds.

## 2. Manual workflow tests

For each workflow:

1. Import the JSON into a test n8n instance.
2. Reconnect credentials and configure test-only resource IDs.
3. Read the project README and confirm that node fields match the test input.
4. Run sample inputs through success and failure paths.
5. Inspect node outputs, the final result in the connected service, and the execution history.
6. Leave the workflow inactive until outputs and recipients are verified.

Use synthetic or non-sensitive information wherever possible. For voice and publishing workflows, use destinations and phone numbers you control.

## Test documentation

| Workflow | Test documentation |
|---|---|
| AI Invoice Processing | [Invoice test cases](../../tests/invoice-processing/test-cases.md) |
| AI Lead Qualification | [Lead qualification test cases](../../tests/lead-qualification/test-cases.md) |
| RAG Document Agent | [RAG test cases](../../tests/rag-agent/test-cases.md) |
| AI Lead Capture | Manual checklist in the [project README](../../workflows/04-ai-lead-capture/README.md) |
| Department Intelligence Agent | Manual checklist in the [project README](../../workflows/05-department-intelligence-agent/README.md) |
| AI Content Generation | Manual checklist in the [project README](../../workflows/06-ai-content-generation/README.md) |

## Recommended test scenarios

- Valid input and expected output.
- Missing or malformed fields.
- External API timeout, rate limit, or authentication failure.
- Duplicate input where relevant.
- Partial failure in a downstream service.
- Incorrect or empty model output.
- Confirmation that an unsuccessful run is not recorded as a successful result.

## Future improvements

- Add automated JSON-schema and export linting.
- Add dedicated secret scanning.
- Add repeatable mocked integration tests where practical.
- Add version-specific import smoke tests and documented n8n version compatibility.
