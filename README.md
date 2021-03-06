# svu

[![Build Status](https://img.shields.io/github/workflow/status/caarlos0/svu/build?style=for-the-badge)](https://github.com/caarlos0/svu/actions?workflow=build)

Semantic Version Util is a tool to manage semantic versions at ease!

You can print the current version, increase patch/minor/major manually or just
get the next tag based on your git log!

## Example usage:

### `svu`

Based on the log between the latest tag and `HEAD`, prints the next tag.

> aliases: `svu next` and `svu n`

```sh
$ svu
v1.3.0
```

#### Commit messages vs what they do:

| Commit message | Tag increase |
|---|---|
| `fix: fixed something` | Patch |
| `feat: added new button to do X` | Minor |
| `fix: fixed thing xyz`<br><br>`BREAKING CHANGE: this will break users because of blah` | Major |
| `fix!: fixed something` | Major |
| `feat!: added blah` | Major |
| `chore: foo` | Nothing |

### `svu current`

Prints the latest tag.

> alias: `svu c`

```sh
$ svu current
v1.2.3
```

### `svu major`

Increases the major of the latest tag and prints it.

```sh
$ svu major
v2.0.0
```

### `svu minor`

Increases the minor of the latest tag and prints it.

> alias: `svu m`

```sh
$ svu minor
v1.3.0
```

### `svu patch`

Increases the patch of the latest tag and prints it.

> alias: `svu p`

```sh
$ svu patch
v1.2.4
```

## Creating tags

The idea is that `svu` will just print things, so its safe to run at any time.

You can create tags by wrapping it in an alias. For example, I have one like
this:

```bash
alias gtn='git tag $(svu next)'
```

So, whenever I want to create a tag, I just run `gtn`.

## Install

```sh
go get github.com/caarlos0/svu
```

or

```sh
brew install caarlos0/tap/svu
```

or

```sh
curl -sfL https://install.goreleaser.com/github.com/caarlos0/svu.sh | bash -s -- -b /usr/local/bin
```

Or download one from the releases tab and install manually.
