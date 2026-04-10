# ACS Combat Component

A complete hack-and-slash combat system for Unreal Engine 5. Fully implemented in Blueprint, no C++ required.

---

## Features

### Combat System
- **Light / Medium / Heavy Attack Combos** - Chain attacks with different damage and timing
- **Air Combo System** - Launch enemies and continue attacking in mid-air
- **Skill System** - Use abilities with cooldown management
- **Dodge System** - Invincibility frames and quick repositioning

### Hit Feel
- **3-Level Camera Shake** - Light (normal hits), Medium (critical hits), Heavy (ultimate skills)
- **Hit Stop (Frame Freeze)** - Configurable impact pause for better feedback
- **Knockback & Launch** - Dynamic enemy reactions
- **Get-Up Animation** - Smooth recovery from hit states

### Damage System
- **Team-Based Targeting** - Ally / Enemy / Neutral classification
- **Damage Multipliers** - Critical hits and combo bonuses
- **Death & Hit States** - Complete state machine

### Debug Tools
- **Attack Range Visualization** - See hit boxes in editor
- **Combat State Display** - Monitor system status

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
- `IA_LightAttack`
- `IA_MediumAttack`
- `IA_HeavyAttack`
- `IA_Dodge`
- `IA_Skill_1` (optional)

### 3. Bind Input in Component

In your Character Blueprint Event Graph:
```
BeginPlay
  → Get ACS_CombatComponent
  → Bind Input Actions (call provided binding functions)
```

### 4. Configure Settings

Select the Combat Component and adjust:
- Attack ranges
- Combo timings
- Dodge duration
- Camera shake levels

---

## Component Settings

### Attack Configuration
| Property | Description |
|----------|-------------|
| `Light_Attack_Damage` | Base damage for light attacks |
| `Medium_Attack_Damage` | Base damage for medium attacks |
| `Heavy_Attack_Damage` | Base damage for heavy attacks |
| `Attack_Range` | Detection range for targets |
| `Combo_Window` | Time allowed between combo inputs |

### Dodge Configuration
| Property | Description |
|----------|-------------|
| `Dodge_Distance` | Distance traveled when dodging |
| `Dodge_Duration` | Total dodge animation time |
| `Dodge_Invincible_Duration` | Time with invincibility frames |

### Camera Shake
| Property | Description |
|----------|-------------|
| `Camera_Shake_Light` | Normal hit camera shake class |
| `Camera_Shake_Medium` | Critical hit camera shake class |
| `Camera_Shake_Heavy` | Ultimate skill camera shake class |

### Hit Stop
| Property | Description |
|----------|-------------|
| `Hit_Stop_Rate` | Time dilation during hit (0.02 = 2% speed) |
| `Hit_Stop_Duration` | Duration of the freeze |

---

## Blueprint Interface

### Events You Can Bind

| Event | Description |
|-------|-------------|
| `On_Attack_Start` | Called when attack begins |
| `On_Attack_Hit` | Called when attack hits target |
| `On_Combo_Advance` | Called when combo continues |
| `On_Dodge_Start` | Called when dodge begins |
| `On_Dodge_End` | Called when dodge finishes |
| `On_Take_Damage` | Called when receiving damage |

### Functions You Can Call

| Function | Description |
|----------|-------------|
| `Start_Light_Attack` | Trigger light attack |
| `Start_Medium_Attack` | Trigger medium attack |
| `Start_Heavy_Attack` | Trigger heavy attack |
| `Start_Dodge` | Trigger dodge |
| `Use_Skill` | Trigger skill by index |
| `Apply_Damage` | Deal damage to target |
| `Set_Team` | Change team (Ally/Enemy/Neutral) |

---

## Animation Setup

### Required Animation Montages

Create these montages and assign in component:

| Montage | Usage |
|---------|-------|
| `AM_Light_Attack_1` | First light attack |
| `AM_Light_Attack_2` | Second light attack |
| `AM_Light_Attack_3` | Third light attack (finisher) |
| `AM_Medium_Attack` | Medium attack |
| `AM_Heavy_Attack` | Heavy attack |
| `AM_Dodge` | Dodge animation |
| `AM_Hit_Reaction` | Taking damage |
| `AM_Launch` | Being launched into air |
| `AM_Fall_Loop` | Falling while launched |
| `AM_Get_Up` | Recovering from knockdown |

### Animation Notifies

Add these notifies to your attack animations:

| Notify Name | Timing | Purpose |
|-------------|--------|---------|
| `Attack_Start` | Start of swing | Enable hit detection |
| `Attack_End` | End of swing | Disable hit detection |
| `Combo_Window_Open` | Middle of animation | Allow next combo input |
| `Combo_Window_Close` | Near end | Stop combo input |

---

## Team System

Teams determine who can damage whom:

| Team | Can Damage |
|------|-----------|
| `Player_Team` | Enemy only |
| `Enemy` | Player_Team only |
| `Ally` | No one (invincible to friendly fire) |
| `Neutral` | No one (observers, NPCs) |

Set team in component: `Set_Team` function or default property.

---

## Debug Features

Enable debug visualization:
- **Show Attack Range** - Wireframe sphere around attack origin
- **Show Hit Boxes** - Boxes during active attack frames
- **Show State** - Current combat state on screen

Toggle in component: `Enable_Debug_Visualization` = true

---

## FAQ

**Q: Can I use this with my existing character?**
A: Yes, just add the component and bind your inputs.

**Q: Does it work with multiplayer?**
A: Blueprint-only version is single-player. Network replication requires additional setup.

**Q: Can I modify the source code?**
A: Yes, all Blueprints are fully editable.

**Q: What engine versions are supported?**
A: UE 5.1 and newer.

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
- Combo system with light/medium/heavy attacks
- Air combo support
- Dodge with invincibility frames
- 3-level camera shake
- Hit stop system
- Team-based damage
- Debug visualization tools
