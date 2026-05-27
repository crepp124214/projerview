# projerview

帮助计算机应届生深度理解简历项目、生成面试准备材料、进行模拟面试的 Agent Skill。

遵循 [Agent Skills 规范](https://agentskills.io)，支持 Claude Code、OpenAI Codex、Trae 等所有兼容客户端。

## 解决什么问题

简历上的项目不是自己做的，面试时心虚？不知道面试官会怎么深挖？不知道怎么用面试官能听懂的方式讲解项目？

projerview 通过三阶段闭环解决这些问题：

1. **分析你的项目代码** → 生成面试手册，让你真正理解项目
2. **生成面试题库** → 提前预习可能被问到的问题
3. **模拟面试** → 实战练习，逐题评分、追问、反馈

## 安装

### 一行命令安装（推荐）

```bash
npx skills add crepp124214/projerview
```

> `npx skills add` 会自动检测你本地安装的 AI 编程工具（Claude Code、Cursor、Trae 等），一键同步配置到对应目录。

### 按平台安装

#### Claude Code

```bash
# 方式一：npx 一键安装（推荐）
npx skills add crepp124214/projerview

# 方式二：Claude Code 内置安装器
$skill-installer crepp124214/projerview

# 方式三：手动安装
git clone https://github.com/crepp124214/projerview.git
cp -r projerview ~/.claude/skills/projerview
```

安装后重启 Claude Code，输入 `/projerview` 即可启动。

#### OpenAI Codex

```bash
# 方式一：npx 一键安装（推荐）
npx skills add crepp124214/projerview

# 方式二：手动安装
git clone https://github.com/crepp124214/projerview.git
cp -r projerview ~/.agents/skills/projerview
```

安装后重启 Codex，输入 `$projerview` 即可启动。

#### Trae

```bash
# 方式一：npx 一键安装（推荐）
npx skills add crepp124214/projerview

# 方式二：手动安装
git clone https://github.com/crepp124214/projerview.git
# 将 projerview/ 目录复制到 .trae/skills/ 下
```

安装后在对话中输入 `projerview` 即可启动。

#### Cursor / VS Code / 其他兼容客户端

```bash
npx skills add crepp124214/projerview
```

或手动将 `projerview/` 目录复制到对应客户端的 Skills 目录下。

### 验证安装

对 AI 编程助手说 `projerview`，如果 Skill 正常响应预检流程，说明安装成功。

## 快速开始

在你的项目目录下，对 AI 编程助手说：

```
projerview
```

Skill 会自动检测进度，从你上次停下的地方继续。首次使用会从项目分析开始。

## 使用方式

| 命令 | 说明 |
|------|------|
| `projerview` | 自动检测进度，从断点继续 |
| `projerview analyze` | 重新分析项目代码，生成面试手册 |
| `projerview question-bank` | 重新生成面试题库 |
| `projerview mock-interview` | 直接进入模拟面试 |
| `面试准备` / `模拟面试` | 中文触发词 |

## 三阶段流程

### 阶段1：项目深度分析

深度分析你的项目代码，生成面试手册 `.projerview/handbook.md`。

分析维度：项目一句话介绍、项目概览、架构解析、核心模块详解（含测试覆盖分析）、技术亮点、技术选型对比、难点与解决方案、可优化点。支持选择话术风格（口语自然/简洁干练/学术严谨）。

分析完成后会暂停让你审阅，确认无误后再继续。

### 阶段2：题库生成

基于面试手册，生成面试题库 `.projerview/question-bank.md`。

核心题库 25-35 题，扩展题库不限。难度分层：⭐基础 ~15% / ⭐⭐中等 ~60% / ⭐⭐⭐进阶 ~25%。每道题附带口语化参考答案、常见追问、关联八股文知识点，并按面试阶段（自我介绍→项目深挖→技术基础→场景题→反问）分类速查。

### 阶段3：模拟面试

Skill 扮演面试官，逐题提问、评分、追问。四种模式：全量/专题/随机/压力面试。评分维度：准确性(40%) + 深度(35%) + 表达(25%)。支持暂停保存进度、历史成绩对比、断点续面。面试结束后生成评价报告。

## 产出文件

所有文件保存在项目目录下的 `.projerview/` 中，自动加入 `.gitignore`。

## 安全与隐私

- 自动过滤敏感信息（API Key、数据库连接串、密码等）
- 面试材料自动加入 .gitignore
- 如果项目涉及公司机密代码，建议在个人设备上使用，并注意 AI 平台的数据处理政策

## 适用项目

Python / Java / Node.js / Go / Rust / C# / Ruby 及其他主流项目。支持 Monorepo。

## 常见问题

**Q: 分析一个项目需要多长时间？**
A: 小型项目约2-3分钟，中型约5-8分钟，大型可能10分钟以上。

**Q: 支持多语言混合项目吗？**
A: 支持。自动识别 Monorepo，分别分析前后端子项目。

**Q: 题库会生成多少题？**
A: 核心题库 25-35 题，扩展题库不限。全量面试约需 1-1.5 小时。

**Q: 面试中途中断了怎么办？**
A: 说"暂停"保存进度，下次运行 `projerview` 会自动检测并提示续面。

## 版本日志

### v1.1.0 (2026-05-27)
- **压力面试模式**：模拟高压环境，追问更犀利、可打断冗长回答、质疑式追问，锻炼抗压能力
- **面试复盘与历史对比**：多次面试自动对比成绩，生成进步/退步分析，报告按时间戳归档
- **八股文关联**：每道题标注可能引出的基础知识追问，项目题与八股文串联复习
- **按面试阶段速查**：题库新增面试流程维度分类（自我介绍→项目深挖→技术基础→场景题→反问）
- **测试代码分析**：analyze 阶段自动扫描测试文件，提取边界 case，评估测试覆盖度
- **话术风格选择**：支持口语自然型、简洁干练型、学术严谨型三种话术风格

### v1.0.0 (2026-05-17)
- 初始版本
- 三阶段流程：项目分析 → 题库生成 → 模拟面试
- 遵循 Agent Skills 规范，支持 Claude Code / Codex / Trae

## 文件结构

```
projerview/
├── SKILL.md                  # Skill 入口（Agent Skills 规范）
└── references/               # 阶段详细指令
    ├── analyze.md            # 阶段1：项目深度分析
    ├── question-bank.md      # 阶段2：题库生成
    └── mock-interview.md     # 阶段3：模拟面试
```
