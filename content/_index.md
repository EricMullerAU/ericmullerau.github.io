---
# Leave the homepage title empty to use the site title
title: ""
date: 2024-07-09
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
        url: uploads/CV.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: NasaM83.jpg #stacked-peaks.svg
          filters:
            brightness: 0.3
          size: cover
          position: center
          parallax: false
  # - block: markdown
  #   content:
  #     title: 'My Research'
  #     subtitle: ''
  #     text: |-
  #       Use this area to speak to your mission. I'm a research scientist in the Moonshot team at DeepMind. I blog about machine learning, deep learning, and moonshots.

  #       I apply a range of qualitative and quantitative methods to comprehensively investigate the role of science and technology in the economy.
        
  #       Please reach out to collaborate 😃
  #   design:
  #     columns: '1'
  # - block: collection
  #   id: papers
  #   content:
  #     title: Featured Publications
  #     filters:
  #       folders:
  #         - publication
  #       featured_only: false
  #   design:
  #     view: article-grid
  #     columns: 2
  - block: collection
    content:
      title: Current Projects
      text: ""
      filters:
        folders:
          - current_projects
        featured_only: false
    design:
      view: article-grid
      columns: 3
      fill_image: true
      custom_css:
        - width: 100%  # Or specify a custom width like '90%' or '1200px'
        - max-width: 1200px  # Set the max-width for the block
  # - block: collection
  #   content:
  #     title: Publications
  #     text: ""
  #     filters:
  #       folders:
  #         - publications
  #       featured_only: true
  #   design:
  #     view: citation
  - block: markdown
    content:
      title: Recent Publications
      text: |
        <p style="text-align: left; font-size: large;"><b>2025</b></p>
        <ul style="list-style-position: inside; padding-left: 0; width: 1000px;">
          <li style="text-align: left;">Caroline Foster, Mark W. Donoghoe, Andrew Battisti, <b>et al.</b> The MAGPI Survey: the kinematic morphology-density relation (or lack thereof) and the Hubble sequence at z ∼ 0.3 <i>Publications of the Astronomical Society of Australia, accepted for publication, February 2025</i><br><a href="https://arxiv.org/abs/2502.16751">arxiv</a></li>
          <li style="text-align: left;">Marcie Mun, Emily Wisnioski, Katherine E. Harborne, <b>et al.</b> The MAGPI Survey: radial trends in star formation across different cosmological simulations in comparison with observations at z ∼ 0.3 <i>Monthly Notices of the Royal Astronomical Society, accepted for publication, February 2025</i><br><a href="https://arxiv.org/abs/2411.17882">arxiv</a> <a href="https://academic.oup.com/mnras/advance-article/doi/10.1093/mnras/staf342/8045600">MNRAS</a></li>
          <li style="text-align: left;">Hiep Nguyen, Haiyang Tang, Matthew Alger, Antoine Marchal, <b>Eric G. M. Muller</b>, Cheng Soon Ong, N. M. McClure-Griffiths. TPCNet: representation learning for HI mapping <i>Monthly Notices of the Royal Astronomical Society, Volume 536, Issue 1, January 2025, Pages 962-987</i><br><a href="http://arxiv.org/abs/2411.13325">arxiv</a> <a href=https://academic.oup.com/mnras/article/536/1/962/7908519">MNRAS</a></li>
        </ul>
  - block: resume-skills
    content:
      title: Skills
      username: admin
    design:
      show_skill_percentage: false
  - block: resume-awards
    content:
      title: Awards
      username: admin
  # - block: collection
  #   id: talks
  #   content:
  #     title: Recent & Upcoming Talks
  #     filters:
  #       folders:
  #         - event
  #   design:
  #     view: article-grid
  #     columns: 1
  # - block: collection
  #   id: news
  #   content:
  #     title: Recent News
  #     subtitle: ''
  #     text: ''
  #     # Page type to display. E.g. post, talk, publication...
  #     page_type: post
  #     # Choose how many pages you would like to display (0 = all pages)
  #     count: 5
  #     # Filter on criteria
  #     filters:
  #       author: ""
  #       category: ""
  #       tag: ""
  #       exclude_featured: false
  #       exclude_future: false
  #       exclude_past: false
  #       publication_type: ""
  #     # Choose how many pages you would like to offset by
  #     offset: 0
  #     # Page order: descending (desc) or ascending (asc) date.
  #     order: desc
  #   design:
  #     # Choose a layout view
  #     view: date-title-summary
  #     # Reduce spacing
  #     spacing:
  #       padding: [0, 0, 0, 0]
  # - block: cta-card
  #   demo: true # Only display this section in the Hugo Blox Builder demo site
  #   content:
  #     title: 👉 Build your own academic website like this
  #     text: |-
  #       This site is generated by Hugo Blox Builder - the FREE, Hugo-based open source website builder trusted by 250,000+ academics like you.

  #       <a class="github-button" href="https://github.com/HugoBlox/hugo-blox-builder" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star HugoBlox/hugo-blox-builder on GitHub">Star</a>

  #       Easily build anything with blocks - no-code required!
        
  #       From landing pages, second brains, and courses to academic resumés, conferences, and tech blogs.
  #     button:
  #       text: Get Started
  #       url: https://hugoblox.com/templates/
  #   design:
  #     card:
  #       # Card background color (CSS class)
  #       css_class: "bg-primary-700"
  #       css_style: ""
---
