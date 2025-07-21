### 8. 添加主题切换功能 (可选)

*   **AI 沟通**: 询问用户是否希望添加白天/黑夜模式切换功能。
*   如果用户同意，执行以下步骤：
    1.  **安装 `next-themes`**:
        ```bash
        npm install next-themes
        ```
        *   **AI 注意**: 如果遇到 React 19 依赖冲突 (ERESOLVE 错误)，提示用户并建议使用 `--force` 或 `--legacy-peer-deps` 重新运行安装命令。例如: `npm install next-themes --force`。
    2.  **添加 `dropdown-menu` 组件**: (用于切换按钮的 UI)
        ```bash
        npx shadcn@latest add dropdown-menu
        ```
    3.  **创建 `ThemeProvider` 组件**: 在 `components/` 目录下创建 `theme-provider.tsx` 文件：
        ```tsx
        // components/theme-provider.tsx
        "use client"

        import * as React from "react"
        import { ThemeProvider as NextThemesProvider, type ThemeProviderProps } from "next-themes"

        export function ThemeProvider({ children, ...props }: ThemeProviderProps) {
          return <NextThemesProvider {...props}>{children}</NextThemesProvider>
        }
        ```
    4.  **更新根布局 (`app/layout.tsx`)**: 导入 `ThemeProvider` 并用它包裹 `{children}`，同时在 `<html>` 标签添加 `suppressHydrationWarning`：
        ```diff
        // app/layout.tsx
        + import { ThemeProvider } from "@/components/theme-provider";

        export default function RootLayout({ children }) {
          return (
        -   <html lang="en">
        +   <html lang="en" suppressHydrationWarning>
              <body>
        +       <ThemeProvider
        +         attribute="class"
        +         defaultTheme="system"
        +         enableSystem
        +         disableTransitionOnChange
        +       >
                  {children}
        +       </ThemeProvider>
              </body>
            </html>
          );
        }
        ```
        *(AI 注意: 上述 diff 仅为示例，实际修改需基于文件当前内容进行)*
    5.  **创建主题切换按钮组件**: 在 `components/` 目录下创建 `theme-toggle.tsx` 文件：
        ```tsx
        // components/theme-toggle.tsx
        "use client"

        import * as React from "react"
        import { Moon, Sun } from "lucide-react"
        import { useTheme } from "next-themes"

        import { Button } from "@/components/ui/button"
        import {
          DropdownMenu,
          DropdownMenuContent,
          DropdownMenuItem,
          DropdownMenuTrigger,
        } from "@/components/ui/dropdown-menu"

        export function ThemeToggle() {
          const { setTheme } = useTheme()

          return (
            <DropdownMenu>
              <DropdownMenuTrigger asChild>
                <Button variant="outline" size="icon">
                  <Sun className="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0" />
                  <Moon className="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100" />
                  <span className="sr-only">切换主题</span>
                </Button>
              </DropdownMenuTrigger>
              <DropdownMenuContent align="end">
                <DropdownMenuItem onClick={() => setTheme("light")}>
                  亮色
                </DropdownMenuItem>
                <DropdownMenuItem onClick={() => setTheme("dark")}>
                  暗色
                </DropdownMenuItem>
                <DropdownMenuItem onClick={() => setTheme("system")}>
                  系统默认
                </DropdownMenuItem>
              </DropdownMenuContent>
            </DropdownMenu>
          )
        }
        ```
    6.  **在页面中使用切换按钮**: 将 `<ThemeToggle />` 组件添加到需要显示切换按钮的地方（例如，导航栏或页面角落）。步骤 7 中的示例页面代码已包含此操作。
