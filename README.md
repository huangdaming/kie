作为精通 JavaFX + CSS 的高级 UI/UX 设计师，请帮我重构「Mata Toolkit」个人工具集的界面，打造现代科技感（类似 VS Code / Notion 极简风）。请严格按照以下规范生成或修改代码：

一、整体风格与布局框架
1. 深色主题（Dark Theme）：全局背景使用深灰 #1e1e1e，主文字颜色 #d4d4d4，强调色/交互色使用科技蓝 #0078d4（用于选中状态、按钮 hover、激活态等）。
2. 布局容器：主窗口使用 VBox 承载所有元素，设置全局内边距 Padding: 20px，子元素间距 Spacing: 15px，保证界面呼吸感。
3. 导航栏（TabPane）：移除默认边框与背景；选中 Tab 底部添加 2px 蓝色横线（-fx-border-color: transparent transparent #0078d4 transparent; -fx-border-width: 0 0 2px 0;）；未选中 Tab 文字透明度设为 0.6；Tab 标签字体为 Segoe UI, 14px，hover 时文字亮度提升。
4. 按钮统一风格：所有操作按钮设为圆角矩形（-fx-background-radius: 4px;），默认背景 #2d2d2d，文字 #d4d4d4；hover 时背景变为 #3c3c3c；点击/激活时背景变为 #0078d4 且文字变为白色；按钮组使用 HBox 水平排列，垂直居中对齐，间距 8px。

二、各功能模块细节优化
1. Column Join 模块
   - Delimiter 输入框：背景 #2d2d2d，边框 1px solid #3c3c3c，圆角 4px，内边距 5px 10px，文字颜色 #d4d4d4。
   - 操作按钮（Join/Split/Sort A-Z/Sort Z-A/Copy）：放入 HBox，垂直居中，间距 8px，样式遵循全局按钮规范。
   - 输入/输出文本区：背景 #252526，边框 1px solid #3c3c3c，圆角 4px，内边距 10px；滚动条轨道 #1e1e1e，滑块 #424242，hover 滑块 #5a5a5a。
   - 底部 Tip 文字：颜色 #888888，字体 12px，左对齐。

2. String Tools 模块
   - 操作按钮组（UPPER/lower/Trim/Collapse Spaces 等）：HBox 水平排列，间距 8px，垂直居中，每个按钮最小宽度 80px，宽度自适应。
   - 输入/输出文本区：样式与 Column Join 完全一致；输入区上方添加标题 "Input:"，输出区上方添加 "Output:"，标题字体 14px，颜色 #aaaaaa，下边距 5px。

3. JSON Tools 模块
   - 操作按钮（Format/Minify/Validate 等）：HBox 水平排列，间距 8px，样式遵循全局按钮规范。
   - 输入/输出区域：文本区背景 #252526，边框 1px solid #3c3c3c，圆角 4px，内边距 10px；若支持语法高亮则集成 RichTextFX，否则保证等宽字体清晰可读。

4. Token Parser 模块
   - JWT Token 输入区：大文本区，背景 #252526，边框 1px solid #3c3c3c，圆角 4px，内边距 10px，高度占页面 30%。
   - Header/Payload/Signature 展示区：使用 TitledPane 折叠面板，标题栏背景 #2d2d2d，文字 #d4d4d4；展开后内容区背景 #252526，内边距 10px；JSON 内容使用等宽字体 Consolas, 12px，自动换行。
   - Parse/Clear 按钮：置于 JWT Token 输入区下方，HBox 水平排列，间距 8px，样式遵循全局按钮规范。

5. Clipboard History 模块
   - 顶部操作栏（Refresh/Copy Selected/Search）：HBox 包裹，Search 输入框背景 #2d2d2d，边框 1px solid #3c3c3c，圆角 4px，内边距 5px 10px；按钮组间距 8px。
   - 剪贴板列表（ListView/TableView）：单元格背景 #252526，选中项背景 #0078d4（文字变白），未选中项文字 #d4d4d4；列表项间距 5px，内边距 10px。
   - Preview 区域：背景 #252526，边框 1px solid #3c3c3c，圆角 4px，内边距 10px，高度占页面 30%。
   - 底部 Tip 文字：颜色 #888888，字体 12px，左对齐。

三、交互与细节增强
1. 动效与反馈：按钮点击时添加轻微缩放（scale(0.98)）+ 阴影变化；Tab 切换时内容区添加淡入动画（fade-in，持续 200ms）。
2. 滚动条美化：所有文本区滚动条宽度 8px，轨道 #1e1e1e，滑块 #424242，hover 滑块 #5a5a5a。
3. 响应式适配：窗口缩放时各组件按比例调整大小，保证布局不崩坏、不溢出。
4. 一致性检查：所有页面的输入框、按钮、文本区、标题样式必须完全统一，禁止出现视觉割裂。

请基于以上规范，优先输出完整的 CSS 样式文件，再给出对应 FXML/JavaFX 布局代码的修改建议，确保可直接落地使用。
