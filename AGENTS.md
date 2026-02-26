# AGENTS.md

## Cursor Cloud specific instructions

This is a static Jekyll/GitHub Pages site (Arduino Cheat Sheet). There is no backend, no tests, no linter, and no build pipeline beyond Jekyll.

### Services

| Service | Command | Notes |
|---|---|---|
| Jekyll dev server | `bundle exec jekyll serve --host 0.0.0.0 --port 4000` | Serves at `http://localhost:4000`. Auto-regeneration is enabled by default. |

### Prerequisites

- Ruby 3.x and Bundler must be installed (`sudo apt-get install -y ruby-full build-essential zlib1g-dev && sudo gem install bundler`).
- Run `sudo bundle install` in the repo root to install gems (requires write access to system gem dir).

### Gotchas

- `bundle install` needs `sudo` because gems install to `/var/lib/gems/`. Alternatively, configure a user-local gem path.
- The GitHub Metadata warning ("No GitHub API authentication could be found") is harmless for local dev; some GitHub-specific metadata fields will be empty.
- The generated `_site/` directory and `Gemfile.lock` are build artifacts. `_site/` is not checked in.
