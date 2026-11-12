# Actrium 字段流程图

[打开流程图](https://alinejun.github.io/actrium-field-flow/)

展示 develenv 三份公开发现文档与 Echo Realm Profile 的字段及使用环节，区分 Publisher、Realm signing key holder 与 Realm issuer 的签名密钥用途。

选择流程步骤时只显示该环节涉及的文档卡片；完整字段默认折叠。

「Actr Authority Discovery」集中介绍 Realm、AFP、Publisher 三份 well-known 的职责、主要字段与使用时机。AFP 入口采用 `/.well-known/actr_facility_provider`。

「Actr Realm Profile」按 Echo Realm 的公开 Profile 说明完整字段、使用环节和 Key roles。AFP 的说明统一为「基础设施提供者」，保留 Realm、Publisher、Issuer、Host、Actor、Service 等英文名称。

三份 Authority Descriptor 与 Realm Profile 的完整 JSON 使用带语法高亮的 JSONC 代码块，逐字段添加用途注释，默认折叠。每个代码块提供「复制 JSONC」与「复制 JSON」按钮，分别复制含注释和不含注释的数据。

公开配置快照日期：2026-11-10。

Membership 说明核对日期：2026-11-11。页面区分 owner 初始化、`role=editor/viewer` 新 member 邀请和 `member_id` 添加 client 邀请；明确 `create_invite` / `join` 使用 Realm client key、加入结果不是 Actor credential，Service 注册要求 owner。完整公开 JSON 的字段和值保持与端点一致。

「Realm Invite」有四步，从申请、权限校验、生成邀请到带外交付。「Realm Join」有七步，依次为导入邀请、取得 Realm 域公钥、验证 Profile 并确定兑换地址、保存 client key、向 AFP Membership 提交 `join`、原子登记和接收结果。Echo 的兑换端点为 `POST https://afp.develenv.com/issuer/membership`。三个示例分别演示受邀成为新 member、已有 member 添加 client，以及使用 Owner Invite 首次成为 Realm 的 owner。

GitHub Pages 从 `main` 分支根目录发布。

## PR #428：显式选择 Service 与 Front

2026-11-12 按 `Actrium/actrium#428` 的 `65b01a360b0b60e074769e7a8cffebafbc06f2f6` 更新 Realm Profile 页。

- 主 Service：`primary_package → packages[ref]`。
- Front：`front_package → packages[ref]`。
- 包表为 2–32 项，版本必须精确，同一类型不能绑定多个摘要；完整包表与未知字段共同参与 Realm 签名。
- 页面可切换 PR 的完整签名规范示例、独立线上验收 Realm 的新格式 Profile，以及原 Echo 的旧版单包快照。原快照正文和签名保持不变。
- 规范示例使用演示域名和示意包摘要，不伪装成线上配置；线上 Front fixture 仅验证归档和控制面，不表示已启动 Front / Service。
- 当前旧 AFP 通过签名前生成的 `package` 主包投影兼容，完整选择进入签名；不宣称 AFP 已原生实现新管理接口。
- 选包不授予 membership、Owner 或宿主启动权限。Host 加载前仍须验证 Publisher 签名、Front Service 依赖与 RPC 契约。

页面维护源位于原可视化 `domain-field-flow.html`，本次可重复导出脚本和验签记录位于工作目录 `realm-pr428-update-20261112/`。保留原有六个主导航及 Owner 初始化 / 新 member / 添加 client 的流程。

最终复核：PR #428 已于 2026-11-12 合并，最终头 `bb0aa747dcd31aa2e43ffbbbd0498306c26b9b58` 的 Realm Profile 文档和签名示例与实现所依据的 `65b01a3` 一致；最后一次同步仅带入主干 Keel 原生沙箱改动。本页规范链接固定到最终 PR 头。
