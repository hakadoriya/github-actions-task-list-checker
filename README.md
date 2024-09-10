# Pull-Request Body Task List Checker

If the pull request body contains a task list, check if all the tasks are completed.  

```markdown
- [x] task1
- [ ] task2
- [ ] task3
```

Like above, if there is a task list in the pull request body, this action will check if all the tasks are completed.  
If there is an incomplete task, the status check will fail.  

## example

```yml
name: task-list-checker

on:
  pull_request:
    types:
      - opened
      - edited
      - ready_for_review
      - reopened
      - synchronize

jobs:
  task-list-checker:
    if: github.actor != 'dependabot[bot]'
    runs-on: ubuntu-latest
    timeout-minutes: 10
    permissions:
      pull-requests: read
    steps:
      - uses: hakadoriya/github-actions-task-list-checker@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```
