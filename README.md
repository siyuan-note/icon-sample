[中文](https://github.com/siyuan-note/icon-sample/blob/main/README_zh_CN.md)

# SiYuan icon sample

## Get started

* Make a copy of this repo as a template with the <kbd>Use this template</kbd> button, please note that the repo name
  must be the same as the icon name, the default branch must be `main`
* Clone your repo to a local development folder. For convenience, you can place this folder in
  your `{workspace}/conf/appearance/icons/` folder

## Development

* icon.json
* icon.png (160*160)
* preview.png (1024*768)
* README*.md
* icon.js

## icon.json

```json
{
  "name": "icon-sample",
  "author": "Vanessa",
  "url": "https://github.com/siyuan-note/icon-sample",
  "version": "0.0.3",
  "minAppVersion": "2.8.8",
  "displayName": {
    "default": "Icon Sample",
    "zh_CN": "图标示例"
  },
  "description": {
    "default": "This is a icon sample",
    "zh_CN": "这是一个图标示例"
  },
  "readme": {
    "default": "README.md",
    "zh_CN": "README_zh_CN.md"
  },
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
* `displayName`: Widget display name, mainly used for display in the marketplace list, supports multiple languages
    * `default`: Default language, must exist
    * `zh_CN`, `en_US` and other languages: optional, it is recommended to provide at least Chinese and English
* `description`: Icon description, mainly used for display in the marketplace list, supports multiple languages
    * `default`: Default language, must exist
    * `zh_CN`, `en_US` and other languages: optional, it is recommended to provide at least Chinese and English
* `readme`: readme file name, mainly used to display in the marketplace details page, supports multiple languages
    * `default`: Default language, must exist
    * `zh_CN`, `en_US` and other languages: optional, it is recommended to provide at least Chinese and English
* `funding`: Icon sponsorship information
    * `openCollective`: Open Collective name
    * `patreon`: Patreon name
    * `github`: GitHub login name
    * `custom`: Custom sponsorship link list
* `keywords`: Search keyword list, used for marketplace search function

## Package

No matter which method is used to compile and package, we finally need to generate a package.zip, which contains at
least the following files:

* icon.png
* preview.png
* README*.md
* icon.js
* icon.json

## List on the marketplace

* Generate the package.zip
* Create a new GitHub release using your new version number as the "Tag version". See here for an
  example: https://github.com/siyuan-note/icon-sample/releases
* Upload the file package.zip as binary attachments
* Publish the release

If it is the first release, please create a pull request to
the [Community Bazaar](https://github.com/siyuan-note/bazaar) repository and modify the icons.json file in it. This
file is the index of all community icon repositories, the format is:

```json
{
  "repos": [
    "username/reponame"
  ]
}
```

After the PR is merged, the bazaar will automatically update the index and deploy through GitHub Actions. When releasing
a new version of the icon in the future, you only need to follow the above steps to create a new release, and you
don't need to PR the community bazaar repo.

Under normal circumstances, the community bazaar repo will automatically update the index and deploy every hour,
and you can check the deployment status at https://github.com/siyuan-note/bazaar/actions.
