# Profile Data — Single Source of Truth

Canonical structured data for Johny A. Pedraza Romero's public profiles.

## Consumers

| Consumer | Repo | How it consumes |
|---|---|---|
| CV (RenderCV) | `JohnyYen/my-cv` | `generators/generate_cv.py` → RenderCV YAML → GitHub Action → PDF release |
| Portfolio | `JohnyYen/my-portfolio-terminal` | Fetch `data/*.json` from `raw.githubusercontent.com` at build (ISR) |
| GitHub Profile | `JohnyYen/JohnyYen` | Workflow runs `generators/generate_github_readme.py` → commits README |
| LinkedIn | Manual | `generators/generate_linkedin.py` → copy-paste text |

## Data Files

- `data/about.json` — name, headline, tagline, bio, location, email, phone, languages
- `data/social.json` — github, linkedin, website, cvUrl
- `data/experience.json` — work history
- `data/education.json` — academic background
- `data/projects.json` — canonical project list
- `data/skills.json` — categorized skills
- `data/publications.json` — publications (placeholder)
- `data/interests.json` — personal interests

## Schema

Each file has a corresponding JSON Schema in `schemas/`. Run `generators/validate.py` to validate.

## Editing

1. Edit the relevant `data/*.json` file(s)
2. Run `generators/validate.py` to check
3. Run the appropriate generator to produce artifacts
4. Commit and push — downstream consumers pick up changes on their next build
