# underthere's skills

我的个人 agent skills 仓库，结构参考 [mattpocock/skills](https://github.com/mattpocock/skills)，可以作为 Claude Code plugin 安装，也可以通过 symlink 直接使用。

## 仓库结构

```
.claude-plugin/
  plugin.json        # plugin 清单，列出要发布的 skills
  marketplace.json   # 让这个仓库本身可以作为 marketplace 被添加
skills/
  <skill-name>/
    SKILL.md         # skill 本体：frontmatter (name/description) + 指令
    *.md             # 可选的支持文档，SKILL.md 里按需引用（渐进式披露）
    agents/
      openai.yaml    # 给 Codex 等非 Claude harness 的界面元数据
scripts/
  link-skills.sh     # 把所有 skills symlink 到 ~/.claude/skills 和 ~/.agents/skills
  list-skills.sh     # 列出仓库里的所有 skills
```

## 安装

**方式一：作为 Claude Code plugin（推荐）**

```bash
claude plugin marketplace add /Users/underthere/repos/skills
```

然后在会话内执行 `/plugin install underthere-skills@underthere`。推送到 GitHub 后，把路径换成 `<github-user>/skills` 即可远程添加。

**方式二：symlink（适用于 Codex 等其他 harness）**

```bash
bash scripts/link-skills.sh
```

之后 `git pull` 即可保持更新，无需重新链接。两种方式二选一，同时用会导致每个 skill 出现两次。

## 添加新 skill

1. 新建 `skills/<skill-name>/SKILL.md`，frontmatter 里写 `name` 和 `description`。`description` 决定模型何时自动触发，写清楚"做什么 + 什么时候用"。
2. 把路径加进 [.claude-plugin/plugin.json](.claude-plugin/plugin.json) 的 `skills` 数组。
3. 重新安装 plugin 或重跑 `scripts/link-skills.sh`。

现有 skill 可以作为模板：[skills/commit-message/SKILL.md](skills/commit-message/SKILL.md)。

## Skills

- **[commit-message](skills/commit-message/SKILL.md)**: 根据已暂存的 diff 起草 commit message，优先遵循仓库自身的历史风格，无明显风格时回退到 Conventional Commits。
