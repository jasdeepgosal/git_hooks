git hooks that I use on all my repos.

## Hooks

### pre-commit
- `pre-commit-catch-do-not-commit-flag`
	- Checks if the words "do not commit" exist in any of the modified files.
- `pre-commit-no-duplicate-words`
	- Checks if duplicate words (ex: "of of") exist in any of the modified files. 
- `pre-commit-no-trailing-whitespace`
	- Checks if there is any trailing whitespace in any of the modified files.
- `pre-commit-focus-tags`
  - Checks if there are any ":focus" tags left in any spec files.
- `pre-commit-rubocop`
  - Runs `rubocop` on any modified `*.rb` files.
- `pre-commit-rails_best_practices`
  - Runs `rails_best_practices` on any modified files, but ignores "remove unused" warnings because they're inaccurate when not being run on the full codebase.
- `pre-commit-commit-directly-on-master`
  - Checks if you're committing directly on master.

### prepare-commit-msg
- `prepare-commit-msg`
  - Check if there is a pivotal tracker story number in the branch name & automatically adds the tag.

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
