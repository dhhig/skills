# dhhig/skills · 我的 AI 技能包

把可复用的「提示词工程」经验固化成 Skill，随取随用。
当前收录 **1** 个技能：Seedance 2.5 视频提示词优化大师。

---

## 🚀 安装

### 方式一：skills CLI（推荐）

> 需要能连 GitHub（github.com 443）。国内网络若克隆超时，用方式二或配好代理。

```bash
# 只看仓库里有哪些 skill
npx skills add dhhig/skills --list

# 安装全部（自动检测项目级 / 全局）
npx skills add dhhig/skills

# 只装某一个
npx skills add dhhig/skills --skill seedance2.5-master-prompt

# 全局安装
npx skills add dhhig/skills -g
```

### 方式二：DeepSeek Harness（DSH）

```bash
git clone https://github.com/dhhig/skills /tmp/dhhig-skills
mkdir -p ~/.dsh/skills
cp -R /tmp/dhhig-skills/skills/* ~/.dsh/skills/
```

然后在 DSH 中 `/reload`。

### 方式三：手动复制

把 `skills/<技能名>/` 整个目录拷到你的 agent 技能目录即可。每个技能都是自包含的：`SKILL.md` + `references/`。

---

## 📦 技能列表

| 技能 | 一句话 | 输入 → 输出 |
|---|---|---|
| [**seedance2.5-master-prompt**](./skills/seedance2.5-master-prompt/) · [SKILL.md](./skills/seedance2.5-master-prompt/SKILL.md) | Seedance 2.5 视频提示词优化大师 | 小说片段 / 一句剧情 / 几个主题词 → 4–30s 多镜头视频提示词 |

### seedance2.5-master-prompt

把一段文本设计成 **4–30s 的连续镜头脚本**，输出为**一条**可直接复制进 Seedance 2.5 的多镜头提示词：

- 头部锚定 `主体 / 场景 / 音乐`，正文按 `镜头N ｜ 时间区间 ｜ …` 顺序排列
- 先确认资产：有图 → `@图片N` 锚定、不写 T2I；无图 → 完整主体档案 + 场景锚点
- 镜头数由故事节奏决定（30s 通常 8–14 镜），每镜时长之和 = 总时长
- 只写画面：不写音效、不写叙事意图；每镜必须有强动词 + 运镜 + 时间内变化
- 输出 ≤4000 字，违禁词自动替换，交付前逐项质检

**参考文件**

- [`references/templates.md`](./skills/seedance2.5-master-prompt/references/templates.md) — 输出模板 + 范例 + 镜头数决策 + 风格/运镜/光线词库
- [`references/examples.md`](./skills/seedance2.5-master-prompt/references/examples.md) — 官方手册案例库（写实/广告/打斗/科幻/一镜到底/故事板/短剧/超长片）

---

## 🧭 目录约定

```
skills/
└── <技能名>/
    ├── SKILL.md        # 必需：YAML frontmatter（name + description）+ 工作流
    ├── README.md       # 可选：给人看的说明
    └── references/     # 可选：模板、示例、词库
```

新增技能只需新建 `skills/<技能名>/SKILL.md`，`name` 用 kebab-case 且与目录名一致。

## 📄 License

个人技能包，仅供学习与个人创作使用；转载或商用请先联系作者。
