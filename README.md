# LXTI 旅行人格测评


[![Stars](https://img.shields.io/github/stars/Leowu9839/=social)](https://github.com/Leowu9839/lxti-travel-personality/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 🏠 这是 [Leo's AI Skill Workshop](https://github.com/Leowu9839/leos-workshop) 的 6 大 Skill 之一，点击查看完整项目集。
> 原创文旅社交测评工具 · 16 型唯一人格 · 动态自适应出题 · 专属头像 + 定制攻略

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Codex%20%7C%20Claude%20%7C%20Cursor%20%7C%20Trae-blue)]()

---

## ⚡ 安装

```bash
git clone https://github.com/Leowu9839/lxti-travel-personality.git
cp -r lxti-travel-personality ~/.codex/skills/
```

支持平台：**Codex CLI** / **Claude Code** / **Cursor** / **Trae** —— 放到对应 skills 目录重启即可。

---

## 🎯 这是什么

市面上旅行攻略千篇一律——"3 天玩遍 XX""必打卡 10 大景点"。问题不在攻略本身，而在**它不知道你是谁**。

LXTI 用 8-20 道互斥选择题测出你的旅行人格，然后给你：
- 🧬 **16 型唯一人格报告**——你是什么旅行生物
- 🎨 **专属头像**——16 张预生成 Q 版插画，直接拿去做社交头像
- 🗺️ **定制旅行攻略**——按你的人格生成，不是按城市生成

---

## 🧬 四大维度

| 维度 | 名称 | A 端 | B 端 |
|------|------|------|------|
| L / E | 社交 | L 独处治愈型 | E 轻社交融入型 |
| X / T | 节奏 | X 松弛慢游型 | T 紧凑高效型 |
| S / I | 体验 | S 景观视觉出片 | I 人文深度沉浸 |
| I / H | 舒适 | I 舒适省心优先 | H 探索抗压能吃苦 |

4 × 2 × 2 × 2 = **16 种唯一人格**

---

## 👥 16 型人格速览

| 编码 | 人格名称 | 一句话 |
|------|---------|--------|
| LXSI | 旷野充电独行侠 | 独行山野，充电即自由 |
| LXII | 古村躺平摆烂仙 | 古镇橘猫一杯茶，摆烂即正义 |
| LXSH | 野地秘境探险家 | 无人之境才是目的地 |
| LXIH | 人文佛系独行僧 | 寺庙石柱旁，宁静致远 |
| LTSI | 高效赏景效率怪 | 日出前就位，快门即正义 |
| LTII | 人文速通通关机 | 博物馆就是我的副本 |
| LTSH | 山野疯跑运动猿 | 森林步道全速冲刺 |
| LTIH | 古迹单刷内卷皇 | 古遗迹群是我的战绩榜 |
| EXSI | 躺平看景咸鱼瘫 | 躺椅鸡尾酒，海边即天堂 |
| EXII | 市井闲逛烟火民 | 小吃街就是我的星辰大海 |
| EXSH | 山川追风漫游者 | 风在发梢，路在脚下 |
| EXIH | 烟火慢逛体验师 | 蹲在匠人摊位前忘了时间 |
| ETSI | 网红打卡突击兵 | 打卡点就是勋章墙 |
| ETII | 走街串巷逛吃控 | 夜市是我的自助餐厅 |
| ETSH | 热衷开图先锋官 | 地图上没标的地方才想去 |
| ETIH | 人文带队全能王 | 古镇分叉路口，跟我走 |

---

## 🔬 设计亮点

- **动态自适应出题**：你越清楚要什么，题越少（最少 8 题）；越模糊，题越多（最多 20 题）
- **互斥选项逼出真实偏好**：没有「都可以」，必须二选一
- **90% 标准化 + 10% 个性化**：同人格核心结论一致（公信力），细节微调（专属感）
- **末尾开放式补全**：测评结束给你自述特殊偏好的机会
- **年轻化命名，自带社交货币**：拒绝文艺假高级，滑稽自嘲有画面感

---

## 🎨 关于头像

`avatars/` 目录包含 16 张预生成的 Q 版人格头像（PNG），可**直接用作社交头像**。

如果你的 AI 底层模型不支持图像生成（如 Deepseek），可使用 `LXTI_avatar_prompts.md` 中的提示词，丢给任何支持生图的工具（Midjourney / DALL·E / 通义万相）重新生成。

---

## 🚀 触发方式

在 AI 对话中说：
- 「帮我测一下旅行人格」
- 「我想出去玩但不知道去哪」
- 「给我推荐个旅行攻略」

Skill 自动触发，开始动态出题。

---

## 📂 文件结构

```
lxti-travel-personality/
├── SKILL.md                  # 核心测评逻辑（AI 执行规范）
├── LXTI_avatar_prompts.md    # 16 型头像绘画提示词库
├── config/
│   ├── personalities.json    # 16 型人格定义数据
│   └── question_bank.json    # 动态出题题库
├── scripts/
│   └── scoring_logic.md      # 四维评分算法
├── avatars/                  # 16 张预生成头像（PNG）
├── README.md
└── LICENSE
```

---

## 📄 许可

MIT License · 欢迎使用、修改、分发。

测出来你是什么人格？欢迎提 Issue 分享 🧳

---

*Made with ❤️ for travelers who refuse generic itineraries.*

---

## 🔗 相关项目

这是 [Leo's AI Skill Workshop](https://github.com/Leowu9839/leos-workshop) 的一部分，更多 Skill：

| Skill | 场景 |
|:---|:---|
| 🏛️ [制度顾问](https://github.com/Leowu9839/policy-counsel) | 企业合规 / 政策分析 |
| 🐕 [数据宝藏猎犬](https://github.com/Leowu9839/data-treasure-hound) | 数据调研 / 信息挖掘 |
| ⚙️ [工程化 Agent](https://github.com/Leowu9839/engineering-agent) | 开发提效 / 自动化 |
| 💎 [富人生活顾问](https://github.com/Leowu9839/luxury-experience-designer) | 生活方式 / 品质提升 |
| ✈️ [LXTI 旅行人格](https://github.com/Leowu9839/lxti-travel-personality) | 旅行规划 / 人格测试 |
| 🔍 [拆穿 Skill](https://github.com/Leowu9839/deconstruct-skill) | 批判思维 / 信息甄别 |