### 2. 安装核心依赖

*   **AI 行动**：进入项目目录。如果项目是新建的，目录名即为上一步中用户提供的名称。如果是已有项目，则为你从用户处获取的路径。
    ```bash
    cd your-project-name
    ```
    (将 `your-project-name` 替换为实际的项目目录名)
*   **AI 行动**：接下来，你将安装 Tailwind CSS 及其运行所需的关键工具。告知用户：“我将安装 Tailwind CSS 及其相关依赖，包括 PostCSS, Autoprefixer, @tailwindcss/postcss, 以及 tw-animate-css (用于 Shadcn UI 动画)。”
    ```bash
    npm install -D tailwindcss@latest postcss@latest autoprefixer@latest @tailwindcss/postcss tw-animate-css
    ```
*   **AI 验证与沟通**：执行完毕后，你需要检查命令是否成功执行。如果遇到错误，应将错误信息呈现给用户并请求指示。如果成功，告知用户：“核心依赖已成功安装。”
