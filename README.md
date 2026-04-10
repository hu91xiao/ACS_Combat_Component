# ACS Combat Component

A complete hack-and-slash combat system for Unreal Engine 5. Fully implemented in Blueprint, no C++ required.

---

## Features

### Combat System
- **Light/Heavy/Skill Attack Combos** - Chain attacks with different damage and timing
- **Skill System** - Highly customizable, supports multiple skill configurations
- **Air Combo** - Launch enemies and continue attacking in mid-air
- **Dodge** - Invincibility frames and quick repositioning

### Hit Feedback
- **Level 1/2/3 Camera Shake** - Corresponding to different impact intensities
- **Hit Stop** - Configurable freeze frame for enhanced feedback
- **Knockback & Launch** - Dynamic enemy hit reactions
- **Get-Up Animation** - Smooth recovery from knockdown

### Damage System
- **Team Classification** - Player_Team / Enemy_Team
- **Damage Multiplier** - Set base damage multiplier for each hit
- **Death & Hit States** - Complete state machine

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
- Various attack and hit reaction animations

---

## Animation Notify - Attack Settings

Add Attack Notify to your animation montages and configure:

| Property | Description |
|----------|-------------|
| `Damage_Multiplier` | Damage multiplier for this attack |
| `Distance` | Attack detection distance |
| `Radius` | Attack detection radius |
| `Knockback_Distance` | Knockback distance |
| `Launch_Height` | Launch height |
| `Time_Duration` | Hit stop duration |
| `Time_Rate` | Hit stop rate (0.02-0.1) |
| `Hit_Shake_Amplitude` | Hit enemy shake amplitude |
| `Camera_Shake_Level` | Camera shake level (1/2/3) |
| `Miss_Camera_Shake` | Camera shake on miss |
| `Debug_Attack_Range` | Show attack range debug |

---

## Team System

| Team | Description |
|------|-------------|
| `Player_Team` | Player team, can attack Enemy_Team |
| `Enemy_Team` | Enemy team, can attack Player_Team |

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
