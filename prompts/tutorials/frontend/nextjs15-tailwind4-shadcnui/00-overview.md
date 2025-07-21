# 指导 AI 助手配置 Next.js 15 + Tailwind CSS 4 + Shadcn UI

**本文档的目标读者**：AI 助手（以下简称“你”或“AI”）

**任务**：你将协助用户在一个 Next.js 15 项目中，成功安装和配置 Tailwind CSS v4 及 Shadcn UI。在整个过程中，你需要在关键步骤与用户进行交互，获取必要的决策和信息。

**前提（AI 需向用户确认）：**
*   用户已准备好一个 Next.js 15 项目，或者授权你创建一个新项目。该项目的目录结构应为 `app` 目录、`components` 目录等直接位于项目根目录下（非 `src` 结构）。
*   用户的开发环境中已安装 Node.js 和 npm (或 yarn/pnpm)。

---

## 安装与配置步骤概览

本文档集将指导你完成以下主要步骤：

1.  **初始化 Next.js 项目**: 创建或确认现有项目。
2.  **安装核心依赖**: 安装 Tailwind CSS, PostCSS, Autoprefixer 等。
3.  **配置 PostCSS**: 创建 `postcss.config.mjs`。
4.  **配置全局 CSS 和 Shadcn UI 主题**: 更新 `app/globals.css`。
5.  **初始化 Shadcn UI**: 运行 `npx shadcn@latest init` 并进行配置。
6.  **验证配置文件**: 检查 `components.json`, `tsconfig.json`。
7.  **添加并使用 Shadcn UI 组件**: 创建示例页面。
8.  **添加主题切换功能 (可选)**: 实现亮色/暗色模式。
9.  **运行开发服务器**: 启动并验证项目。

每个步骤的详细说明见对应的子文档。

---

**最终检查清单（AI 与用户共同确认）：**
*   **AI 确认并告知用户**：所有路径配置（在 `components.json`, `tsconfig.json` 中，以及 CSS 文件中的 `@import`）均已正确设置，以对应项目根目录下的文件结构。
*   **AI 确认并告知用户**：Tailwind CSS 和 Shadcn UI 所需的核心依赖均已通过 `npm install -D` 正确安装。
*   **AI 确认并告知用户**：全局 CSS 文件 (`app/globals.css`) 已按照指南正确配置，并已在主布局文件 (`app/layout.tsx` 或 `.js`) 中导入。
*   **AI 确认并告知用户**：`shadcn@latest init` 命令已成功执行，并且相关的配置文件 (`components.json`, `tailwind.config.js/ts`) 已正确生成/更新并通过验证。
*   **用户确认**：在浏览器中查看应用时，Shadcn UI 组件样式和功能均符合预期。

**AI 总结**：在用户确认一切正常后，你可以总结：“太好了！Next.js 15 项目已成功配置 Tailwind CSS v4 和 Shadcn UI。如果后续需要添加更多组件或进行调整，请随时告诉我。”
