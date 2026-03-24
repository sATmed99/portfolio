# Copilot Workspace Instructions

## Overview
This workspace is a minimalist Jekyll theme for academic sites, based on "The Plain Academic". It is designed for simplicity and easy customization, primarily using Markdown and HTML with Jekyll conventions.

## Build & Test Commands
- **Build locally:**
  - Install dependencies: `bundle install`
  - Serve locally: `bundle exec jekyll serve`
- **Key files:**
  - `_config.yml`: Main configuration
  - `Gemfile`: Ruby gem dependencies
  - `_layouts/`, `_includes/`, `_sass/`: Theme structure
  - `assets/`, `img/`, `script/`: Static assets and scripts

## Conventions
- Use Markdown for content in `_posts/`, `_projects/`, `_researches/`, `_talks/`, and `_blog/`.
- Layouts and includes are in their respective folders and follow standard Jekyll naming.
- Custom styles go in `assets/core.scss` and `_sass/`.
- Add new pages as `.md` or `.html` in the root directory.
- Use `jekyll-remote-theme` for theme updates (see README for setup).

## Pitfalls & Tips
- Always run `bundle install` after modifying the `Gemfile`.
- If using GitHub Pages, ensure plugins are supported or use a build action.
- For local development, Ruby and Bundler must be installed.
- Images should be placed in the `img/` directory or subfolders.

## Documentation
- See [README.md](README.md) for theme setup and licensing.
- No additional docs, contributing, or architecture files found.

## Example Prompts
- "How do I add a new blog post?"
- "How do I change the site title?"
- "How do I update the theme or add a new page?"

---

For further customization, consider creating agent instructions for content automation, post templating, or deployment workflows.
