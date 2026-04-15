---
name: commit
description: Automatically generate commit messages based on code changes, and commit your changes.
disable-model-invocation: true
allowed-tools: Read Write Bash
---

## Parameters

- language: commit message language (chinese/english)

## Changes Context

- context-status:

```!
  git diff --cached --quiet
  echo $?
```

- context-diff: !`git diff --staged`

## Generate git commit message （使用 $ARGUMENTS 作为语言，默认语言 chinese 简体中文）

1. 根据 context-status 判断 stage 区域是否有内容，为 0 表示无内容，1 表示有内容。无内容则放弃本次提交，并提示用户“没有可提交的变更”
2. Use cl-descriptions.md in this skill directory for the commit message rules
3. Generate commit message based on context-diff
4. 将 commit message 输出，并**使用 AskUserQuestion 工具**向用户显示以下选择：

- 确认（直接提交）
- 继续修改（提供修改建议）
- 用户自行修改
- 取消

4. 根据用户的选择：

- 确认 - 直接提交
- 继续修改 - 重新生成 commit message，返回第 3 步
- 用户自行修改 - 创建临时文件 `.commit_message`，将已生成的 message 写入其中，执行 `code --wait .commit_message` 打开 VS Code 让用户编辑，文件关闭后自动读取内容、执行 git commit 并删除临时文件
- 取消 - 结束工作流，不提交
