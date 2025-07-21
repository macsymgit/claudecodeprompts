### 1. 初始化 Next.js 项目

*   **AI 行动**：首先，向用户确认是否需要创建一个新的 Next.js 项目。
    *   如果用户表示需要新项目，你应该询问：“请用户提供新项目的名称。如果你需要建议，我可以提供一些，例如 `my-next-project` 或 `webapp-alpha`。”
    *   获得用户提供的项目名称后（例如，用户选择了 `your-project-name`），你将执行以下命令来创建项目。此命令会确保项目使用 `app` 目录且直接位于根级：
        ```bash
        npx create-next-app@latest your-project-name --typescript --tailwind --eslint --no-src-dir --app
        ```
    *   **AI 沟通**：告知用户：“在 `create-next-app` 执行过程中，CLI 可能会询问一些问题（例如：“Would you like to use Turbopack for `next dev`?”，“Would you like to customize the import alias (`@/*` by default)?”）。对于这些问题，通常可以直接按回车键接受默认选项，除非用户有特定偏好。”
    *   **AI 注意**：如果 `create-next-app` 的版本不支持 `--no-src-dir` 选项，你需要在项目创建后，通过检查文件结构来确认项目符合要求，并告知用户。
*   如果用户表示已有项目，请用户提供项目路径，你后续的操作将在此项目路径下进行。
