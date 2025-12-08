# ThePointsPup 🐾

A pet travel blog about using credit card points for free hotel stays while traveling with dogs.

**Live site:** [https://thepointspup.com](https://thepointspup.com)

## About

ThePointsPup helps dog owners travel more by leveraging credit card rewards for free hotel stays. The site focuses on Hilton properties (which have no pet weight limits at most locations) and practical tips for road tripping with large dogs.

## Tech Stack

- **Static Site Generator:** [Hugo](https://gohugo.io/) (v0.128.0+)
- **Theme:** [Stack](https://github.com/CaiJimmy/hugo-theme-stack)
- **Hosting:** GitHub Pages
- **Domain:** Porkbun
- **Analytics:** Google Analytics 4

## Local Development
```bash
# Clone the repo
git clone https://github.com/thepointspupblog/thepointspup.git
cd thepointspup

# Start the dev server
hugo server -D

# View at http://localhost:1313
```

## Deployment

The site automatically deploys to GitHub Pages via GitHub Actions when changes are pushed to the `main` branch.

The workflow is defined in `.github/workflows/hugo.yml`.

## Project Structure
```
thepointspup/
├── content/
│   ├── posts/           # Blog posts
│   ├── _index.md        # Homepage
│   ├── about.md
│   ├── contact.md
│   ├── disclosure.md
│   └── privacy.md
├── layouts/
│   ├── partials/        # Custom overrides
│   └── shortcodes/      # Custom shortcodes
├── static/              # Images, favicon, CNAME
├── themes/
│   └── hugo-theme-stack/
└── hugo.toml            # Site configuration
```

## Content Categories

- **Guides** - How-to articles for pet travel
- **Credit Cards** - Reviews and comparisons for earning points
- **Trip Reports** - Real experiences from road trips with Ansel

## Author

**Dani** - Based in Jacksonville, FL, traveling with Ansel, a 70-lb German Shorthaired Pointer/Lab mix.

## License

Content © 2024-2025 ThePointsPup. All rights reserved.