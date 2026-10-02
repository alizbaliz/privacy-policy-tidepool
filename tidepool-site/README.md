# Tidepool website

A static site for the game: home page, support and FAQ, privacy policy, and `app-ads.txt`. There is no
build step, no JavaScript, no cookies and no trackers, so it can be hosted anywhere as-is.

| File | Used for |
|---|---|
| `index.html` | Play Console › Store settings › **Website** (also required for app-ads.txt) |
| `privacy.html` | Play Console › App content › **Privacy policy**, and `privacyPolicyUrl` in the game's `store.properties` (Settings links to it) |
| `support.html` | Contact and FAQ: purchases, subscriptions, consent, data deletion |
| `app-ads.txt` | AdMob ad seller verification. Must be at the **root** of the domain |
| `404.html`, `.nojekyll` | Not-found page; `.nojekyll` makes GitHub Pages serve the files untouched |

## Before publishing

1. Replace every highlighted placeholder (search for `[YOUR`, `[STREET`, `[POSTCODE` and `[HOSTING`)
   in `index.html`, `support.html` and `privacy.html`. GDPR requires a real name, postal address and
   email for the controller.
2. In `app-ads.txt`, replace `pub-XXXXXXXXXXXXXXXX` with your AdMob publisher ID.
3. When the game is live, switch the "Coming soon" badge in `index.html` to the Google Play link (it's in a comment).

## Hosting (free options)

- **Netlify Drop**: drag this folder onto <https://app.netlify.com/drop>. You get an `https://….netlify.app` address straight away.
- **Cloudflare Pages**: create a project › Upload assets › select this folder.
- **GitHub Pages**: push this folder to a repository, then Settings › Pages › deploy from the main branch.

`app-ads.txt` only works at the root of a domain (`https://example.com/app-ads.txt`), not in a sub-folder.
A GitHub Pages project URL (`user.github.io/repo/`) is therefore not enough for it; use a Netlify or
Cloudflare address, or your own domain.

## After it's online

- Put the privacy URL into the game's `store.properties` (`privacyPolicyUrl=https://…/privacy.html`)
  and into the Play Console.
- Enter the home page URL as the developer website in Play Console › Store settings, then AdMob
  verifies `app-ads.txt` within about a day.
- Whenever the game adds an SDK or changes what data it uses, update `privacy.html` and its effective date first.
