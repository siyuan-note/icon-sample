[English](https://github.com/siyuan-note/icon-sample/blob/main/README.md)

# 思源笔记图标示例

## 开始

* 通过 <kbd>Use this template</kbd> 按钮将该库文件复制到你自己的库中，请注意库名必须和图标名称一致，默认分支必须为 `main`
* 将你的库克隆到本地开发文件夹中，为了方便可以直接将开发文件夹放置在 `{workspace}/data/icons/` 下

图标文件、更新和卸载会通过思源数据同步共享，各设备独立保留图标选择。旧客户端无需升级即可继续同步笔记，并将内部包归档作为普通文件运输。图标包变更由支持此功能的客户端应用，旧客户端不采用新的图标目录。升级迁移会保留原有本地文件供恢复。该目录中的开发修改也会同步；实验性修改请放在工作空间外，或将整个图标目录加入同步忽略规则。

## 开发

* icon.json
* icon.png（可选默认图标，160*160）
* preview.png（可选默认预览图，1024*768）
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

* `name`：图标名称，必须和库名一致，且全局唯一（集市中不能有重名图标）
* `author`：图标作者名
* `url`：图标仓库地址
* `version`：图标版本号，建议遵循 [semver](https://semver.org/lang/zh-CN/) 规范
* `minAppVersion`：图标支持的最低思源笔记版本号
* `displayName`：图标显示名称，主要用于图标集市列表中显示，支持多语言
    * `default`：默认语言，必须存在
    * `zh-CN`、`en` 等其他语言：可选，须为 [BCP 47](https://tools.ietf.org/html/bcp47) 标签（如 `zh-CN`、`zh-TW`、`en`、`ja`、`pt-BR`）
* `description`：图标描述，主要用于图标集市列表中显示，支持多语言
    * `default`：默认语言，必须存在
    * `zh-CN`、`en` 等其他语言：可选，须为 BCP 47 标签
* `readme`：自述文件名，主要用于图标集市详情页中显示，支持多语言
    * `default`：默认语言，必须存在
    * `zh-CN`、`en` 等其他语言：可选，须为 BCP 47 标签
    * 相对图片存在于 `package.zip` 时从本地加载，否则在线集市会回退到对应的 GitHub Release；如需离线显示，请将图片打入 `package.zip`
* `icon`：可选的集市图标文件名，图片必须位于包根目录；支持 PNG、JPEG、WebP 和 AVIF，最大 64 KiB，建议尺寸为 160*160
* `preview`：可选的集市预览图文件名，图片必须位于包根目录；支持 PNG、JPEG、WebP 和 AVIF，最大 512 KiB，建议尺寸为 1024*768
    * 不支持 SVG。不需要图片时，请删除对应字段及传统文件 `icon.png` 或 `preview.png`，字段值不能为空字符串
* `funding`：图标赞助信息
    * `openCollective`：Open Collective 名称
    * `patreon`：Patreon 名称
    * `github`：GitHub 登录名
    * `custom`：自定义赞助链接列表
    * `links`：带标签的自定义赞助链接列表，例如 `{"label": "赞助", "url": "https://example.com"}`
* `keywords`：搜索关键字列表，用于集市搜索功能

## 打包

无论使用何种方式编译打包，我们最终需要生成一个 package.zip，它至少包含如下文件：

* `icon` 和 `preview` 字段声明的图片文件（可选）
* README*.md
* icon.js
* icon.json

## 上架集市

* 生成 package.zip
* 在 GitHub 上创建一个新的发布，使用图标版本号作为 “Tag
  version”，示例 https://github.com/siyuan-note/icon-sample/releases
* 上传 package.zip 作为二进制附件
* 提交发布

首次发布时，请 Fork [社区集市仓库](https://github.com/siyuan-note/bazaar)，在根目录的 `icons.txt` 中新增一行 `owner/repo`，然后向 `main` 分支提交 PR。每行一个仓库，不添加逗号或空行；每个新增包 PR 只添加一个包。完整流程和审核规则请参阅[提交集市包](https://github.com/siyuan-note/bazaar/blob/main/README.zh-CN.md#提交集市包)。

PR 合并后，集市会自动更新索引。后续更新只需提升清单中的 `version` 并发布包含 `package.zip` 的正式 GitHub Release，无需再次提交上架 PR。更新时效和排错方法请参阅[更新集市包](https://github.com/siyuan-note/bazaar/blob/main/README.zh-CN.md#更新集市包)，部署状态可在 [Stage 工作流](https://github.com/siyuan-note/bazaar/actions/workflows/stage.yml) 查看。
