# Practice 3 使用 GitHub Actions 编译 LaTeX 简历

作者：姚其其 / Seven17777。简历根据本人提供的 Word 简历整理，隐藏手机、邮箱、住址、出生年月等个人信息，保留教育、技能、项目、荣誉及论文投稿状态。

将 `main.tex` 推送到 main，或在 Actions 手动运行 Build LaTeX CV。成功后，从运行页下载 `latex-cv-pdf`，也可以从 Releases 下载 `main.pdf`。

## 原理与答辩

- `.tex` 是文本源文件，PDF 是编译产物；必须展示 Actions 的实际成功记录。
- XeLaTeX 处理 Unicode，ctex 提供中文排版，CI 使用 latex-action 的完整 TeX Live 2025 环境和其中的中文字体，避免本地有字体而云端缺字。
- latexmk 自动按需多次编译以更新链接等辅助信息，默认启用 `-halt-on-error` 使编译错误导致工作流失败。
- PR 只编译和上传 artifact，main 成功构建后才发布；发布任务单独授予写权限。
- 本机没有 LaTeX 也可构建，因为软件环境由工作流声明，在 GitHub runner 上安装。
- 修改一个项目描述并提交，可以演示 PDF 自动更新。

参考示例：https://github.com/reveurmichael/cv_latex
