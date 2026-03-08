# write-blog

Claude Code skill for writing and publishing blog posts to [johnsonlee.io](https://johnsonlee.io) (Hexo + GitHub Pages).

## Trigger Examples

- "写一篇关于 xxx 的博客"
- "把这个整理成博客"
- "写个技术分享"
- "blog about xxx"

## Workflow

Topic alignment -> draft generation -> quote normalization -> user review -> publish to GitHub.

## Files

| File | Description |
|---|---|
| `SKILL.md` | Skill definition: workflow, formatting rules (front matter, file naming, excerpt marker), and a detailed writing style guide tailored to Johnson's voice |
| `fix_quotes.py` | Auto-normalizes quote marks in Markdown -- Chinese content gets curly double quotes, English content gets straight double quotes. Skips code blocks and YAML front matter |
| `push_to_github.sh` | Pushes a post to `johnsonlee/blog` repo via GitHub API. Handles both create and update (fetches SHA if file already exists) |

## Runtime Environments

In **Claude Code**, posts are pushed using `gh api` directly (requires `gh auth` login).

In **Claude Web**, the `gh` CLI is not available, so `push_to_github.sh` is used instead (requires a `GITHUB_TOKEN` environment variable).
