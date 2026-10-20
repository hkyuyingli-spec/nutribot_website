# NutriBot Website — InfinityFree Deployment

## What's included
- `index.html` — Home page, with the NutriBot AI chatbot embedded (live iframe to your Streamlit app)
- `about.html`, `services.html`, `faq.html`, `blog.html`, `contact.html`, `privacy.html`, `pricing_1.html`, `x5-pro.html`
- `assets/style.css`, `assets/script.js` — site styling and mobile menu
- `send-message.php` — handles the contact form (works on InfinityFree's PHP hosting)

## Chatbot embed
The chatbot is embedded via iframe pointing to:
`https://dennis-the-robot-bf5y8vwm4a6nb7jfymyh9x.streamlit.app/`

Notes:
- Free Streamlit apps "sleep" after inactivity. The first visitor each day may see a 10–30 second loading spinner inside the iframe while it wakes up — this is normal.
- A fallback "Open NutriBot in a new tab" link is included on the home page in case the iframe is blocked by the visitor's browser.
- If you ever change the chatbot's URL, update the `src` attribute of the `<iframe>` in `index.html` (search for `chatbot-frame`).

## How to upload to InfinityFree

1. Sign up / log in at infinityfree.net and create a hosting account + domain (or use a free subdomain).
2. Open the **File Manager** (or use an FTP client like FileZilla with the credentials InfinityFree gives you).
3. Navigate to the `htdocs` folder — this is your site's root.
4. Delete the default `index.html` / placeholder files InfinityFree puts there.
5. Upload everything from this package into `htdocs`, keeping the `assets` folder structure intact:
   ```
   htdocs/
     index.html
     about.html
     services.html
     faq.html
     blog.html
     contact.html
     privacy.html
     pricing_1.html
     x5-pro.html
     send-message.php
     assets/
       style.css
       script.js
   ```
6. Visit your domain — the site should load immediately (InfinityFree serves static HTML/PHP with no build step needed).

## Before going live
- Edit `send-message.php` and set `$to_email` to the real inbox you want contact form messages sent to.
- Update the email address shown on `contact.html` (currently `hello@ainutribot.com`) if needed.
- Optional: replace the placeholder colored blog thumbnails (`.news-thumb`) with real images by adding image files to `assets/` and updating the `<div class="news-thumb">` elements to `<img>` tags.

## Notes on email sending
InfinityFree's free tier has limits on outgoing mail via PHP `mail()` and may flag messages as spam or block sending entirely depending on the plan. If the contact form doesn't deliver emails, consider using a free form service like Formspree or Web3Forms and pointing the form's `action` to that instead.
