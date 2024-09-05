---
title: 'Projects'
date: 2024-05-19
type: landing

design:
  # Section spacing
  spacing: '5rem'

# Page sections
sections:
  - block: collection
    content:
      title: Current Projects
      text: ""
      filters:
        folders:
          - current_projects
    design:
      view: article-grid
      fill_image: false
      columns: 3
  - block: collection
    content:
      title: Past Projects
      text: ""
      filters:
        folders:
          - past_projects
    design:
      view: article-grid
      fill_image: false
      columns: 3
---