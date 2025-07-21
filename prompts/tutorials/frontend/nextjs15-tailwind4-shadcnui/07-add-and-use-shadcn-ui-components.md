### 7. 添加并使用 Shadcn UI 组件

*   **AI 行动与沟通**：你可以向用户建议添加一些示例组件来测试安装。例如：“用户，为了验证 Shadcn UI 是否正常工作，我可以添加一些常用组件（如 Card, Button, Input, Avatar, Select, Calendar, Popover）吗？”
*   如果用户同意，你将逐个或分批执行添加命令（注意：`date-picker` 不存在，需要添加 `calendar` 和 `popover`）：
    ```bash
    npx shadcn@latest add button card input avatar select calendar popover dropdown-menu badge
    ```
    *(AI 注意: 上述命令添加了欢迎页面所需的组件，包括主题切换按钮使用的 `dropdown-menu` 和 `badge`)*
    并告知用户：“这通常会在 `components/ui/` 目录下创建相应的组件文件。”
*   **AI 行动与沟通**：然后，你可以建议在主页 (`app/page.tsx`) 使用这些组件构建一个示例页面。例如：“我可以用这些组件在 `app/page.tsx` 中创建一个示例页面吗？”
*   如果用户同意，你将修改 `app/page.tsx`，创建一个包含主题切换按钮和固定框架亮点的欢迎页面：
    ```tsx
    // 在 app/page.tsx
    "use client";

    import { Button } from "@/components/ui/button";
    import {
      Card,
      CardContent,
      CardDescription,
      CardFooter,
      CardHeader,
      CardTitle,
    } from "@/components/ui/card";
    // 导入更多图标
    import { PartyPopper, Zap, Palette, Settings2, ExternalLink, Library, CheckCircle, Rocket, Package, PaintBucket, Gauge } from 'lucide-react'; // 添加更多图标
    import { ThemeToggle } from "@/components/theme-toggle";
    import { cn } from "@/lib/utils";
    import { Badge } from "@/components/ui/badge";
    import { useState } from "react"; // 移除 useEffect

    // 为 CardContent 准备的固定友好亮点
    const friendlyHighlights = {
      nextjs: [
        { icon: Gauge, text: "Turbopack: 开发启动速度提升数倍" },
        { icon: Rocket, text: "智能缓存: 默认不缓存 API，加载更快" },
        { icon: CheckCircle, text: "React 19 支持: 完全兼容最新特性" },
      ],
      tailwind: [
        { icon: Zap, text: "全新引擎: 构建速度提升约 5 倍" },
        { icon: Palette, text: "现代 CSS 支持: 利用最新网页样式技术" },
        { icon: Settings2, text: "零配置内容检测: 自动扫描更省心" },
      ],
      shadcn: [
        { icon: PaintBucket, text: "OKLCH 颜色: 支持更广色域，色彩更精准" },
        { icon: Package, text: "组件化构建: 复制粘贴即可使用" },
        { icon: Settings2, text: "完全可定制: 轻松调整样式匹配品牌" },
      ]
    };


    export default function WelcomePage() {
      // 保留 activeFramework 用于 Badge 悬停效果
      const [activeFramework, setActiveFramework] = useState<'nextjs' | 'tailwind' | 'shadcn'>('nextjs');
      // 移除 featureIndex 和相关的 useEffect

      return (
        <div className="relative flex flex-col justify-center items-center min-h-screen p-6 bg-background transition-colors duration-500">
          <div className="absolute top-6 right-6 z-10">
            <ThemeToggle />
          </div>

          <Card className="w-full max-w-2xl text-center shadow-xl border border-border/40 rounded-xl overflow-hidden backdrop-blur-sm transition-all duration-300 hover:shadow-primary/10 relative"> {/* 稍微加宽 */}
            <div className="absolute -top-20 -right-20 w-40 h-40 bg-primary/10 rounded-full blur-3xl opacity-70 animate-pulse"></div>
            <div className="absolute -bottom-20 -left-20 w-40 h-40 bg-primary/10 rounded-full blur-3xl opacity-70 animate-pulse delay-700"></div>

            <CardHeader className="bg-card/60 p-8 pb-6 space-y-4 relative">
              <div className="flex justify-center mb-2">
                <div className="relative group">
                  <div className="absolute inset-0 bg-primary/20 rounded-full blur-md opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                  <PartyPopper className="h-14 w-14 text-primary animate-pulse relative z-10" />
                  <div className="absolute -top-1 -right-1 h-3 w-3 bg-primary rounded-full animate-ping" />
                  <div className="absolute -bottom-1 -left-1 h-2 w-2 bg-primary/70 rounded-full animate-ping delay-300" />
                </div>
              </div>
              <CardTitle className="text-3xl font-bold tracking-tight">恭喜！项目初始化成功</CardTitle>
              <CardDescription className="text-base">
                您的开发环境已准备就绪，可以开始构建精彩的应用了
              </CardDescription>
              {/* 框架选择 Badge */}
              <div className="flex justify-center gap-2 flex-wrap pt-2"> {/* 增加 pt-2 */}
                 <Badge
                  variant={activeFramework === 'nextjs' ? 'default' : 'outline'}
                  className={cn(
                    "px-3 py-1 cursor-pointer transition-all duration-300",
                    activeFramework === 'nextjs' ? "bg-primary/90" : "hover:bg-primary/10"
                  )}
                  onMouseEnter={() => setActiveFramework('nextjs')}
                >
                  <svg className="mr-1 h-3.5 w-3.5" viewBox="0 0 180 180" fill="none" xmlns="http://www.w3.org/2000/svg"><mask id="mask0_408_134" style={{ maskType: 'alpha' }} maskUnits="userSpaceOnUse" x="0" y="0" width="180" height="180"><circle cx="90" cy="90" r="90" fill="black" /></mask><g mask="url(#mask0_408_134)"><circle cx="90" cy="90" r="90" fill="black" /><path d="M149.508 157.52L69.142 54H54V125.97H66.1136V69.3836L139.999 164.845C143.333 162.614 146.509 160.165 149.508 157.52Z" fill="url(#paint0_linear_408_134)" /><rect x="115" y="54" width="12" height="72" fill="url(#paint1_linear_408_134)" /></g><defs><linearGradient id="paint0_linear_408_134" x1="109" y1="116.5" x2="144.5" y2="160.5" gradientUnits="userSpaceOnUse"><stop stopColor="white" /><stop offset="1" stopColor="white" stopOpacity="0" /></linearGradient><linearGradient id="paint1_linear_408_134" x1="121" y1="54" x2="120.799" y2="106.875" gradientUnits="userSpaceOnUse"><stop stopColor="white" /><stop offset="1" stopColor="white" stopOpacity="0" /></linearGradient></defs></svg>
                  Next.js 15
                </Badge>
                {/* 修改 Tailwind Badge 样式 */}
                <Badge
                  variant={activeFramework === 'tailwind' ? 'secondary' : 'outline'} // 使用 secondary variant
                  className={cn(
                    "px-3 py-1 cursor-pointer transition-all duration-300",
                     // 移除蓝色硬编码，悬停效果由 variant 控制
                     activeFramework === 'tailwind' ? "border-border" : "hover:bg-secondary/80" // 调整悬停效果
                  )}
                  onMouseEnter={() => setActiveFramework('tailwind')}
                >
                  <svg className="mr-1 h-3.5 w-3.5" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path fillRule="evenodd" clipRule="evenodd" d="M12 6.036c-2.667 0-4.333 1.325-5 3.976 1-1.325 2.167-1.822 3.5-1.491.761.189 1.305.738 1.906 1.345C13.387 10.855 14.522 12 17 12c2.667 0 4.333-1.325 5-3.976-1 1.325-2.167 1.822-3.5 1.491-.761-.189-1.305-.738-1.906-1.345C15.613 7.181 14.478 6.036 12 6.036zM7 12c-2.667 0-4.333 1.325-5 3.976 1-1.325 2.167-1.822 3.5-1.491.761.189 1.305.738 1.906 1.345C8.387 16.819 9.522 17.964 12 17.964c2.667 0 4.333-1.325 5-3.976-1 1.325-2.167 1.822-3.5 1.491-.761-.189-1.305-.738-1.906-1.345C10.613 13.145 9.478 12 7 12z" fill="currentColor" /></svg> {/* 使用 currentColor */}
                  Tailwind CSS v4
                </Badge>
                <Badge
                  variant={activeFramework === 'shadcn' ? 'default' : 'outline'}
                  className={cn(
                    "px-3 py-1 cursor-pointer transition-all duration-300",
                    activeFramework === 'shadcn' ? "bg-foreground text-background" : "hover:bg-foreground/10"
                  )}
                  onMouseEnter={() => setActiveFramework('shadcn')}
                >
                  <svg className="mr-1 h-3.5 w-3.5" viewBox="0 0 256 256" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M165.809 128C165.809 149.122 148.931 166 127.809 166C106.687 166 89.809 149.122 89.809 128C89.809 106.878 106.687 90 127.809 90C148.931 90 165.809 106.878 165.809 128Z" fill="currentColor" /><path fillRule="evenodd" clipRule="evenodd" d="M128 0C57.308 0 0 57.308 0 128C0 198.692 57.308 256 128 256C198.692 256 256 198.692 256 128C256 57.308 198.692 0 128 0ZM127.809 198C166.943 198 198.809 166.134 198.809 127C198.809 87.866 166.943 56 127.809 56C88.6751 56 56.809 87.866 56.809 127C56.809 166.134 88.6751 198 127.809 198Z" fill="currentColor" /></svg>
                  Shadcn UI
                </Badge>
              </div>
              {/* 移除特性轮播区域 */}
            </CardHeader>

            {/* 新的 CardContent，展示固定的友好亮点 */}
            <CardContent className="p-8 pt-6 space-y-6 bg-gradient-to-b from-card/60 to-background/80 relative z-10">
              <h3 className="text-lg font-semibold text-center mb-4">核心优势</h3>
              <div className="grid grid-cols-1 sm:grid-cols-3 gap-6 text-left">
                {/* Next.js 亮点 */}
                <div className="space-y-3 p-4 rounded-lg bg-card/40 border border-border/30">
                  <h4 className="font-medium text-center text-primary/90">Next.js 15</h4>
                  <ul className="space-y-2">
                    {friendlyHighlights.nextjs.map((item, index) => (
                      <li key={`next-${index}`} className="flex items-start space-x-2">
                        <item.icon className="h-4 w-4 mt-1 text-primary/80 flex-shrink-0" />
                        <span className="text-sm text-muted-foreground">{item.text}</span>
                      </li>
                    ))}
                  </ul>
                </div>
                 {/* Tailwind CSS 亮点 */}
                 <div className="space-y-3 p-4 rounded-lg bg-card/40 border border-border/30">
                  <h4 className="font-medium text-center text-secondary-foreground">Tailwind CSS 4</h4> {/* 使用 secondary 颜色 */}
                  <ul className="space-y-2">
                    {friendlyHighlights.tailwind.map((item, index) => (
                      <li key={`tailwind-${index}`} className="flex items-start space-x-2">
                        <item.icon className="h-4 w-4 mt-1 text-secondary-foreground/80 flex-shrink-0" /> {/* 使用 secondary 颜色 */}
                        <span className="text-sm text-muted-foreground">{item.text}</span>
                      </li>
                    ))}
                  </ul>
                </div>
                 {/* Shadcn UI 亮点 */}
                 <div className="space-y-3 p-4 rounded-lg bg-card/40 border border-border/30">
                  <h4 className="font-medium text-center text-accent-foreground">Shadcn UI</h4> {/* 使用 accent 颜色 */}
                  <ul className="space-y-2">
                    {friendlyHighlights.shadcn.map((item, index) => (
                      <li key={`shadcn-${index}`} className="flex items-start space-x-2">
                        <item.icon className="h-4 w-4 mt-1 text-accent-foreground/80 flex-shrink-0" /> {/* 使用 accent 颜色 */}
                        <span className="text-sm text-muted-foreground">{item.text}</span>
                      </li>
                    ))}
                  </ul>
                </div>
              </div>
            </CardContent>

            <CardFooter className="flex justify-center gap-4 p-8 pt-6 bg-background/50 relative z-10"> {/* 调整上内边距 */}
              <Button
                onClick={() => window.open('https://nextjs.org/docs', '_blank')}
                className="transition-all duration-300 hover:shadow-md hover:shadow-primary/10 hover:translate-y-[-2px] group"
              >
                <ExternalLink className="mr-2 h-4 w-4 opacity-70 group-hover:opacity-100 transition-opacity" />
                查看文档
              </Button>
              <Button
                variant="outline"
                onClick={() => window.open('https://ui.shadcn.com', '_blank')}
                className="transition-all duration-300 hover:shadow-md hover:shadow-primary/10 hover:translate-y-[-2px] hover:border-primary/30 group"
              >
                <Library className="mr-2 h-4 w-4 opacity-70 group-hover:opacity-100 transition-opacity" />
                组件库
              </Button>
            </CardFooter>
          </Card>
        </div>
      );
    }
