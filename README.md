# Actrium 字段流程图

[打开流程图](https://alinejun.github.io/actrium-field-flow/)

展示 develenv 三份公开发现文档与 Echo Realm Profile 的字段及使用环节，区分 Publisher、Realm signing key holder 与 Realm issuer 的签名密钥用途。

选择流程步骤时只显示该环节涉及的文档卡片；完整字段默认折叠。

「Actr Authority Discovery」集中介绍 Realm、AFP、Publisher 三份 well-known 的职责、主要字段与使用时机。AFP 入口采用 `/.well-known/actr_facility_provider`。

「Actr Realm Profile」按 Echo Realm 的公开 Profile 说明完整字段、使用环节和 Key roles。AFP 的说明统一为「基础设施提供者」，保留 Realm、Publisher、Issuer、Host、Actor、Service 等英文名称。

三份 Authority Descriptor 与 Realm Profile 的完整 JSON 使用带语法高亮的 JSONC 代码块，逐字段添加用途注释，默认折叠。每个代码块提供「复制 JSONC」与「复制 JSON」按钮，分别复制含注释和不含注释的数据。

公开配置快照日期：2026-11-10。

GitHub Pages 从 `main` 分支根目录发布。
