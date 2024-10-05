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
    - title: 동아리
      content: 동아리 활동에 대한 이야기
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
        text: 바로가기
        url: activity/#band
    - title: 해외 봉사
      content: 해외 교류 봉사 경험
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
        text: 바로가기
        url: activity/#viet
    - title: 자원 봉사
      content: 2023 전주 얼티밋 뮤직 페스티벌
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
        text: 바로가기
        url: activity/#jumf
---