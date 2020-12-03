# Nuxt Supercharged Boilerplate

> nuxt pwa twa netlify identity and netlifycms

Features: 
- Nuxt.js
- Progressive Web App (PWA)
- Trusted Web Application (TWA) 
- Authentication with Netlify Identity
- Content Management System(CMS) with NetlifyCms
- Flat-file site settings (editable through NetlifyCms)

----
steps taken to create:
- [x] create-nuxt-app
- [x] install netlifycms
  - [x] create static/admin.html
  - [x] create static/config.yml
  - [x] run netlify cms locally ```npx netlify-cms-proxy-server```
- [x] create site data via local cms
- [x] put siteData in runtimeConfig
- [x] add @nuxt/ngrok
- [x] implement dynamic head
- [ ] create git repository
- [ ] add remote
- [ ] push to github
- [ ] create netlify.toml, and add deploy to netlify in README.md
- [ ] deploy to netlify from github
- [ ] enable netlify identity
- [ ] invite self
- [ ] install post-css
- [ ] add sitemap
- [ ] add feed feed.json and rss.xml
- [ ] add robots.txt


env
 - baseUrl - deploy domain
 - NGROK_AUTHTOKEN - for ngrok usage

Nuxt Content / NetlifyCms Collections
- site data (json)
  - url ✔️
  - name ✔️
  - description
  - keywords
  - language
  - summary
  - networks
    - name
    - url
    - icon
    - handle
  - favicon
  - tags
- pages
- articles
- blog
- photos
