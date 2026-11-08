# KraftInk Market

The public catalogue of KraftInk plugins, themes, and game modules. Listings and versions come from GitHub releases in registered repositories.

Listing names, descriptions, and optional images come from `manifest.market`. Plain text stays a string, and translated fields keep the languages supplied by the extension. To include an image from `resources/market/`, reference its filename or relative path in the manifest. The catalogue resolves it to a GitHub URL for the release tag. Image fields contain an HTTPS URL or a map of URLs by language. The KraftInk website and CMS use these listings directly. When a translation is missing, they fall back to English, then to the first available language.

Maintain `resources.json` on `dev`. The `repositories` array contains entries in this format.

```json
{ "repository": "Kraftink-CMS/Plugin-Example", "auto_update": true }
```

`auto_update` controls automatic updates for the listing. Set it to `false` to pause automatic updates while keeping the listing and its published versions. The `resources` array contains manually maintained listings.

The CMS and the KraftInk website use the [public JSON catalogue](https://raw.githubusercontent.com/Kraftink-CMS/Market/master/catalogue.json) published on `master`.

The central [Refresh Market workflow](https://github.com/Kraftink-CMS/automation/actions/workflows/refresh-market.yml) runs on `master`. Choose a scope when starting it manually.

| Scope        | Repositories refreshed                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------- |
| `automatic`  | Repositories with `auto_update: true`                                                             |
| `repository` | The registered repository entered in the `repository` field, even if automatic updates are paused |
| `all`        | All registered repositories, including those with automatic updates paused                        |

The `repository` and `all` scopes leave `auto_update` as configured.
