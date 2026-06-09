# NearHealth Widgetbook

Static web build of the Flutter Widgetbook for the NearHealth app.

Public GitHub Pages URL:

```text
https://nearhealth.github.io/widgetbook/
```

The source of truth is the `flutter_app` package in the `main_app` repo:

```text
/Users/davecaos/repos/flutter-examples/main_app/flutter_app
```

## Publish

From the `main_app` repo root:

```bash
./scripts/deploy_widgetbook_ghpages.sh
```

The deploy script builds the Widgetbook static bundle with
`BASE_HREF=/widgetbook/`, syncs `flutter_app/build/web/` into this repo,
strips bundled `assets/.env*` files, adds `.nojekyll`, commits, and pushes
`main`.

## GitHub Pages Status

As of June 9, 2026, this repo is public so GitHub Pages can build and serve the
generated static assets on the standard project-site path.

## Maintenance Notes

- Do not hand-edit generated Flutter web assets in this repo. Make source
  changes in `main_app/flutter_app`, then redeploy.
- `README.md` is intentionally preserved by the deploy script and is the only
  hand-maintained file here.
- `.env*` files are removed before publish so local or staging configuration is
  not served as plaintext.
- After redeploying, browsers can briefly show cached content because Flutter
  ships a service worker. Use a hard reload if the live page looks stale.

## Pages URL Lookup

```bash
gh api repos/NearHealth/widgetbook/pages --jq '.html_url'
```
