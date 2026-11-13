# 安装与使用

## 1. skills CLI

要求 Node.js 18+。

```bash
npx skills add dhhig/skills --list              # 列出仓库内所有 skill
npx skills add dhhig/skills --skill seedance2.5-master-prompt
npx skills add dhhig/skills -g                  # 全局安装
npx skills add dhhig/skills -a claude-code      # 指定安装到某个 agent
```

## 2. DeepSeek Harness

```bash
git clone https://github.com/dhhig/skills /tmp/dhhig-skills
mkdir -p ~/.dsh/skills
cp -R /tmp/dhhig-skills/skills/* ~/.dsh/skills/
```

`~/.dsh/skills` 不存在时先手动创建，再重启 DSH 或 `/reload`。装好后在输入框输入 `/seedance2.5-master-prompt`，或直接描述任务（"帮我写一条 Seedance 2.5 多镜头提示词"）。

## 3. 手动复制

任意 agent 的技能目录，放入：

```
<skill-dir>/seedance2.5-master-prompt/SKILL.md
<skill-dir>/seedance2.5-master-prompt/references/...
```

## 4. 怎么用这个技能

1. 给它输入：小说片段 / 一句剧情 / 几个主题词。
2. 它会先确认**总时长**（未指定时问你要 4–30s 里的哪个值）和**资产情况**（有没有参考图/视频/音频）。
3. 输出三段：**【脚本总览】**（叙事与镜头设计依据）、**【资产说明】**（@ 引用或完整档案 / T2I）、**【视频提示词】**（单一完整可复制块）。
4. 整块复制进 Seedance 2.5 生成即可。

## 5. 常见问题

| 问题 | 处理 |
|---|---|
| 没图能做吗 | 能。无图时技能会先写完整主体档案 + 场景锚点；需要资产图再附 T2I 提示词 |
| 有图但人物总变 | 把图作为 `@图片N` 资产上传，并在提示词里保留技能给出的 `@图片N 是 主体短名` 声明 |
| 生成结果动作做不完 | 单镜动作太多；减少该镜动作数量，或把长镜拆成两镜 |
| 想要特定风格 | 明确说"风格：xxx"；不指定时技能默认不写风格词，只在交付时推荐 1–3 种 |
| 超过 30s | 技能会按 30s 收敛，或建议拆成多条生成再剪 |
