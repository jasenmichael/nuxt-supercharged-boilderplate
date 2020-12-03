# Nuxt Supercharged Boilerplate

> nuxt pwa twa netlify identity and netlifycms

Features: 
- Nuxt.js
- Progressive Web App (PWA)
- Trusted Web Application (TWA) 
- Authentication with Netlify Identity
- Content Management System(CMS) with NetlifyCms
- Flat-file site settings (editable through NetlifyCms)

## 💫 Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/jasenmichael/nuxt-supercharged-boilderplate)

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
- [x] create git repository
- [x] add remote
- [x] push to github
- [x] create netlify.toml, and add deploy to netlify in README.md
- [x] deploy to netlify from github
- [x] check seo tags on..
  ```note: twiter validator and fb debugger cache your site, so changes in your header will not reflect immediatly when you re-run, use metatags first, and to work around twitter and fb cache of site - use a dev branch or change subdomain in netlify, as you will have a new url ;)```
  - [x] [metatags.io](https://metatags.io/) 
  - [x] [Twitter validator](https://cards-dev.twitter.com/validator)
  - [x] [Facebook Debugger](https://developers.facebook.com/tools/debug/)
- [ ] setup and config Netlify identity
  - [x] enable netlify identity
  - [ ] invite self
  todo:
- [ ] install post-css
- [ ] add sitemap
- [ ] add feed feed.json and rss.xml
- [ ] add robots.txt

env
 - NGROK_AUTHTOKEN - for ngrok usage in dev

Nuxt Content / NetlifyCms Collections
- site data (json)
  - name ✔️
  - description
  - language
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
