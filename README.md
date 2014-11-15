git_template directory composed primarily of various commit hooks. 

## Installation

```
$ git clone … ~/src/git_template
$ git config --global init.templatedir '~/src/git_template'
$ ~/src/git_template/setup.sh
```

## Usage

- The plan is to have one script for each check we want to do as a part of the hook, then name the file `[hook name]-[check_name]`, ex: `pre-commit` `-` `no-trailing-whitespace`
- Then we have one script run `[hook name]-*` and aggregate the results

Hooks:
- `pre-commit-catch-do-not-commit-flag`
- `pre-commit-no-duplicate-words`
- `pre-commit-no-trailing-whitespace`

---
Installation Instructions:
- After checking out this branch or merging this into master, run: 
`cw_mainsite/etc/hooks/setup` 

