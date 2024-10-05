---
# Documentation: https://docs.hugoblox.com/managing-content/

title: "Class-Manager"
summary: "위치 기반 QR 출석 서비스"
authors: [admin]
tags: ["Frontend", "Backend"]
categories: []
date: 2024-09-01

# Optional external URL for project (replaces project detail page).
external_link:

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
  - name: GitHub
    url: https://github.com/tkddnr1022/Class-Manager
    icon_pack: fab
    icon: github
  - name: 개발일지
    url: https://powerful-aries-478.notion.site/8f9462fd3f6641c2b224bc0a5b3a12de?pvs=74
    icon_pack: fas
    icon: book

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

# Class Manager

위치 기반 QR 출석 체크 애플리케이션

### 사용 스택

- React Native(expo)
- Nest.js
- MongoDB

### 대략적인 설계

1. 수업 생성 후 수업명, 강의실, 출석시간, 위치 등 설정
2. 모바일 앱으로 강의실 내 QR코드 촬영
3. 촬영자의 위치, 디바이스 ID, 학적 등 정보를 서버에 전달
4. 대리 출석, 부정 출석을 방지하기 위해 올바른 위치와 디바이스 ID 중복여부 확인
5. 출석 정보 저장

### 대리 출석

디바이스 고유 ID 혹은 애플리케이션 ID 검증을 통해 하나의 기기에서 1회 출석만 가능하도록 구현

### 부정 출석

- **정적 QR 코드(보류)**
    
    강의실 내에 정적인 QR코드를 배치하는 방법은 비용과 효율 면에서 이점이 있음
    
    그러나 URL이 노출되어있기 때문에 GPS 오차 범위 내에서 어디서든 출석이 가능하다는 취약점 또한 존재함
    
    해결책으로, 모바일 앱에서 URL 노출 없이 QR코드 촬영 후 시크릿 키와 같은 검증 방법을 통해 강의실에서 모바일 앱으로 직접 촬영한 경우만 출석이 가능하도록 설계
    
    → **웹 브라우저 등 비정상적 경로를 통한 QR코드 접속 방지**
    
    앱 설치의 번거로움 없이 웹 브라우저로 접근할 수 있도록 경량화하고자 하였으나, 정적 QR의 이점을 위해서는 모바일 앱 사용이 불가피함
    
    <aside>
    
    사실 이러한 방법은 QR코드가 아니어도 강의실 번호와 같은 정적 값으로 구현할 수 있고, QR코드 활용에 큰 이점이 없다.
    
    따라서 출석 환경을 조금 제한하여 동적 QR코드로 구현하는 것이 바람직해 보였고, 수업에 대한 QR코드를 직접 생성하는 방법으로 설계를 수정하였다.
    
    </aside>
    

**동적 QR 코드 생성**

현장에서 수업에 대한 고유 식별자를 포함한 QR코드를 생성하면 수업 참여자가 이를 촬영하여 출석을 진행할 수 있도록 설계

브라우저에서 디바이스 ID에 접근하기는 어렵기 때문에 여전히 모바일 앱 개발이 필요함