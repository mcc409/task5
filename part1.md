## 使用的 Agent

- **Agent 名称**：DeepSeek Harness（dsh）
- **选择原因**：开源、支持 Web UI、可配置项目级规则、能执行本地文件操作。

## 安装和配置过程

1. 安装 Node.js（版本 ≥ 18）。
2. 通过 npx 启动 Web UI：
   npx @deepseek-ai/dsh web
3. 在 Web 界面中配置 DeepSeek API Key。
4. 选择工作区为本地 Git 仓库目录。
5. 确认 Agent 可正常读写工作区文件。
6. 可网页直接安装

## 交给它的任务

1. 只读任务：阅读当前仓库，不要修改任何东西，简单介绍仓库内容。
2. 修改任务：整理 README.md —— 理顺标题层级、增加目录小节、统一代码块语言标注。

## Agent 做了哪些修改

- 仅修改了 README.md 文件。
- 将一级标题 # git笔记 改为了二级标题 ## git 笔记。
- 删除了原有无实质内容的“用于焦糖工作室”。
- 在开头新增了引用块，补充了仓库用途、远端仓库地址和主分支信息。
- 新增了「目录」小节，列出了常用命令、概念说明、操作流程等索引。
- 未修改其他文件。

## git diff 中看到了什么

执行 git diff 后，输出如下：
```diff
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
diff --git a/README.md b/README.md
index 7bf99a3..d1d6da6 100644
--- a/README.md
+++ b/README.md
@@ -1,20 +1,64 @@
-# git笔记
+## git 笔记
 
-用于焦糖工作室
+> 焦糖工作室的 git 学习笔记：把常用的命令和概念记下来，忘了就回来翻一翻。
+
+**仓库用途:** 记录 git 的常用操作与个人理解
+**远端仓库:** <https://github.com/mcc409/git-.git>
+**主分支:** `main`
+
+## 目录
+
+- [常用命令](#常用命令)
+- [概念说明](#概念说明)
+- [操作流程](#操作流程)
+- [本仓库文件说明](#本仓库文件说明)
+
 ## 常用命令
-- **git status**: 查看当前状态（看看哪些文件被修改了，哪些还没提交）。
-- **git add**: 把修改过的文件添加到暂存区（相当于把文件放进购物车）。
-- **git commit**: 把暂存区的文件提交到本地仓库，并生成一个版本记录（相当于结账存档，并且可以写备注）。
-- **git diff**: 查看文件具体修改了哪些内容。
```

如果 git diff 没有输出，说明 Agent 未修改任何文件，或改动已被提交。此时应检查 git status 与 git log。

## 最终结果是否符合预期

-  符合预期：README 结构更清晰，改动范围可控。
- 通过 git diff 完整审计了 Agent 的修改，未发现意外改动。