git hooks that I use on all my repos.

## Hooks

- `pre-commit-catch-do-not-commit-flag`
	- Checks if the words "do not commit" exist in any of the modified files.
- `pre-commit-no-duplicate-words`
	- Checks if duplicate words (ex: "of of") exist in any of the modified files. 
- `pre-commit-no-trailing-whitespace`
	- Checks if there is any trailing whitespace in any of the modified files.
- `pre-commit-focus-tags`
  - Checks if there are any ":focus" tags left in any spec files.

## Installation

```
$ git clone … ~/src/git_hooks
$ cd my_awesome_repo
$ ~/src/git_hooks/setup
```

## Development

- There is one script for each check we want to do as a part of the hook.
- The files are named `[hook name]-[check_name]`, ex: `pre-commit` `-` `no-trailing-whitespace`
- Then we have one script run `[hook name]-*` and aggregate the results

## Implementation Notes

### Why use symlinks instead of git init.templatedir?
Because running `git init` with a specified `init.templatedir` just copies over (and does not overwrite) files, which makes getting updates to these commit hooks difficult.
