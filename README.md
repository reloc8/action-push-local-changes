# Push Local Repository Changes

A Github Action to push local repository changes to remote.

By default commits are made by Github Actions bot `github-actions`. 
You can specify a custom username with input `commit-username` and a custom email with input `commit-email`.

## Usage

```
jobs:
  job-name:
    runs-on: ubuntu-latest
    steps:

      - uses: actions/checkout@v2

      - name: Create a new file
        run: touch new_file.txt

      - name: Push local repository changes
        id: push-local-repository-changes
        uses: reloc8/action-push-local-changes@1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          commit-message: 'Create new file'

      - name: Test
        run: echo ${{ steps.push-local-repository-changes.outputs.commit-hash }}
``` 
