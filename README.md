# Commit Plugin for Claude Code

基于 Claude Code 的自动提交信息生成与提交插件，可根据代码变更生成符合规范的提交信息。

## 功能特性

- **自动生成提交信息**：分析暂存区的代码变更，生成符合规范的提交信息
- **多语言支持**：支持中文和英文提交信息生成
- **交互式确认流程**：提供多种确认选项，确保提交信息准确无误
- **遵循最佳实践**：基于 Google 工程实践中的 CL 描述规则生成高质量的提交信息
- **灵活的编辑方式**：支持自动生成、用户编辑或手动修改提交信息

## 使用示例

在 Claude Code 中调用 commit 技能：

```
/commit-plugin:commit
```

或指定语言：

```
/commit-plugin:commit <english/chinese>
```

## 参考

- [Google Engineering Practices - CL Descriptions](https://github.com/google/eng-practices/blob/master/review/developer/cl-descriptions.md)
