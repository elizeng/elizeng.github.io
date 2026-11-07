---
title: Publications
cms_exclude: true

# Don't generate a separate page for each paper (or this list page).
# Papers are shown on /publications/ and as homepage cards only.
_build:
  render: never
cascade:
  - _target:
      kind: page
      path: '/publication/**'
    _build:
      render: never

# View.
view: citation

# Optional header image (relative to `static/media/` folder).
banner:
  caption: ''
  image: ''
---
