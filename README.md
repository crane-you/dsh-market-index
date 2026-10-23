# dsh-market-index

[DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 插件市场索引（format 1），收录 [crane-you](https://github.com/crane-you) 发布的 DSH 插件。

A format-1 plugin market index for DeepSeek Harness, listing the DSH bundles published by crane-you.

> **状态 · Status**：这份索引**已退役**。DSH 的市场已改用 [dshmarket 的社区目录](https://cdn.jsdelivr.net/npm/dsh-plugin-catalog/index.json)（同样是 format 1），因此本仓库**已归档为只读**，npm 上的 `dsh-market-index` 包**也已从 npm 取消发布**（全部 7 个版本，2026-10-23 完成，registry 现在只留下墓碑记录）。它保留下来的价值是作为参考：演示了「把 format-1 索引发布成 npm 数据包、再用无重定向的 CDN 直链喂给市场」的完整做法，含版本固定与缓存的取舍。
>
> **Status**: retired. The market now reads dshmarket's community catalog, this repository **is archived (read-only)**, and the `dsh-market-index` npm package **has been unpublished from npm** (all seven versions, on 2026-10-23; the registry keeps only a tombstone record). It remains as a reference for publishing a format-1 index as an npm data package and feeding the market a redirect-free CDN URL, including the version-pinning and cache trade-offs.

## 索引地址 · Index URL

```
https://cdn.jsdelivr.net/npm/dsh-market-index@1/index.json
```

源文件就是这个仓库里的 `index.json`，但给市场客户端请用上面的 **npm 回源直链**：npm 数据包
[`dsh-market-index`](https://www.npmjs.com/package/dsh-market-index) 分发同一份文档。

> **缓存与「立刻生效」** · Cache note：jsDelivr 的缓存很激进 —— GitHub 分支地址（`@main`）边缘缓存 **12 小时**（`s-maxage=43200`），查询参数不参与缓存键；npm 的 `@1` **范围地址理论上会自动跟随，但实测其解析结果可能在边缘缓存里长时间停留**（观察到十几分钟后仍是旧文档）。所以按需要选：
> - **人工加索引、能接受延迟** → 用上面的 `@1` 地址最省事（新版本最终会跟随）；
> - **需要立即且确定地读到最新索引** → 固定到**精确版本**，例如 `https://cdn.jsdelivr.net/npm/dsh-market-index@1.0.4/index.json` —— 每个版本都是不可变的缓存键，一次就对。本机 DSH 里配置的就是这种精确版本地址，索引重新发布后需同步版本号。

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