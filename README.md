# VAULT 中文多功能工作台

`vault-studio-cn` 是面向 VAULT 模块化收纳系统的一站式中文工作台。单 HTML 文件即可离线运行，集成模型检索、三维预览、场景组合、部件展开、组装指南、空间配色、耗材预算、打印计划与文件导出。

[by 王嘉祥](https://github.com/iWangJiaxiang)

[在线使用](https://vault-studio.jiaxiang.wang/) · [个人网站](https://www.jiaxiang.wang/)

## 功能

- **场景导视与组合清单**：13 组场景，按层查看零件、打印文件份数与五金参考。
- **模型检索与三维预览**：736 条新旧版模型索引及缩略图；关联本地 STL 后可旋转查看真实模型。
- **部件展开与组装指南**：按型号定位部件、查看展开图，并对照中文步骤与原版手册。
- **空间规划与配色**：自定义堆叠、查看名义尺寸、检查高度余量、保存配色方案。
- **耗材与成本预算**：根据输入的切片用料、单价、损耗和出料速度计算预算与粗略时长。
- **打印计划管理**：同零件同版本合并份数，记录配色、支撑与完成进度。
- **文件导出与备份**：支持 CSV 清单、原始 STL ZIP、JSON 备份恢复及打印/PDF。
- **离线使用**：图片、数据、手册和运行依赖内嵌，无需服务器或 API 密钥。

## 开始使用

1. 下载 [VAULT-本地工作台.html](./VAULT-本地工作台.html)，用浏览器打开。
2. 选择场景组合，或从模型图库添加零件到打印计划。
3. 点击「关联本地模型文件夹」，选择自己已有且已解压的 VAULT 模型目录。
4. 核对份数、配色和支撑，导出文件后在切片软件中完成打印设置。

HTML 约 34.5 MB，包含缩略图、64 页说明图及五份手册 PDF，**不包含 STL 模型文件**。关联模型时只在本地读取，不上传、不修改原文件。

详细操作、保存方式及使用限制见 [使用说明](./使用说明.md)。

## 在线部署与自定义域名

GitHub Actions 工作流 [deploy-pages.yml](./.github/workflows/deploy-pages.yml) 在 `main` 分支的 HTML、`CNAME` 或工作流文件更新时自动部署，也支持在 Actions 页面手动运行。发布时将单 HTML 复制为 `index.html`，同时发布 `CNAME`，无需构建依赖。

仓库的 **Settings → Pages → Build and deployment → Source** 使用 **GitHub Actions**，自定义域名设置为 `vault-studio.jiaxiang.wang`。在 `jiaxiang.wang` 的 DNS 服务商处设置：

| 参数 | 配置值 |
| --- | --- |
| 记录类型 | `CNAME` |
| 主机记录 | `vault-studio` |
| 完整域名 | `vault-studio.jiaxiang.wang` |
| 目标 / 记录值 | `iwangjiaxiang.github.io` |
| TTL | `300` 秒或自动 |

目标值不包含协议或仓库路径。如果已有同名 CNAME，直接映射 GitHub Pages 时需替换旧记录，避免同名记录冲突。DNS 生效并完成 GitHub 证书签发后，在 Pages 设置中启用 **Enforce HTTPS**。

在线版与下载版使用同一份 HTML。浏览器数据按网站来源分别保存；从本地文件切换到在线版时，可通过 JSON 备份和恢复迁移计划。

## 来源与参考项目

本项目基于现有可视化指南制作单文件离线版本，并结合以下项目的功能与交互思路进行整理和扩展。

| 来源 / 项目 | 本项目采用或参考的内容 |
| --- | --- |
| [VAULT 模块化收纳指南](https://vault-storage-visual-guide.ample-rhino-5935.chatgpt.site/#combinations) | 主要基础：页面布局与交互代码、13 组场景组合数据、模型索引、预览图及说明资料。原导视制作署名为「普罗米修斯盗火者」。本项目在此基础上进行单文件打包、离线适配和中文界面整理。 |
| [HairuoLiu / VaultForge](https://github.com/HairuoLiu/VaultForge) | 参考空间规划、耗材与成本预算、物料清单等功能思路。 |
| [link-ding / vault-workbench](https://github.com/link-ding/vault-workbench) | 参考本地模型关联、文件去重、打印份数管理及保留原始 STL 的导出流程。 |
| [jiahaom / vault-hub](https://github.com/jiahaom/vault-hub) | 参考配色方案、打印完成勾选及浏览器本地保存等交互。 |

感谢原指南作者及各参考项目的贡献。本项目对功能进行了取舍和适配，并未完整移植上述项目的全部能力；例如，本版本不提供自动切片、G-code 生成或额外本机 3MF 助手。

## 权利归属与第三方组件

- 本项目为非官方中文整理与扩展工具，与 USSA Design 无官方关联。
- VAULT 模型、手册、图文和商标归 USSA Design 及各自权利人所有；原指南及参考项目的相关权利归各自作者所有。
- 三维显示使用 Three.js，压缩打包使用 fflate。相关第三方许可证保留在 HTML 的「关于工作台」中。
- 场景组合包含按图推测的配置，尚未经过全套实物装配验证；打印前请核对原版手册、模型版本、实际尺寸和切片结果。
