[中文](https://github.com/siyuan-note/icon-sample/blob/main/README.zh-CN.md)

# SiYuan icon sample

## Get started

* Make a copy of this repo as a template with the <kbd>Use this template</kbd> button, please note that the repo name
  must be the same as the icon name, the default branch must be `main`
* Clone your repo to a local development folder. For convenience, you can place this folder in your `{workspace}/data/icons/` folder

Icon files sync with the workspace; each device chooses its own icons. Development changes in this folder also sync, so keep local-only work outside the workspace or add the development folder to the sync ignore rules.

## Development

* icon.json
* icon.png (optional default icon, 160*160)
* preview.png (optional default preview, 1024*768)
* README*.md
* icon.js

## icon.json

```json
{
  "name": "icon-sample",
  "author": "Vanessa",
  "url": "https://github.com/siyuan-note/icon-sample",
  "version": "0.0.4",
  "minAppVersion": "3.7.0",
  "displayName": {
    "default": "Icon Sample",
    "zh-CN": "图标示例"
  },
  "description": {
    "default": "This is an icon sample",
    "zh-CN": "这是一个图标示例"
  },
  "readme": {
    "default": "README.md",
    "zh-CN": "README.zh-CN.md"
  },
  "icon": "icon.png",
  "preview": "preview.png",
  "funding": {
    "openCollective": "",
    "patreon": "",
    "github": "",
    "custom": [
      "https://ld246.com/sponsor"
    ]
  },
  "keywords": [
    "sample", "示例"
  ]
}
```

* `name`: Icon name, must be the same as the repo name, and must be unique globally (no duplicate icon names in the
  marketplace)
* `author`: Icon author name
* `url`: Icon repo URL
* `version`: Icon version number, it is recommended to follow the [semver](https://semver.org/) specification
* `minAppVersion`: Minimum version number of SiYuan that supports this icon
* `displayName`: Icon display name, mainly used for display in the marketplace list, supports multiple languages
    * `default`: Default language, must exist
    * `zh-CN`, `en` and other languages: optional, must be [BCP 47](https://tools.ietf.org/html/bcp47) tags (e.g. `zh-CN`, `zh-TW`, `en`, `ja`, `pt-BR`)
* `description`: Icon description, mainly used for display in the marketplace list, supports multiple languages
    * `default`: Default language, must exist
    * `zh-CN`, `en` and other languages: optional, must be BCP 47 tags
* `readme`: readme file name, mainly used to display in the marketplace details page, supports multiple languages
    * `default`: Default language, must exist
    * `zh-CN`, `en` and other languages: optional, must be BCP 47 tags
    * Relative images are loaded from `package.zip` when present; otherwise the online marketplace falls back to the matching GitHub Release. Include them in `package.zip` for offline use
* `icon`: Optional marketplace icon filename at the package root. Supports PNG, JPEG, WebP, and AVIF up to 64 KiB; the recommended size is 160*160
* `preview`: Optional marketplace preview filename at the package root. Supports PNG, JPEG, WebP, and AVIF up to 512 KiB; the recommended size is 1024*768
    * SVG is unsupported. To omit an image, remove its field and the legacy `icon.png` or `preview.png`; an empty field value is invalid
* `funding`: Icon sponsorship information
    * `openCollective`: Open Collective name
    * `patreon`: Patreon name
    * `github`: GitHub login name
    * `custom`: Custom sponsorship link list
    * `links`: Labeled custom sponsorship links, for example `{"label": "Sponsor", "url": "https://example.com"}`
* `keywords`: Search keyword list, used for marketplace search function

## Package

No matter which method is used to compile and package, we finally need to generate a package.zip, which contains at
least the following files:

* Image files declared by `icon` and `preview` (optional)
* README*.md
* icon.js
* icon.json

## List on the marketplace

* Generate the package.zip
* Create a new GitHub release using your new version number as the "Tag version". See here for an
  example: https://github.com/siyuan-note/icon-sample/releases
* Upload the file package.zip as binary attachments
* Publish the release

For the first release, fork the [community bazaar repository](https://github.com/siyuan-note/bazaar), add one `owner/repo` line to `icons.txt` in its root, and open a PR against `main`. Use one repository per line without commas or empty lines, and add only one new package per PR. See [Submitting a bazaar package](https://github.com/siyuan-note/bazaar#submitting-a-bazaar-package) for the full process and review rules.

After the PR is merged, the bazaar updates its index automatically. For subsequent updates, increase `version` in the package manifest and publish a regular GitHub Release containing `package.zip`; no additional listing PR is needed. See [Updating a bazaar package](https://github.com/siyuan-note/bazaar#updating-a-bazaar-package) for update timing and troubleshooting, and check deployment status in the [Stage workflow](https://github.com/siyuan-note/bazaar/actions/workflows/stage.yml).
