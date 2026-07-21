# yash-personal-website

Personal website of Yash Thakkar, built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme.

## Structure

| Path | What lives there |
| --- | --- |
| `_config.yml` | Site-wide settings: name, email, socials, URL, feature toggles |
| `_pages/about.md` | Landing page bio |
| `_data/cv.yml` | Everything on the `/cv/` page |
| `_projects/` | One file per project card (`category:` puts it in a section) |
| `_bibliography/papers.bib` | Publications; `selected={true}` surfaces it on the homepage |
| `_news/` | Short dated announcements shown on the homepage |
| `_data/repositories.yml` | Which GitHub repos appear on `/repositories/` |
| `assets/img/prof_pic.jpg` | Profile photo |
| `assets/resume/` | LaTeX source for the resume |

## Running it locally

The theme needs **Ruby 3.x**; macOS ships 2.6, which is too old. Install a newer Ruby first:

```bash
# Homebrew (if you don't have it: https://brew.sh)
brew install ruby imagemagick
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
exec zsh
```

Then:

```bash
bundle install
bundle exec jekyll serve
```

The site is at <http://localhost:4000>. It rebuilds on save.

Alternatively, with Docker (no Ruby install needed):

```bash
docker compose up
```

## Deploying to GitHub Pages

1. Create a repo named `YashThakkar21.github.io` (a user site — it publishes at the root, which is what `_config.yml` assumes: `url: https://yashthakkar21.github.io`, empty `baseurl`).
2. Push this directory to it. `.github/workflows/deploy.yml` builds the site on every push to `main` and pushes the output to a `gh-pages` branch.
3. After the first workflow run finishes, go to **Settings → Pages** and set the source to **Deploy from a branch → `gh-pages` / `(root)`**.

For a custom domain, add a `CNAME` file at the repo root containing the domain, and point a DNS `A`/`CNAME` record at GitHub Pages.

## Things to update later

- **Profile photo** — `assets/img/prof_pic.jpg` is currently the GitHub avatar. Drop in a real photo at the same path to swap it.
- **Resume PDF** — build `assets/resume/yash_thakkar_resume.tex`, put the PDF in `assets/pdf/`, then add `cv_pdf: <filename>.pdf` back to the front matter of `_pages/cv.md` to get a download button on the CV page.
- **Project images** — project cards render without images right now. Add `img: assets/img/<file>` to a project's front matter to give it a thumbnail.
- **Blog** — `_pages/blog.md` exists with `nav: false` since there are no posts yet. Add files to `_posts/` and flip it to `nav: true`.
- **Google Scholar** — once there's a profile, set `scholar_userid` in `_config.yml` to get the icon and citation badges.
