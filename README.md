# NGSL-DICTIONARY-GPT

![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)
![MkDocs](https://img.shields.io/badge/Docs-MkDocs-526CFE?logo=markdown&logoColor=white)
![Theme](https://img.shields.io/badge/Theme-ReadTheDocs-0F172A)
![License](https://img.shields.io/badge/License-CC--BY--SA--4.0-lightgrey)

一个面向中文学习者的 **NGSL 高频英语词汇学习文档项目**：

- 以 `ngsl_src/day_001.csv ~ day_113.csv` 为数据源；
- 以 `docs/day_001.md ~ day_113.md` 为学习内容载体；
- 使用 MkDocs 构建并通过 GitHub Pages 自动部署；
- 目标是更贴近日常英语使用场景，而不是考试导向词表。

---

## 为什么做这个项目

本项目灵感来自 [Ceelog/DictionaryByGPT4](https://github.com/Ceelog/DictionaryByGPT4.git)。

原项目覆盖了中考/高考/四六级等体系下的 8000+ 词汇，偏向考试与学术语境。

但很多学习者都会遇到同一个问题：
**背了很多词，真实交流时却“不常用”**。原因不在努力，而在词表顺序——中国应试体系强调“考试识别与学术阅读”，而英语母语者的日常沟通更依赖一组高频通用词。

因此，这个仓库把核心目标改成：

- **先掌握日常高频词，再扩展考试/专业词**；
- 用更少的词覆盖更高比例的日常输入与输出场景；
- 通过结构化文档持续沉淀可复习、可检索、可迭代的词汇内容。

### 学习路径对比（核心）

| 维度 | 中国应试词汇路径（常见） | NGSL 路径（本项目） |
|---|---|---|
| 目标优先级 | 考试成绩、题型覆盖 | 日常沟通、真实语境覆盖 |
| 词汇规模 | 通常更大（常见 8000+） | 更聚焦（约 2800 词级别） |
| 语境侧重 | 学术、书面、测试语料 | 通用、生活、媒体与工作日常 |
| 学习体感 | 词多且分散，迁移慢 | 高频集中，见词率高，反馈快 |
| 推荐顺序 | 常直接全量推进 | 先高频核心，再专项进阶 |

> 这不是“应试词汇无用”，而是把顺序调整为：**先会用，再做深**。

## NGSL 是什么？

NGSL（New General Service List，新通用英语词表）由 **Charles Browne、Brent Culligan、Joseph Phillips** 团队发布（2013），是对 Michael West 于 1953 年 GSL 的现代化更新。

### 核心要点（聚焦“日常实用”）

- **它不是“冷门大词表”**，而是优先收录英语真实使用中最常见、最有复用价值的词；
- **语料基础**：来自大规模现代英语语料（官方说明常提到 Cambridge English Corpus 的 2.73 亿词级别子集）；
- **词量策略**：用约 2800 词级别（版本口径 2801/2802/2809）追求更高通用覆盖；
- **覆盖效果**：对一般英语文本可达约 **92%+**，适合作为“先学会用”的第一层词汇；
- **版本演进**：1.0 → 1.01 → 1.2（2023 起主版本），持续根据研究与反馈迭代。

### 为什么它适合这个仓库

如果你的目标是“和英语母语者的真实日常语言更接轨”，NGSL 的优势非常直接：

- 先抓住高频核心词，聊天、阅读、听力的“见词率”更高；
- 更贴近日常交流、通识内容和轻职场语境，而非单纯应试题库；
- 后续再叠加学术/考试词汇时，理解与记忆成本更低。

---

## 项目结构

```text
NGSL-DICTIONARY-GPT/
├─ docs/                  # MkDocs 文档目录（day_001.md ~ day_113.md）
├─ ngsl_src/              # 词表源数据（day_001.csv ~ day_113.csv）
├─ .github/workflows/
│  └─ deploy-docs.yml     # GitHub Pages 自动部署工作流
├─ mkdocs.yml             # MkDocs 配置（readthedocs 主题）
├─ requirements.txt       # Python 依赖
└─ README.md
```

## 提示词

本项目提示词为开源思路，基于 [Ceelog/DictionaryByGPT4](https://github.com/Ceelog/DictionaryByGPT4.git) 进行二次改造，重点适配 NGSL 词表与文档化产出。模型采用`GPT-5.3-Codex`。

### 生成提示词
下面的提示词生成了这个项目
```markdown
0. 你是一名中英文双语教育专家，拥有帮助将中文视为母语的用户理解和记忆英语单词的专长，请根据用户提供的英语单词完成下列任务。
1. 用mkdocs创建项目文档的框架，每个markdown文档的单词数量和文件名与`ngsl_src`文件夹下的每一个csv文件保持一致，比如day_001.csv对应day_001.md
2. 每个markdown文件里面的具体内容，需要手动编写输出内容，绝对不能借助脚本或者使用脚本一键生成垃圾内容，内容生成顺序严格按照序号来进行编写，比如先创建文件day_001.md然后编写相应的内容，然后创建day_002.md 以此类推，直到完整生成`ngsl_src`下所有对应内容为止。每个day_xxx.md中的每个单词内容框架与具体要求如下，并确保单个文件中没有缺失的单词。
{
# day_xxx
## ${具体的单词}
单词元数据
Lemma：
SFI Rank：
SFI：
Adjusted Frequency per Million (U)：

### 分析词义
- 系统地分析用户提供的英文单词，并以简单易懂的方式解答；

### 列举例句

- 根据所需，为该单词提供至少 3 个不同场景下的使用方法和例句。并且附上中文翻译，以帮助用户更深入地理解单词意义。

### 词根分析

- 分析并展示单词的词根；
- 列出由词根衍生出来的其他单词；

### 词缀分析

- 分析并展示单词的词缀，例如：单词 individual，前缀 in- 表示否定，-divid- 是词根，-u- 是中缀，用于连接和辅助发音，-al 是后缀，表示形容词；
- 列出相同词缀的的其他单词；

### 发展历史和文化背景

- 详细介绍单词的造词来源和发展历史，以及在欧美文化中的内涵

### 单词变形

- 列出单词对应的名词、单复数、动词、不同时态、形容词、副词等的变形以及对应的中文翻译。
- 列出单词对应的固定搭配、组词以及对应的中文翻译。

### 记忆辅助

- 提供一些高效的记忆技巧和窍门，以更好地记住英文单词。

### 小故事

- 用英文撰写一个有画面感的场景故事，包含用户提供的单词。
- 要求使用简单的词汇，100 个单词以内。
- 英文故事后面附带对应的中文翻译。

## ....下一个单词
### ......
}
3. 生成完全部markdown文件后，用mkdocs进行部署，mkdocs主题采用默认的readthedocs，编写相应的GitHub workflow，以git push状态作为触发源

### 润色提示词
下面的提示词用于进一步润色
```markdown
# Role
你是一位拥有多年教学经验的英语词汇学导师。你的目标是为普通学生（涵盖高中生、大学生及英语自学者）编写高质量、易吸收的开源词汇学习笔记。

# Task
我将提供一份基于特定单词的词汇学习笔记（Markdown格式）。请你**保持我原有的所有标题和排版结构完全不变**，仅对每个标题下的文本内容进行深度优化、润色和扩写。

# Guidelines (内容优化策略)

1. 【分析词义】与【列举例句】：
   - 释义要准确、全面，符合权威词典（如牛津、朗文）的定义。
   - 例句必须贴近**校园生活、日常交流、阅读理解或通用写作场景**（例如：考试、旅行、交友、社会现象等）。
   - 坚决避免任何偏门的技术、工程或特定行业的专业黑话。句子要地道且具有模仿价值，适合学生积累用作写作素材。

2. 【词根分析】与【词缀分析】：
   - 有明确词根词缀的，提供清晰、容易记忆的拆解，并顺带提一下同源词（举一反三）。
   - 对于无法拆解的简单基础词（如 knife, ocean, bite），放弃生硬的词源解释，直接替换为**“考试高频搭配 (Collocations)”** 或 **“常用地道习语 (Idioms)”**（例如：a drop in the ocean 沧海一粟）。

3. 【发展历史和文化背景】：
   - 介绍该单词在英语国家文化中的有趣背景、引申含义，或者在不同语境下的感情色彩变化，增加学习的趣味性。

4. 【记忆辅助】：
   - 提供一个巧妙的助记方法（可以是谐音、联想画面、逻辑推导等）。一句话即可，要能瞬间在大脑中建立画面的那种。

5. 【小故事】：
   - 写一段 1-2 句话的微型生活情境小故事。
   - 场景需日常且有代入感（如：期末复习、朋友聚餐、假期旅行等）。
   - 中英文对照，英文使用纯正、地道的 Standard English，时态和语法严谨，适合学生作为口语或语感的练习素材。

# Input
请优化下面的文件
day_001.md
```
## 本地使用
有虚拟环境尽量激活虚拟环境
### 1) 安装依赖

```bash
pip install -r requirements.txt
```

### 2) 本地预览

```bash
mkdocs serve
```

### 3) 严格构建

```bash
mkdocs build --strict
```


## 参考文献与链接

- [Ceelog/DictionaryByGPT4](https://github.com/Ceelog/DictionaryByGPT4.git)
- [MkDocs 官方仓库](https://github.com/mkdocs/mkdocs)
- [MkDocs 官方文档](https://www.mkdocs.org/)
- [Material for MkDocs](https://github.com/squidfunk/mkdocs-material)
- [NGSL 官方项目（.org）](https://www.newgeneralservicelist.org/home)
- [NGSL 官方项目（.com）](https://www.newgeneralservicelist.com/new-general-service-list)

## 许可证

本仓库采用 [CC BY-SA 4.0](./LICENSE)。

在引用、改编和二次分发内容时，请遵守署名与相同方式共享条款。