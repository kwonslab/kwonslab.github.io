# Local Development Setup for the Kwon Lab Website

This guide describes how to set up a local Jekyll environment for the Kwon Lab website on macOS, preview changes, and publish them to GitHub Pages.

- Repository: <https://github.com/kwonslab/kwonslab.github.io>
- Website: <https://kwonslab.github.io/>
- Theme: [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)
- Ruby tools: Homebrew, `ruby-install`, and `chruby`

> The repository currently uses `remote_theme: "mmistakes/minimal-mistakes@4.13.0"` and declares `github-pages`, `minimal-mistakes-jekyll`, and several older plugins in its `Gemfile`. Preserve the existing dependency setup while getting the first local build working; do not run `bundle update` as a first troubleshooting step.

## 1. Install Apple's command-line tools

```bash
xcode-select --install
```

If macOS reports that the tools are already installed, continue.

## 2. Install Homebrew

Check whether Homebrew is installed:

```bash
brew --version
```

If needed, install it using the official instructions at <https://brew.sh/>. The standard installer command is:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow any additional instructions printed by the installer, then check `brew --version` again.

## 3. Install Ruby version management tools

```bash
brew install chruby ruby-install
```

For Zsh, configure `chruby` in `~/.zshrc`:

```bash
echo 'source "$(brew --prefix)/opt/chruby/share/chruby/chruby.sh"' >> ~/.zshrc
echo 'source "$(brew --prefix)/opt/chruby/share/chruby/auto.sh"' >> ~/.zshrc
source ~/.zshrc
```

Check the shell with `echo $SHELL`. If using Bash or another shell, configure the appropriate startup file instead.

## 4. Clone or enter the repository

For the current Mac, the repository is at:

```bash
cd /Users/stephaniekwon/Documents/Projects/labsite/kwonslab.github.io
```

On a new Mac, clone it first (use the SSH URL if SSH access has been configured):

```bash
git clone git@github.com:kwonslab/kwonslab.github.io.git
cd kwonslab.github.io
```

Check that you are in the repository root:

```bash
pwd
ls -la
```

## 5. Inspect the project's Ruby requirements

Run these commands **from the repository root**:

```bash
ls -la Gemfile Gemfile.lock .ruby-version 2>/dev/null
cat Gemfile
cat .ruby-version 2>/dev/null
grep -nE 'RUBY VERSION|BUNDLED WITH|jekyll|github-pages|sassc|faraday' Gemfile.lock 2>/dev/null
```

If `.ruby-version` exists, inspect it and use a compatible Ruby version. If `Gemfile.lock` exists, it records the dependency versions previously resolved. If either file is absent, do not assume a specific Ruby version solely from that absence; use the `Gemfile` and any installation errors to choose a compatible version.

Install a Ruby version with `ruby-install` only after choosing it. For example, if Ruby `3.3.6` is selected:

```bash
ruby-install ruby 3.3.6
chruby ruby-3.3.6
ruby -v
which ruby
gem -v
```

`3.3.6` is an example, not a confirmed requirement for this repository. Replace it consistently with the version you actually install. Older gems may not build with every newer Ruby version, so check the actual dependency constraints and errors before selecting a version.

## 6. Install Bundler and dependencies

From the repository root, with the selected Ruby active:

```bash
gem install bundler
bundle install
```

Bundler installs the gems declared by the repository's `Gemfile`. If no `Gemfile.lock` exists, it will normally create one when resolving dependencies.

Do not run `bundle update` just to address an error. First inspect the error; this older `Gemfile` includes a historical `faraday` version constraint, which may affect dependency resolution. Make dependency changes deliberately and test the site after each change.

## 7. Run Jekyll locally

From the repository root:

```bash
bundle exec jekyll serve --livereload
```

Open <http://localhost:4000/> in your browser. Keep Terminal running while previewing the site. Stop the server with **Control+C**.

Most content edits trigger a rebuild automatically. Changes to `_config.yml` generally require stopping and restarting the server.

## 8. Check and publish changes

Review the changes before committing:

```bash
git status
git diff
```

Stage and commit the intended files, then push:

```bash
git add <files-to-commit>
git commit -m "Describe website update"
git push
```

Use `git add .` only after checking `git status`, so you do not accidentally commit generated files, local settings, or secrets. GitHub Pages will publish according to the repository's configured deployment method. Check the repository's **Actions** tab if a deployment fails.

## 9. New-Mac checklist

1. Install Apple's command-line tools.
2. Install Homebrew.
3. Install `chruby` and `ruby-install`; configure the shell.
4. Clone the repository.
5. Inspect `Gemfile`, `Gemfile.lock`, and `.ruby-version` if present.
6. Install and activate a compatible Ruby version.
7. Run `gem install bundler` and `bundle install`.
8. Run `bundle exec jekyll serve --livereload` and inspect the site at <http://localhost:4000/>.
9. Commit and push only after reviewing the changes.

## Useful official documentation

- [Jekyll on macOS](https://jekyllrb.com/docs/installation/macos/)
- [Jekyll installation](https://jekyllrb.com/docs/installation/)
- [Minimal Mistakes quick-start guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
