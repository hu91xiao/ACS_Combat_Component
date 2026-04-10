# ACS Combat Component

A complete hack-and-slash combat system for Unreal Engine 5. Fully implemented in Blueprint, no C++ required.

---

## Features

### 战斗系统
- **轻/重/技能攻击连招** - 链式攻击，不同伤害和时机
- **技能系统** - 可高度自定义，支持多技能配置
- **空中连击** - 将敌人击飞并在空中继续攻击
- **闪避** - 无敌帧和快速位移

### 打击反馈
- **1级/2级/3级镜头震动** - 对应不同强度的打击感
- **顿帧（Hit Stop）** - 可配置的命中暂停，增强反馈
- **击退与击飞** - 动态敌人受击反应
- **起身动画** - 流畅的击倒恢复

### 伤害系统
- **队伍分类** - Player_Team / Enemy_Team
- **伤害倍率** - 可设置每次命中的基础伤害倍率
- **死亡与受击状态** - 完整的状态机

---

## Installation

1. Copy `ACS_CombatComponent` folder to your project's `Plugins/` directory
2. Restart Unreal Engine
3. Enable plugin: Edit → Plugins → Gameplay → ACS Combat Component → Enable
4. Restart editor

---

## Quick Start

### 1. Add Component to Character

Open your Character Blueprint:
- Add Component → **ACS_CombatComponent**

### 2. Setup Input Actions

Create Input Actions:
- `Light_Attack`
- `Heavy_Attack`
- `Dodge`
- `Skill_Attack(0/1/2/3...)`
- `Jump_Cancels_Attack`

### 3. Bind via Blueprint Interface

Implement the Combat Interface in your Character:
- Handle health reduction
- Determine death condition
- Process input actions

### 4. Configure Settings

Select the Combat Component and adjust:
- `Team`
- `Dodge_Invincible_Duration`
- `Global_Anim_Play_Rate`
- `Base_Damage`
- 各种攻击和受击动画

---

## Animation Notify - Attack Settings

Add Attack Notify to your animation montages and configure:

| Property | Description |
|----------|-------------|
| `Damage_Multiplier` | 本次攻击的伤害倍率 |
| `Distance` | 攻击检测的距离 |
| `Radius` | 攻击检测的半径范围 |
| `Knockback_Distance` | 击退距离 |
| `Launch_Height` | 击飞高度 |
| `Time_Duration` | 顿帧持续时间 |
| `Time_Rate` | 顿帧速率（0.02-0.1）|
| `Hit_Shake_Amplitude` | 命中时的镜头震动幅度 |
| `Camera_Shake_Level` | 镜头震动等级（1/2/3）|
| `Miss_Camera_Shake` | 未命中时是否震动 |
| `Debug_Attack_Range` | 是否显示攻击范围调试 |

---

## Team System

| Team | Description |
|------|-------------|
| `Player_Team` | 玩家队伍，可攻击 Enemy_Team |
| `Enemy_Team` | 敌人队伍，可攻击 Player_Team |

Set team in component: `Team` property

---

## FAQ

**Q: Can I use this with my existing character?**
A: Yes, just add the component and implement the interface.

**Q: Does it work with multiplayer?**
A: Blueprint-only version is single-player. Network replication requires additional setup.

**Q: Can I modify the source code?**
A: Yes, all Blueprints are fully editable.

**Q: What engine versions are supported?**
A: UE 5.3 and newer.

---

## Support

For questions or issues:
- Bilibili: 落熊DorpBear (UID: 475686778)
- WeChat: LuoxiongGamer
- QQ: 505668976

---

## Version History

### v1.0.0
- Initial release
- Light/Heavy/Skill attack combo system
- Highly customizable skill system
- Air combo support
- Dodge with invincibility frames
- 3-level camera shake (1/2/3)
- Hit stop system
- Per-attack damage multiplier
- Team-based damage (Player/Enemy)
- Animation Notify-based configuration
