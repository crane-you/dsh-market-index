# dsh-market-index

[DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 插件市场索引（format 1），收录 [crane-you](https://github.com/crane-you) 发布的 DSH 插件。

A format-1 plugin market index for DeepSeek Harness, listing the DSH bundles published by crane-you.

## 索引地址 · Index URL

```
https://cdn.jsdelivr.net/gh/crane-you/dsh-market-index@main/index.json
```

## 怎么用 · How to add it

DSH → 设置 → 插件 → **发现** → 添加索引，粘贴上面的地址。

Settings → Plugins → **Discover** → add index, paste the URL above.

## 收录的插件 · Listed plugins

| 包名 · Package | 名称 · Name | 说明 · What it does |
| --- | --- | --- |
| [`dsh-task-plugin-scout`](https://www.npmjs.com/package/dsh-task-plugin-scout) | `dsh-task-plugin-scout` | 按任务排序本机插件（已启用 / 已安装但未启用 / 市场可安装），并给出每个候选的启用或安装步骤。 |

## 为什么用 jsDelivr 地址 · Why the jsDelivr URL

索引源文件托管在 GitHub，但市场客户端**拒绝重定向**，且部分网络环境下 `raw.githubusercontent.com` 无法通过证书校验。jsDelivr 提供同一份文档的 HTTPS 直链（无重定向），因此这里给出的是 CDN 地址。

The index is hosted on GitHub, but the market client refuses redirects and, on some networks, `raw.githubusercontent.com` fails certificate verification. jsDelivr serves the same document over HTTPS without a redirect, so that is the URL to configure.

## 格式 · Format

`index.json` 遵循 DSH 插件市场索引 **format 1**（校验实现见 `@deepseek-ai/dsh-plugin-market-index`）。版本号与发布时间从 npm registry 读取，避免与已发布内容漂移。

`index.json` follows DSH plugin market index **format 1**. Versions and publish timestamps are read from the npm registry so the index cannot drift from what is installable.