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
  # - block: collection
  #   content:
  #     title: Publications
  #     text: ""
  #     filters:
  #       folders:
  #         - publications
  #       featured_only: false
  #   design:
  #     view: citation
# Rather than using a citation view, instead use a basic markdown view with manually-added publication information.
  - block: markdown
    design:
      columns: '1'
      text: |
        <style>
          @media (max-width: 600px) {
            .publication-list {
              font-size: small;
              max-width: 100%;
              color: blue;
            }
          }
          @media (min-width: 601px) {
            .publication-list {
              font-size: medium;
              max-width: 1000px;
            }
          }
        </style>
        <p style="text-align: left;"><b style="font-size: large;">2024</b></p>
        <ul class="publication-list" style="list-style-position: inside; padding-left: 0; width: 1000px;">
          <li style="font-size: medium; text-align: left;">Hiep Nguyen, Haiyang Tang, Matthew Alger, Antoine Marchal, <b>Eric G. M. Muller</b>, Cheng Soon Ong, N. M. McClure-Griffiths. TPCNet: Representation learning for HI mapping <i>Monthly Notices of the Royal Astronomical Society, Volume XX, Issue X, November 2024, Pages XXX</i><br><a href="http://arxiv.org/abs/2411.13325">arxiv</a> <a href="https://doi.org/10.48550/arXiv.2411.13325">DOI</a></li>
        </ul>
    content:
      title: Publications
      text: |
        <p style="text-align: left;"><b style="font-size: large;">2024</b></p>
        <ul class="publication-list" style="list-style-position: inside; padding-left: 0; width: 1000px;">
          <li style="font-size: medium; text-align: left;">Hiep Nguyen, Haiyang Tang, Matthew Alger, Antoine Marchal, <b>Eric G. M. Muller</b>, Cheng Soon Ong, N. M. McClure-Griffiths. TPCNet: Representation learning for HI mapping <i>Monthly Notices of the Royal Astronomical Society, Volume XX, Issue X, November 2024, Pages XXX</i><br><a href="http://arxiv.org/abs/2411.13325">arxiv</a> <a href="https://doi.org/10.48550/arXiv.2411.13325">DOI</a></li>
        </ul>
  
---