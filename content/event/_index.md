---
title: Recent & Upcoming Talks
cms_exclude: true

# Don't generate a separate page for each talk (or this list page).
# Talks are shown only in the Talks & Presentations section of /about/.
_build:
  render: never
cascade:
  - _target:
      kind: page
      path: '/event/**'
    _build:
      render: never

# View
view: card

# Optional cover image (relative to `assets/media/` folder).
image:
  caption: ''
  filename: ''
---
