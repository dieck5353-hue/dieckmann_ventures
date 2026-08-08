# FEOS Repository Factory

The factory creates initialized **private** repositories under `dieck5353-hue` from controlled GitHub issues in `dieckmann_ventures`.

## FEOS operating route

1. Create an issue whose title begins `[FEOS REPO]` and whose body uses the sections in the repository-request form.
2. Assign the issue to `dieck5353-hue`.
3. Add the `feos-repo-approved` label. Adding this label is the privileged execution trigger.
4. Wait for the workflow to comment with the created repository URL and close the request.
5. Confirm the new repository is visible through the ChatGPT Codex Connector before writing product code.

## Standing authority

FEOS may create, initialize, and operate private repositories. It may not make a repository public, transfer it, archive it, or delete it without the owner's approval. The workflow exposes no operation for those actions.

## Credential handling

The fine-grained token is stored only as the encrypted Actions secret `FEOS_REPO_TOKEN`. Never place it in source files, issues, workflow inputs, logs, or chat. Rotate the token before expiration and update the secret in repository settings.

## Failure behavior

A failed request stays open and receives a link to its workflow run. Fix the configuration or request data, remove the `feos-repo-approved` label, and add it again to retry. Existing repositories are treated idempotently and are never overwritten.
