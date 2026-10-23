# shantikorporaal.com

Personal site of Shanti Korporaal: articles, series and a portfolio.

Built with [Hugo](https://gohugo.io/) and the [Blowfish](https://blowfish.page/) theme (Princess colour scheme), published to GitHub Pages by GitHub Actions on every push to `main`.

## Rules

- Nothing personal goes on the site without Shanti's approval.
- Content drawn from the private about-me repo follows that repo's external-use rules.

## Where things live

| What | Where |
| --- | --- |
| Site settings (title, URL) | `config/_default/hugo.toml` |
| Theme settings (colours, layouts, features) | `config/_default/params.toml` |
| Name, headline, bio, social links | `config/_default/languages.en.toml` |
| Menus | `config/_default/menus.en.toml` |
| Homepage text | `content/_index.md` |
| Articles | `content/posts/<slug>/index.md` |
| Portfolio | `content/portfolio.md` |
| About | `content/about.md` |
| Contact (LinkedIn button; add a form here later) | `content/contact.md` |
| Series landing titles | `content/series/<name>/_index.md` |
| Site-wide images (profile photo, background) | `assets/img/` |
| Theme (git submodule, don't edit) | `themes/blowfish/` |
| Deploy workflow | `.github/workflows/hugo.yml` |

## Publishing an article

1. Create a folder `content/posts/<short-slug>/`.
2. Add `index.md` with front matter:
   ```yaml
   ---
   title: "Article title"
   date: 2026-10-21
   summary: "One or two sentences for cards and link previews."
   tags: ["careers"]
   ---
   ```
3. Add a cover image named `feature.jpg` (or `.png`) to the same folder. It becomes the header image, the card thumbnail and the social-share preview. Other images in the folder can be used in the text with `![Alt text](image.jpg "Caption")`.
4. For a series part, add `series: ["Recruiterbot"]` and `series_order: 1` to the front matter (and the series to the Series menu in `menus.en.toml` the first time).
5. Commit and push to `main`. The site rebuilds in a minute or two.

### Scheduling an article

Give it a future date and time in Sydney time, e.g. `date: 2026-10-27T10:30:00+11:00` (`+10:00` outside daylight saving). Future-dated posts are skipped by the build, and the site rebuilds hourly, so the post appears within the hour after that time. Scheduled posts can be read in this public repo before they go live; Shanti is fine with that.

GitHub pauses scheduled workflows in a repo that has had no commits for 60 days. If that happens, re-enable "Deploy site" under the repo's Actions tab.

Keep images web-sized (ideally under ~500 KB each).

## Updating the theme

```shell
git submodule update --remote --merge
```

Then check `HUGO_VERSION` in `.github/workflows/hugo.yml` is within the range in `themes/blowfish/config.toml` (`[module.hugoVersion]`).

## Custom domain

The domain `shantikorporaal.com` is registered with Cloudflare (auto-renew on). DNS: four A records for `@` (185.199.108–111.153) and a `www` CNAME to `shantibk.github.io`, all **DNS only** (grey cloud) so GitHub can issue the HTTPS certificate. The custom domain is set under the repo's Settings → Pages.
