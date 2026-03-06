# Copilot Instructions for hazel-bohon.github.io

This repository is a Jekyll-based academic portfolio and personal website, forked from Academic Pages and built on the Minimal Mistakes Jekyll Theme. It is designed for GitHub Pages deployment and local development with Ruby, Bundler, and Node.js, or via Docker/DevContainer.

## Architecture & Key Components
- **Jekyll site**: Content is organized in `_posts/`, `_pages/`, `_data/`, `_includes/`, `_layouts/`, `_sass/`, and asset folders. Site configuration is in `_config.yml`.
- **Custom Data**: `_data/` holds YAML/JSON for authors, navigation, CV, and UI text. These are referenced in layouts and includes for dynamic content.
- **Markdown & HTML**: Content pages are Markdown (`.md`) or HTML (`.html`), with YAML front matter for metadata.
- **Python/Jupyter**: `talkmap.py` and `talkmap.ipynb` are used for generating or analyzing content (e.g., talk maps). Output may be written to `talkmap_out.ipynb` or similar files.
- **Docker/DevContainer**: Supports containerized development and builds. See `Dockerfile`, `docker-compose.yaml`, and `.devcontainer/`.

## Developer Workflows
- **Local Development**:
  - Install Ruby, Bundler, and Node.js (see README for platform-specific commands).
  - Run `bundle install` (use `bundle config set --local path 'vendor/bundle'` if permission errors).
  - Start the site locally: `jekyll serve -l -H localhost` or `bundle exec jekyll serve -l -H localhost`.
  - Access at [http://localhost:4000](http://localhost:4000).
- **Docker/DevContainer**:
  - Run `docker compose up` to build and serve the site in a container.
  - In VS Code, use "Dev Container: Reopen in Container" for a pre-configured environment.
- **Content Generation**:
  - Use scripts in `markdown_generator/` or Jupyter notebooks to generate markdown for publications/talks from TSV or other data.
  - Place generated files in appropriate content folders (`_posts/`, `_talks/`, etc.).
- **Static Assets**: Place PDFs and other files in `files/` for direct linking.

## Project-Specific Conventions
- **YAML/JSON in `_data/`**: Used for dynamic site sections (navigation, CV, authors, UI text). Reference these in includes/layouts.
- **Custom Includes/Layouts**: `_includes/` and `_layouts/` contain reusable HTML partials and page templates. Use these for consistent site structure.
- **Front Matter**: All content pages require YAML front matter for Jekyll processing.
- **No direct editing of `_site/`**: This is the build output and should not be modified directly.
- **Fork/Sync Guidance**: If customizing the theme, be aware of merge conflicts when syncing with upstream. Manual patching may be required.

## Integration Points & External Dependencies
- **Jekyll plugins and Ruby gems**: Managed via `Gemfile`.
- **Node.js**: Used for asset pipeline (if needed).
- **Python**: Used for content generation scripts/notebooks.
- **GitHub Actions**: Used for deployment (see repository badges and workflows).

## Key Files & Directories
- `_config.yml`: Main site configuration.
- `Gemfile`, `Gemfile.lock`: Ruby dependencies.
- `Dockerfile`, `docker-compose.yaml`: Container setup.
- `.devcontainer/`: VS Code DevContainer config.
- `_data/`, `_includes/`, `_layouts/`, `_sass/`: Core Jekyll structure.
- `markdown_generator/`, `talkmap.py`, `talkmap.ipynb`: Content generation tools.
- `README.md`: Essential setup and workflow instructions.

## Example: Adding a New Publication
1. Add publication data to `_data/publications.yml` or use a script in `markdown_generator/` to generate a new markdown file in `_publications/`.
2. Ensure the file has correct YAML front matter.
3. Rebuild the site locally or in Docker to preview changes.

---
For more, see the [README.md](../README.md) and comments in key config files. Follow existing patterns for new content and site customization.
