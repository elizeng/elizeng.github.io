# elizeng.github.io

Source for [elizeng.github.io](https://elizeng.github.io), the academic website of Elize Ng, conservation biologist and Postdoctoral Research Fellow at the University of Queensland.

Built with [Hugo](https://gohugo.io) and the [Hugo Blox](https://hugoblox.com) Academic CV template. Pushing to `main` builds the site and deploys it to GitHub Pages (`.github/workflows/publish.yaml`).

## Where to edit

- Profile, bio, experience, skills, awards: `content/authors/admin/_index.md`
- Homepage sections: `content/_index.md`
- Publications: `content/publication/<slug>/index.md` (or add a `publications.bib` at the root to import via a pull request)
- Talks: `content/event/<slug>/index.md`
- Research projects: `content/project/<slug>/index.md`
- About page (service, teaching, section order): `content/about.md`
- Menu, theme and footer: `config/_default/`

## Preview locally

Install Hugo **extended** 0.136.5 and Go, then run `hugo server` and open http://localhost:1313.

See `CLAUDE.md` for content conventions.
