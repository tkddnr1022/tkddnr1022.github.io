---
# Documentation: https://docs.hugoblox.com/managing-content/

title: "Class-Manager"
summary: "Location-based QR attendance service"
authors: [admin]
tags: ["FE", "BE"]
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
  - name: DevLog
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

Location-based QR attendance check application

### Usage stack

- React Native(expo)
- Nest.js
- MongoDB

### Rough design

1. Create a class, then set the class name, classroom, attendance time, location, etc.
2. Take a picture of the QR code in the classroom with a mobile app
3. Send the location of the photographer, device ID, academic records, etc. to the server
4. Check for duplicate location and device ID to prevent proxy attendance and fraudulent attendance
5. Save attendance information

### Proxy attendance

Implement only one attendance per device through device unique ID or application ID verification

### Fraudulent attendance

- **Static QR code (on hold)**

Placing a static QR code in the classroom has advantages in terms of cost and efficiency

However, there is also a vulnerability that attendance can be made anywhere within the GPS error range because the URL is exposed

As a solution, take a picture of the QR code without exposing the URL on the mobile app, and then use a verification method such as a secret key to directly access the mobile app from the classroom. Designed to allow attendance only when photographed

→ **Preventing QR code access through abnormal paths such as web browsers**

We wanted to make it lightweight so that it can be accessed through a web browser without the hassle of installing an app, but using a mobile app is inevitable to take advantage of static QR

<aside>

In fact, this method can be implemented with static values ​​such as classroom numbers even without QR codes, and there is no significant advantage in utilizing QR codes.

Therefore, it seemed desirable to implement it as a dynamic QR code by slightly restricting the attendance environment, and the design was modified to directly generate QR codes for classes.

</aside>

**Dynamic QR code generation**

Designed so that class participants can take a picture of a QR code that includes a unique identifier for the class on-site and proceed with attendance

It is still necessary to develop a mobile app because it is difficult to access the device ID from a browser.