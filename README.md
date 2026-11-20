# Meta Attribution Fix GTM Variable Template by [Backona](https://backona.com)

Google Tag Manager variable template that returns a fallback campaign source or campaign medium when a landing URL has `fbclid` and no `utm_source` or `utm_medium`. Built by [Backona](https://backona.com).

Untagged Meta clicks often arrive with `fbclid` and a stripped referrer, so GA4 records them as Direct. This variable fills campaign source and medium on that landing hit only. When either UTM is already present, it returns undefined so tagged campaigns stay as they were.

Release history: [CHANGELOG.md](./CHANGELOG.md).

> **Not in the Community Template Gallery yet.** Until it is listed, install by importing [`template.tpl`](./template.tpl) from this repository (see below). Do not rely on searching the [Community Template Gallery](https://tagmanager.google.com/gallery) for now.

## Install

**Preferred method: import [`template.tpl`](./template.tpl)**

1. In Google Tag Manager, go to **Templates** → **Variable Templates** → **New**.
2. Open the menu (⋮) → **Import** → select [`template.tpl`](./template.tpl) from this repository → **Save**.
3. Create a variable from **Meta Attribution Fix variable by Backona**.
   - **Output Mode:** Campaign Source
   - **Source Value:** `facebook` (or your own source)
4. Create a second variable from the same template.
   - **Output Mode:** Campaign Medium
   - **Medium Value:** `organic` (or your own medium)
5. On the GA4 Google tag, open **Fields to set** and add:
   - `campaign_source` → the source variable
   - `campaign_medium` → the medium variable

The variable reads only the current page URL. It does not store the fallback for later pages in the session, so it applies to the landing hit that still has `fbclid`.

| URL | Source variable | Medium variable |
|-----|-----------------|-----------------|
| `?fbclid=…` and no UTMs | `facebook` | `organic` |
| `?fbclid=…&utm_source=…` or `utm_medium=…` | undefined | undefined |
| no `fbclid` | undefined | undefined |

Undefined leaves that GA4 field unset, so an existing UTM campaign is not overwritten. Both `utm_source` and `utm_medium` must be absent before a fallback is returned. If only one of them is present, both variables return undefined.

If **Source Value** is cleared, the template uses `facebook`. If **Medium Value** is cleared, the template uses `organic`.

**Later (after Google approval):** you will also be able to add the template from the [Community Template Gallery](https://tagmanager.google.com/gallery). Until then, use the `template.tpl` import above.

## Consent

This variable only reads query parameters. Set consent on the GA4 tag that uses it. For [Consent Mode v2](https://support.google.com/tagmanager/answer/10718549), consider:

- `analytics_storage`
- `ad_storage`

For consent banners and defaults, see [Backona Cookie Consent Management](https://backona.com/product/cookie-consent-management).

## Support

Report bugs or request features via [GitHub Issues](https://github.com/backona/gtm-meta-attribution-fix-variable/issues) on this repository.
