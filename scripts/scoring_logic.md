# LXTI 旅行人格测评 · 判定逻辑说明

## 1. 计分规则

每个核心维度（LE / XT / SI / IH）独立计分：

- 用户每选一项，根据 `question_bank.json` 中的 `scores` 为该维度两侧分别加分。
- 例如：某题选 A（L+2, E+0），则 L 侧加 2 分，E 侧加 0 分。

## 2. 维度判定

四个维度分别比较两侧总分，高分侧为判定结果：

| 维度 | 选项 A | 选项 B | 判定规则 |
|------|--------|--------|----------|
| LE | L（独处治愈型） | E（轻社交融入型） | L_score > E_score ? L : E |
| XT | X（松弛慢游型） | T（紧凑高效型） | X_score > T_score ? X : T |
| SI | S（景观视觉出片） | I（人文深度沉浸） | S_score > I_score ? S : I |
| IH | I（舒适省心优先） | H（探索抗压能吃苦） | I_score > H_score ? I : H |

**平局处理**：若两侧得分相等，优先采用用户开放题（第 10 步）中的自我描述进行人工判断；若无明确倾向，默认取 **L、X、S、I**（保守/舒适侧）。

## 3. 人格匹配

将四个维度的判定结果组合成 4 位编码，在 `personalities.json` 中精确匹配：

```python
personality_code = le_result + xt_result + si_result + ih_result
# 例如：L + X + S + I = "LXSI"
```

AI **严禁自创**编码，必须在 `personalities.json` 的 `code` 字段中精确查找。

## 4. 个性化微调（10%）

匹配到固定人格后：

1. **90% 固定内容**：直接复用 `personalities.json` 中的 `core_definition`、`travel_preferences`、`advantages`、`disadvantages`、`suitable_playstyles`、`tags`。
2. **10% 个性化**：在报告末尾追加一段「✧ 给你的专属解读」（≤150 字），仅结合用户在答题和开放题中提到的：
   - 具体目的地偏好
   - 特殊习惯/禁忌
   - 开放题补充说明

## 5. 辅助题（SP / TP / FP）用途

辅助题不计入四维得分，仅用于：
- 攻略定制时的预算分配、住宿档次、餐饮优先级
- 目的地推荐时的季节/人流过滤
- 避雷清单生成

## 6. 代码化判定示例（Python 伪代码）

```python
def judge_personality(answers: list[dict]) -> str:
    scores = {"L":0, "E":0, "X":0, "T":0, "S":0, "I_exp":0, "I_com":0, "H":0}
    
    for ans in answers:
        q = find_question(ans.question_id)
        opt = q.options[ans.selected_index]
        for dim, val in opt.scores.items():
            scores[dim] += val
    
    le = "L" if scores["L"] >= scores["E"] else "E"
    xt = "X" if scores["X"] >= scores["T"] else "T"
    si = "S" if scores["S"] >= scores["I_exp"] else "I"
    ih = "I" if scores["I_com"] >= scores["H"] else "H"
    
    return le + xt + si + ih
```

> **注意**：代码中维度③的 I（体验维度）建议记为 `I_exp`，维度④的 I（舒适维度）建议记为 `I_com`（或 `I3` / `I4`），以彻底避免混淆。
