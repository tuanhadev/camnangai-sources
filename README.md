# camnangai-sources

Agent-fetchable reference content for [camnangai.com](https://camnangai.com) articles.

## Why this repo exists

The AI writing workflow in [`tuan-side-project1`](https://github.com/tuanhadev/tuan-side-project1) runs on GitHub Actions. Cloudflare-protected sources (Substack, Hashnode, Medium, Notion) return HTTP 403 to the runner's Azure IPs, so URLs pointing at those hosts get silently dropped from articles.

Files in this repo are served by `raw.githubusercontent.com`, which is bot-friendly. Use this repo as the **canonical agent-readable copy** of any source material that lives on a Cloudflare-blocked host.

## How to use

1. Save the source content as a markdown file under `articles/<slug>.md`.
2. Commit and push to `main`.
3. In the Linear ticket's **References** field, use the raw URL:

   ```
   https://raw.githubusercontent.com/tuanhadev/camnangai-sources/main/articles/<slug>.md
   ```

4. (Optional) Also list the original public URL (e.g. the Hashnode page) so readers of the published article can click through to the human-facing version. The agent cites whichever URL is in the References field.

## Folder conventions

```
articles/   - One markdown file per source article. Filename = slug.
notes/      - (future) Personal drafts, outlines, research notes.
```

Keep filenames URL-safe (lowercase, hyphens, no spaces).

## Verifying a file is agent-fetchable

```bash
curl -sS -o /dev/null -w '%{http_code}\n' \
  https://raw.githubusercontent.com/tuanhadev/camnangai-sources/main/articles/<slug>.md
```

Expected: `200`. Anything else means the file isn't there yet or the path is wrong.
