# GitHub Action to trigger a CircleCI pipeline

Triggers a CircleCI pipeline run for the given branch as if new changes had been committed to it

## Usage

### Inputs

- `circleci-token`: The CircleCI token to allow authenticated API calls
- `repository`: The repository to trigger the pipeline for (defaults to current repository)
- `branch`: The branch to trigger the pipeline for (defaults to current branch for pull requests)
- `parameters`: The pipeline parameters to be passed to the triggered pipeline, formatted as a JSON object

### Example Workflow

```yaml
# Triggers CircleCI checks when the PR is marked as "Ready for Review"
name: Trigger CircleCI
on:
  pull_request:
    types: [ready_for_review]

jobs:
  trigger-circleci:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger CircleCI action
        uses: voiceflow/trigger-circleci@latest
        with:
          circleci-token: ${{ secrets.CIRCLECI_TOKEN }}
          parameters: '{ "build-frontend": true }'
```

## License

MIT
