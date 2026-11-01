# ios-shells

Thin Capacitor shells for Salal's PWAs. Each shell loads the live site over HTTPS, so web changes ship through the normal Cloudflare deploy and never need a rebuild here.

| Folder | App | Loads | Bundle ID |
|---|---|---|---|
| `stylist/` | Stylist | https://stylist-4g4.pages.dev | me.salal.stylist |
| `tasks/` | Tasks (later) | https://salal.me | me.salal.tasks |

## Build

`codemagic.yaml` builds an unsigned IPA on every push to `main`. Download `Stylist.ipa` from the Codemagic build artifacts and sideload it with AltStore (free Apple ID) or install it through TestFlight once a paid developer account exists.

## Rebuild when

- the icon, splash, name or bundle ID changes
- a Capacitor plugin is added
- the URL changes
- a new iOS major needs a newer Capacitor

Nothing else. The site is the app.

## Local notes

- `stylist/www/index.html` is a placeholder. It is only shown if the shell cannot reach the site.
- `WKAppBoundDomains` in `stylist/ios/App/App/Info.plist` must list the site domain or service workers will not run inside the shell.
- Placeholder icon and splash live in `stylist/assets/`. Replace `icon.png` (1024x1024) and `splash.png` (2732x2732), then run `npx capacitor-assets generate --ios` inside `stylist/`.
