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
      css_style: |
        @media (max-width: 600px) {
          body {
            font-size: small;
            max-width: 100%;
            color: red !important;
          }
        }
        @media (min-width: 601px) {
          body {
            font-size: medium;
            max-width: 1000px;
          }
        }
    content:
      title: Publications
      text: |
        <p style="text-align: left; font-size: large;"><b>2025</b></p>
        <ul style="list-style-position: inside; padding-left: 0; width: 1000px;">
          <li style="text-align: left;">Caroline Foster, Mark W. Donoghoe, Andrew Battisti, Francesco D'Eugenio, Katherine Harborne, Thomas Venville, Claudia Del P. Lagos, J. Trevor Mendel, Ryan Bagge, Stefania Barsanti, Sabine Bellstedt, Alina Boecker, Qianhui Chen, Caro Derkenne, Anna Ferre-Matteu, Eda Gjergo, Anshu Gupta, <b>Eric G. M. Muller</b>, Giulia Santucci, Hye-Jin Park, Rhea-Silvia Remus, Sabine Thater, Jesse van de Sande, Sam Vaughan, Sarah Brough, Scott M. Croom, Lucas M. Valenzuela, Emily Wisnioski, the MAGPI Team. The MAGPI Survey: the kinematic morphology-density relation (or lack thereof) and the Hubble sequence at z ∼ 0.3 <i>Publications of the Astronomical Society of Australia, accepted for publication, February 2025</i><br><a href="https://arxiv.org/abs/2502.16751">arxiv</a></li>
          <li style="text-align: left;">Marcie Mun, Emily Wisnioski, Katherine E. Harborne, Claudia D. P. Lagos, Lucas M. Valenzuela, Rhea-Silvia Remus, J. Trevor Mendel, Andrew J. Battisti, Sara L. Ellison, Caroline Foster, Matias Bravo, Sarah Brough, Scott M. Croom, Tianmu Gao, Kathryn Grasha, Anshu Gupta, Yifan Mai, Anilkumar Mailvaganam, <b>Eric G. M. Muller</b>, Gauri Sharma, Sarah M. Sweet, Edward N. Taylor, Tayyaba Zafar. The MAGPI Survey: radial trends in star formation across different cosmological simulations in comparison with observations at z ∼ 0.3 <i>Monthly Notices of the Royal Astronomical Society, accepted for publication, February 2025</i><br><a href="https://arxiv.org/abs/2411.17882">arxiv</a> <a href="https://academic.oup.com/mnras/advance-article/doi/10.1093/mnras/staf342/8045600">MNRAS</a></li>
          <li style="text-align: left;">Hiep Nguyen, Haiyang Tang, Matthew Alger, Antoine Marchal, <b>Eric G. M. Muller</b>, Cheng Soon Ong, N. M. McClure-Griffiths. TPCNet: representation learning for HI mapping <i>Monthly Notices of the Royal Astronomical Society, Volume 536, Issue 1, January 2025, Pages 962-987</i><br><a href="http://arxiv.org/abs/2411.13325">arxiv</a> <a href=https://academic.oup.com/mnras/article/536/1/962/7908519">MNRAS</a></li>
        </ul>

        <p style="text-align: left; font-size: large;"><b>2024</b></p>
        <ul style="list-style-position: inside; padding-left: 0; width: 1000px;">
          <li style="text-align: left;">Giulia Santucci, Claudia Del P Lagos, Katherine E Harborne, Caro Derkenne, Adriano Poci, Sabine Thater, Richard McDermid, J Trevor Mendel, Emily Wisnioski, Scott M Croom, Anna Ferré-Mateu <b>Eric G. M. Muller</b>, Jesse van de Sande, Gauri Sharma, Sarah M Sweet, Takafumi Tsukui, Lucas M Valenzuela, Glenn van de Ven, Tayyaba Zafar. The MAGPI survey: orbital distributions, intrinsic shapes, and mass profiles for MAGPI-like EAGLE galaxies using Schwarzschild dynamical models <i>Monthly Notices of the Royal Astronomical Society, Volume 534, Issue 1, October 2024, Pages 502-522</i><br><a href="https://arxiv.org/abs/2409.05940">arxiv</a> <a href="https://academic.oup.com/mnras/article/534/1/502/7754825">MNRAS</a></li>
  
---