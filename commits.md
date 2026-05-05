---
title: Commit 规范
author: XinHallow
---

> [!important]
> 此文档与 [Conventional Commits](https://www.conventionalcommits.org) 具有相似性，但需要注意不同
>
> 本文档仅为团队内部贡献提交指南，其他项目/团队请遵从其指南

# 通用格式

通用格式：`<type>(<content>): <message>`

其中，`type`、`content` 与 `message` 是必须要填写的部分

---

`type`：提交类型，可用的有：

- `fix` 修复了漏洞
- `feat` 添加了新的功能
- `deps` 添加或更新了依赖项
- `build` 构建流程修改
- `ci` CI/CD 流程修改
- `chore` 杂项
- `docs` 文档更新
- `style` 格式更新
- `refactor` 代码重构
- `perf` 增加性能
- `test` 套件更新

如果涉及到破坏性更改，请在 `<content>` 的括号后添加英文半角感叹号：`!`，如：

```text
feat(component(Hero))!: Remove unnecessary links
```

---

`message`：Commit 提交信息，使用祈使语气，保持现在时（英文可用 `Fix`/`Add`，中文直接用`修复`/`添加`等动词开头）。
英文需要开头小写，中文或英文的结尾都不需要句号。如果更新内容较多，建议分批次提交，否则请在新行后添加修改内容，如：

```text
feat(component(authentication)): 修复 push 到主分支时不会运行测试的问题

- 移除认证组件
- 从 Supabase 迁移到 Convex 后端
- 使用 WorkOS 认证组件
```

---

`content`：修改内容或修改的领域（domain），可用半角逗号分隔（逗号后不需要空格）

以下为建议的内容：

| Content                      | Domain     | Description               |
|------------------------------|------------|---------------------------|
| `helmfile(<item>)`           | kubernetes | 修改 helmfile               |
| `values(<item>)`             | kubernetes | 修改部署用 values              |
| `helm(<item>)`               | kubernetes | 修改 helm chart             |
| `<filename>`                 | general    | 修改的文件名                    |
| `component(<componentname>)` | frontend   | 修改组件                      |
| `component(<componentname>)` | nestjs     | 修改组件（如 module，provider 等） |

`content` 字段填写具体的修改对象，按照表格中的模式（如 `values(ingress-nginx)`、`helmfile(cilium)`）。
若涉及多个对象，使用半角逗号分隔且不加空格（例如 `foo.rs`,`bar.rs`）。

# GitHub 特殊部分

除此之外，如果在 GitHub 上提交贡献，如修复 Issue，请在提交内容后，添加空格和 `(fix: #<issue>)`，如下：

```text
fix(values(cilium)): 修复 cilium 的错误 api 服务器地址 (fix: #1)
```
