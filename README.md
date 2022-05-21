# Automate adding labeled issues to GitHub Beta projects

Action: https://github.com/actions/add-to-project

Create personal token with repo and admin:org permissions

![screenshot](https://user-images.githubusercontent.com/2863246/169510280-1a785454-01c8-4fa5-a293-0cad0b0c5cc1.png)

Add secret to repo where you want issues/PRs from.

Add workflow to repo where you want issues from.

```
name: Add docs to docs project

on:
  issues:
    types:
      - labeled

jobs:
  add-to-project:
    name: Add issue to project
    runs-on: ubuntu-latest
    steps:
      - uses: actions/add-to-project@main
        with:
          project-url: https://github.com/orgs/developerka/projects/1
          github-token: ${{ secrets.ADD_TO_PROJECT_PAT }}
          labeled: docs, 6.1
          label-operator: OR

```

Note `on`, can be `issues` and `pull_request`. https://github.com/developerka/add-to-project#supported-events
Also, types can be different.

Under `jobs` - `labeled`.
