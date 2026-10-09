# FlowForge 项目共享目录

## FlowForge 是什么
FlowForge 是一款 **BYO-API（自带 API 密钥）的节点式 AI 视频创作桌面工具**（macOS / Windows）。创作者在可视化画布上连接「一键拉片、关键帧编辑、画线运镜、文/图生视频、图片生成、形象资产」等节点，像搭积木一样完成 AI 视频创作。

- **自带密钥、成本可控**：使用你自己在火山引擎等平台的 API，自主充值、按量付费，区别于会员 / 积分制平台；可保存多组密钥、按项目一键切换。
- **专业创作节点**：一键拉片 / 复刻、关键帧编辑、画线运镜（FPV 飞行轨迹）、真人 / 虚拟人形象、文 / 图生视频与图片生成。
- **AI 协同**：可通过本地连接器让豆包、DeepSeek Harness、WorkBuddy 等电脑端智能体协助诊断、创作与扩展开发。
- **项目共享**：用户可分享自己的工作流与开发成果，也能一键安装他人共享的项目。

> 本仓库即 FlowForge「**项目共享**」的官方扩展目录（已签名 catalog）。客户端从这里发现并安装经过签名的**声明式「配方」**（工作流模板 / 预设 / 连接器配置）。

> ## ⚠️ 如何使用（请先阅读）
> 本仓库是 **FlowForge 应用的扩展分发源，不是可单独运行的模型或软件**。直接下载 `catalog.json` 或 `packages/*.zip` **无法直接使用**——这些包只能由 FlowForge 客户端在应用内拉取、验签并安装。
> 1. 先安装 **FlowForge** 桌面端；
> 2. 打开应用内的「**项目共享**」；
> 3. 在列表中选择项目并点击「安装」，客户端会自动从本镜像下载、校验签名并完成安装，**无需手动下载本仓库文件**。
>
> 换言之：**没有安装 FlowForge，下载这里的任何文件都没有作用。**

## 获取 FlowForge
主程序不提供公开下载。可先查看产品介绍，联系客服微信 **`W18807763889`**，了解功能与价格后获取安装与授权（一次买断；模型 API 费用由你向平台自充、与授权费无关）。

## 目录说明
- 内容无关、BYO-API：扩展本身不含可执行代码，仅为声明式 JSON「配方」。
- 唯一发现入口：[`catalog.json`](./catalog.json)。
- 包目录：[`packages/`](./packages)，每个 `.zip` 含 `manifest.json` + 内容文件 + `sha256` + 作者包级签名。
- 验签公钥：[`public-keys.json`](./public-keys.json)（与客户端内置公钥一致）。

## 安全模型
- catalog 由 catalog 签名密钥签名（支持 current/fallback 双根钥轮换；轮换公告需双签）。
- 每个包由独立的 package 签名密钥对其 `sha256` 签名。
- 客户端安装前依次校验：catalog 签名 → 包 sha256 → 包签名 → manifest/内容合法性。
- 撤销通过 catalog 内 `revocations` 列表下发，被撤销条目无法安装。
- 签名私钥离线保管，**不在本仓库内**。

## 镜像
- GitHub（国际）：`https://raw.githubusercontent.com/shixinb/community-catalog/main/`
- 魔搭 ModelScope（国内）：`https://www.modelscope.cn/api/v1/datasets/zbbs2026/flowforge-community/repo?Revision=master&FilePath=`

同包同签名，两处内容一致。
