---
widget: slider  # Use the Slider widget as this page section
weight: 50  # Position of this section on the page
active: true  # Publish this section?
headless: true  # This file represents a page section.

design:
  # Slide height is automatic unless you force a specific height (e.g. '400px')
  slide_height: '500px'
  is_fullscreen: false
  # Automatically transition through slides?
  loop: true
  # Duration of transition between slides (in ms)
  interval: 5000

content:
  slides:
    - title: Club
      content: Talk about club activities
      align: center
      background:
        position: bottom
        color: '#666'
        brightness: 0.7
        media: images/band-musician.jpg
        fit: cover
      link:
        icon: arrow-right
        icon_pack: fas
        text: Go
        url: activity/#band
    - title: Overseas volunteer work
      content: Overseas exchange volunteer experience
      align: right
      background:
        position: top
        color: '#555'
        brightness: 0.5
        media: images/viet-school.jpg
        fit: cover
      link:
        icon: arrow-right
        icon_pack: fas
        text: Go
        url: activity/#viet
    - title: Volunteer
      content: 2023 Jeonju Ultimate Music Festival
      align: right
      background:
        position: center
        color: '#333'
        brightness: 0.7
        media: images/jumf.jpg
        fit: cover
      link:
        icon: arrow-right
        icon_pack: fas
        text: Go
        url: activity/#jumf
---