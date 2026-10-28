# Contributing

Please create an issue or open a PR. Including as much detail as possible will help me get through everything as quickly as possible. Thank you!

## Commits

- **[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)**, checked in CI by [`commits / validate`](https://github.com/LeafLab-sh/shared-workflows). Repositories with git hooks also run commitlint locally.
- **Curate history.** Each commit is one logical, reviewable change that builds and passes on its own. `main` gets the commits as they are, with no squashing.
- **Link Linear issues** with a commit footer:

  ```text
  feat: add the thing

  Refs: LEA-123
  ```

## Pull requests

1. Open the PR into `main` as a **draft**. Link Linear issues in the body with `Fixes LEA-123`, which closes the issue on merge, or `Part of LEA-123`, which links it without closing.
2. **Self-review** the diff, and wait for **CI to pass**. Then mark it ready for review.
3. **Fix findings with fixup commits** against the commit they correct, so reviewers can see what changed:

   ```sh
   git commit --fixup=<sha>
   ```

4. **Curate before merging.** `fixup!` commits never reach `main`. Squash them into their targets, then let CI pass again:

   ```sh
   GIT_SEQUENCE_EDITOR=: git rebase -i --autosquash origin/main
   git push --force-with-lease
   ```

   CI rejects any PR that still contains `fixup!`, `squash!` or `amend!` commits.

5. **Merge with rebase.** It's the only merge method enabled.

**Auto-merge** is fine only in repositories with required status checks, where it can't merge something CI hasn't passed.

## Conduct

[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-3.0-4baaaa.svg)](CODE_OF_CONDUCT.md)
