---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: dark_blue_mountains.svg
          filters:
            brightness: 0.6
          size: cover
          position: center
          parallax: false
  - block: markdown
    content:
      title: 'My Research'
      subtitle: ''
      text: |-
        My research aims to bridge fundamental ecology and practical conservation. Many of the world’s most biodiverse regions are also changing the fastest. Even so, decisions about land use, development and protected areas are often made without basic knowledge of which species are present, where they occur and what they need to survive.

        I work across the conservation research continuum to help close these gaps:

        - **What to conserve:** documenting species diversity, taxonomy and evolutionary relationships
        - **What species need to persist:** studying their ecology, distributions, population dynamics and threats
        - **How best to conserve them:** evaluating conservation evidence, setting priorities and developing practical strategies

        Linking these three stages strengthens the scientific foundations of conservation and helps research lead to real outcomes on the ground.

        My long-term goal is to build a multidisciplinary team, and eventually a centre of excellence in applied conservation science. It would advance research where it’s most needed, train the next generation of conservation scientists and help conservation keep pace with development.
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: Publications
      text: ""
      count: 0
      filters:
        folders:
          - publication
        exclude_featured: false
      order: desc
    design:
      view: citation
  - block: collection
    id: talks
    content:
      title: Talks & Presentations
      count: 0
      filters:
        folders:
          - event
      order: desc
    design:
      view: date-title-summary
---
