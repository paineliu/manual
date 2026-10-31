# SynerMind Ego 4 用户手册源码

- [中文手册](zh/index.md)
- [English guide](en/index.md)
- [发布前确认清单](RELEASE-CHECKLIST.md)

当前以评审初稿上线，保留待确认提示，不是正式定版手册。中英文各 11 页（含首页），采用相同文件名、相同目录及相同操作顺序。所有对外内容位于 `zh/`、`en/`；本文件和确认清单仅供内部维护。

## 协作方式

1. 一篇文章一个 Markdown 文件，图片统一放在 `assets/`。
2. 修改操作、参数或界面名称时，同步检查中英文对应页；通过 Git 提交和评审记录修改原因。
3. 非技术同事可提供飞书批注、图片和建议，由文档负责人合入本目录。不要长期并行维护两份正式正文。
4. 页面按用户任务组织，保持五个一级分组、最多两层导航；新增功能优先补进已有页面。
5. 步骤必须写明可观察的成功标志。未知参数、按键和状态不得根据竞品或内部选型推测。
6. 解决“待确认”项时，改成已核验的说明，并同步更新发布清单。删除草稿提示前必须完成整套发布审核。

## 格式与发布交接

采用普通 Markdown、相对链接和表格，避免依赖某个协作平台的专属块。现已使用 VitePress 将正文部署为独立静态网站： https://fivequestions.cn/collecta/manual/ 。

建议网站结构：

- `/zh/`：中文首页及正文。
- `/en/`：英文首页及正文。
- 侧栏按首页的五个分组配置，首页不额外出现在侧栏分组中。
- 语言切换尽量打开对应文章；搜索按当前语言显示结果。
- 只发布批准的正文与图片，不发布本 README、确认清单或内部资料。
- 合并到正式发布分支后自动构建；部署前检查链接、图片、移动端显示和中英文跳转。

VitePress 官方说明：[Markdown 网站生成](https://vitepress.dev/guide/what-is-vitepress)、[多语言](https://vitepress.dev/guide/i18n)、[部署](https://vitepress.dev/guide/deploy)。

## 现有资料与使用边界

本次参考本仓库的：

- [产品架构边界](../hardware/product_architecture/README.md)：仅用于确认产品与数据交付的基本背景，不作为全部功能均已交付的证明。
- [采集员使用教程](../platform/采集员使用教程.md)：用于整理 Collecta 上传概念与流程；用户界面和当前交付环境仍需复核。

已通过浏览器读取竞品 AperEgo 4 页面，参考其产品图和部件说明绘制外观图及按键／接口识别图；未迁移完整正文，也未完成逐项内容对照。草图不代表我方最终结构，后续按交付实物校正。具体素材来源和生成提示词见 [图片说明](assets/README.md)。

不要将内部架构图、厂商密钥文档、演示账号、内部下载地址或未经批准的研发规格放入公开手册。

## 构建、预览与更新线上手册

```bash
cd docs/manual
npm ci
npm run dev
npm run build
npm run preview
```

从仓库根目录发布：

```bash
bash scripts/deploy-manual.sh
```

脚本读取本机 `scripts/deploy.env` 中已有的 SSH 配置，构建后同步到服务器 `/var/www/collecta-manual/releases/`，完成 Nginx 配置检查后切换 `current` 符号链接。旧版本保留，便于回退。无需发布整个 Collecta 前端或后端。

Nginx 独立配置为 `deploy/nginx-collecta-manual.conf`，由 Collecta 的片段引入。`/collecta/manual` 与 `/collecta/manual/` 默认跳转中文；英文入口是 `/collecta/manual/en/`。当前草稿带有禁止搜索引擎索引的标记；正式定版后再调整该标记。

如需回退，在服务器将 `/var/www/collecta-manual/current` 切换到先前的完整 release 目录即可。不要直接修改 `current` 下生成的 HTML，正文始终在本地 Markdown 中修改后重新部署。
