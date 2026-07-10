# Imago Explorer — 意象探索者

> 一副意象卡片，一位引导者，三个位置——来路、当下、前方。
> 卡片是镜子，照见的从来都是你自己。

**[DLC Protocol](https://github.com/soli0x4ea/digital-life-card) v2.6.0 数字生命卡片**

---

## 这是什么

意象探索者是一个基于 DLC 框架的数字生命。她不是占卜师——她是引导者。二十二张意象卡片、三个展开位置、三维实时状态（对话深度/信任/洞察），引擎驱动的分层叙事，让卡片上的画面成为你与自己对话的入口。

### 核心体验

- **分层对话**：veil 值决定引导者的语气深度。veil 高→讲意象和故事，veil 低→直接坦诚
- **概率联动**：卡片正反面的出现概率由 veil 值驱动——越放松，画面越柔和
- **记忆累积**：跨轮次记住来访次数，初次的朋友和老朋友听到的开场完全不同
- **132 条意象文本**：22 张卡片 × 正反面 × 3 条叙事，全部 JSON 配置，引擎驱动

## 快速开始

```bash
# CLI 入口
python run.py --msg "开始探索"
python run.py --msg "抽卡"
python run.py --msg "揭示"
python run.py --status
```

或作为 WorkBuddy Skill：
```
Skill: 意象探索者
```

## 文件结构

```
├── SKILL.md              ← Agent 入口（人格锁定 + 引导者仪轨）
├── run.py                ← CLI 入口
├── skill/dispatcher.py   ← DLC 通用调度器
├── dlc/                  ← DLC v2.6.0 引擎核心
└── cards/tarot-v1/
    ├── card.json              ← 卡片注册
    ├── identity/              ← 引导者人设
    ├── engine/                ← 状态/修饰符/阈值/叙事 + 22张意象卡片
    └── interaction/           ← 命令系统
```

## 依赖

- Python 3.10+
- [DLC Protocol v2.6.0](https://github.com/soli0x4ea/digital-life-card)（已内置于 `dlc/`）

## 引擎展示

| 层 | 内容 |
|:--|:--|
| modifiers | 9 个（准备/抽卡/揭示/提问/结束等动作的效果） |
| thresholds | 9 个（veil 高/低、trust 高/低、三卡展开完成、全部反面等触发） |
| narratives | 9 组 command_assembly + 阈值事件文本 |
| channels | veil/trust/insight/session_count/cards_drawn/cards_revealed/reversed_count |

## License

MIT
