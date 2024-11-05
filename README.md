# clinicadentalmiralva.com

[![clinicadentalmiralva.com](/assets/media/base/icon.png)](https://clinicadentalmiralva.com/)


## STEPS


### Local

- Design
  - You can edit any file with the same structure of theme sansoul
  - GENERAL
    - `config.yml`
    - `data/*.{yml,md}`
  - FONTS
    - Fonts that not be in Google Fonts:
      - .otf/.ttf files in `assets/fonts` + rename
      - You need the `sansoul_tools` project in `../_tools` folder
      - Run `do fonts` comand
      - `Family` + `Style` + `Weight` must match in `config.yml ⏩ params.fonts` + `_fonts.scss` (and disable `params.fonts.google` if appropriate)
  - CONTENT
    - `content/*`
      - `blog/divisores.md` ⏩ remove
      - `admin` ⏩ `draft: true` and/or change params and content
      - SCRAP
        - Copy [this Spreadsheet Layout](https://docs.google.com/spreadsheets/d/1bJQaAFoBAwHhWz_WFRIHlkHoDmZZyT8H8NtdCnSTdaU)
        - First scrap with Screaming Frog and paste `url` and `title`
        - Second scrap with `IMPORTXML` formula in `content-start` tab
        - If need HTML content
          - Three scrap with `Web Scraper` chrome extension and paste in `content-scrap` tab
          - Copy `content-start` tab into `content-next` and get `body_code` (by `content-scrap`) with `VLOOKUP` formula
          - Copy `body_code` column to `body`, replace double quotes, [convert to Markdown](https://smalldev.tools/html-to-markdown-converter-online) and clean it
          - Paste in `file.md` in `./Downloads` and run `_tools/md-replaces.command`
          - Check `file_new.md` content:
            - headers: `^#`
            - images: `!\[.+?\)`
            - links: `(^|[^!])\[.+?\)`
            - internal links: `https?://(www\.)?example\.com`
          - Paste in sheet
        - Export to CSV like `./Downloads/file.csv` and run `_tools/csv-to-md.command`
        - Move files from `markdown_files` to `blog` project
  - HTML
    - `layouts/*`
    - `data/config.yml ⏩ custom_code.html_head.code`
    - `data/config.yml ⏩ custom_code.html_body.code`
  - CSS
    - `assets/css/*`
    - `assets/css/` ⏩ `_variables-custom.scss` + `_custom.scss`
    - `data/config.yml ⏩ custom_code.css.code`
  - JS
    - `assets/js/*`
    - `layouts/partials/sections/common/scripts.html`
    - `data/config.yml ⏩ custom_code.js.code`
  - IMG
    - `assets/media/*`
  - REDIRECTS
    - `assets/redirects.md`
  - ROBOTS
    - `assets/robots.md`
  - If Multilanguaje and Multihosting, add `cp ./public/[es|en]/404.html ./public/` in `netlify.toml ⏩ build.command`
  - Try in Safari and Firefox
  - Check in [W3 Validator](https://validator.w3.org/)
  - Check in [PageSpeed Insights](https://pagespeed.web.dev/)


### After client validate web


#### Domain

- If Netlify
  - [`Domain Management / settings`](https://app.netlify.com/sites/clinicadentalmiralva/settings/domain)
  - `Add custom domain`
  - `Check DNS configuration` Copy
  - Add `DNS Records` copied from Netlify to Domain gestor:
    - From: `clinicadentalmiralva.com`
      DNS Record: `ALIAS`, `ANAME` or `flattened CNAME`
      To: `apex-loadbalancer.netlify.com`
    - From: `clinicadentalmiralva.com`
      DNS Record: `A`
      To: `75.2.60.5`
    - From: `www`
      DNS Record: `CNAME`
      To: `clinicadentalmiralva.netlify.app.`
    - Maybe you need to eliminate the previous records with similar names
  - `Verify DNS configuration`
  - If it does not work after a while, try `Set as main domain` in the `www` version and also in te `nowww` version


#### [Google Analytics](https://analytics.google.com/)

- `Admin ⏩ Libre acount ⏩ New property ⏩ ...` copy ID
- `data/config.yml ⏩ google_analytics` ⏩ paste ID
- `Ajustes de datos`
  - `Recogida de datos`
    - `Recogida de datos de Google signals ⏩ Empezar`
    - `Consentimiento de recogida de datos de usuario` ⏩ Check
  - `Conservación de datos ⏩ Conservación de datos de eventos ⏩ 14 meses ⏩ Guardar`
- `Conversiones ⏩ Nuevo evento de conversión ⏩ Nombre de evento nuevo` ⏩ add `contact_click` and `contact_form_submit`


#### [Google Search Console](https://search.google.com/search-console)

- Add property
- Verify versions ⏩ `data/config.yml`
  - `google_analytics`
  - `google_site_verification`
  - `google_file_verification`
  - DNS:
    From: `@`
    DNS Record: `TXT`
    To: `google-site-verification=[google_site_verification]`
- Link with Analytics
- Add sitemap.xml


##### Delivery

Send to all collaborators next:

###### WhatsApp

```md
*ENTREGA WEB clinicadentalmiralva.com*

Te dejo aquí este mensaje como referencia (también te lo paso por email con el asunto `ENTREGA WEB clinicadentalmiralva.com`).

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```

###### Mail

```
Asunto: ENTREGA WEB clinicadentalmiralva.com
Cuerpo:
Te dejo aquí este email como referencia.

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```
