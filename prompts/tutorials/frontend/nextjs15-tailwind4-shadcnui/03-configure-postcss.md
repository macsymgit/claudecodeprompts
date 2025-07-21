### 3. 配置 PostCSS

*   **AI 行动**：告知用户：“现在我将配置 PostCSS。这是 Tailwind CSS 工作所必需的。”
*   你将在项目根目录下创建一个名为 `postcss.config.mjs` 的文件，并将以下配置内容写入该文件：
    ```javascript
    // postcss.config.mjs
    export default {
      plugins: {
        '@tailwindcss/postcss': {},
        'autoprefixer': {},
      },
    };
    ```
*   **AI 备选方案沟通**：你可以向用户提议：“如果项目规范或偏好使用 `.js` 文件扩展名，我也可以创建 `postcss.config.js` 并使用相应的 `module.exports` 语法。请用户确认是否需要更改。” 如果用户无异议，则使用 `.mjs`。
