---
title: 'Publications'
date: 2024-09-06
type: landing

# # View.
# view: citation

# # Optional header image (relative to `static/media/` folder).
# banner:
#   caption: ''
#   image: ''
# ---

design:
  # Section spacing
  spacing: '5rem'

# Page sections
sections:
#   - block: collection
#     content:
#       title: Publications
#       text: ""
#       filters:
#         folders:
#           - current_projects
#     design:
#       view: article-grid
#       fill_image: true
#       columns: 3
#   - block: collection
#     content:
#       title: Past Projects
#       text: ""
#       filters:
#         folders:
#           - past_projects
#     design:
#       view: article-grid
#       fill_image: true
#       columns: 3
  - block: collection
    content:
      title: Publications
      text: ""
      filters:
        folders:
          - publications
        featured_only: false
    design:
      view: citation
# Rather than using a citation view, instead use a basic markdown view with manually-added publication information.
  - block: markdown
    content:
      title: Publications
      text: "This page lists my publications. For a more detailed list, please see my [Google Scholar profile](https://scholar.google.com/citations?user=YOUR_ID)."
  - block: markdown
    content:
      title: Preprints
      text: "This page lists my preprints. For a more detailed list, please see my [Google Scholar profile](https://scholar.google.com/citations?user=YOUR_ID)."
  - block: collection
    content:
      title: Preprints
      text: ""
      filters:
        folders:
          - preprints
        featured_only: false
    design:
      view: citation
---