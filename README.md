
# UE5 Stamina & Sprint Component (Interface-Based, Momentum-Safe)

A reusable Unreal Engine 5 **Blueprint Component** that provides a clean,
interface-driven stamina and sprint system with **momentum-safe sprint stopping**.

The component requires **zero Player-side movement logic**.
All configuration is done once on `BeginPlay` via a Blueprint Interface.

---

## 🎮 Demo
- Sprint stop while grounded
![2026-02-0223-04-56-ezgif com-optimize](https://github.com/user-attachments/assets/6260f114-1033-4d44-a38e-dd1464f20b9e)

- Sprint stop while airborne (momentum preserved)
![2026-02-0223-04-56-ezgif com-optimize (1)](https://github.com/user-attachments/assets/3f846072-a161-4c5d-9d2d-a9b60f4f7dd2)

---

## ❓ Problem

In Unreal Engine, modifying `MaxWalkSpeed` while a character is airborne
can unintentionally break momentum and cause unnatural mid-air slowdowns.

Additionally, stamina systems are often tightly coupled to Player Blueprints,
making them hard to reuse or maintain.

---

## 🛠️ Solution

This component solves both problems by:

- Using an **interface-based architecture**
- Deferring sprint stop logic while airborne
- Applying walking speed only when grounded
- Keeping all stamina and sprint logic inside a reusable component

The Player Character only supplies references and configuration values.

---

## ✨ Features

- Blueprint-only (no C++)
- Interface-driven setup
- Momentum-safe sprint stopping
- Clean separation of responsibilities
- Plug-and-play design
- Works with `CharacterMovementComponent`
- Edge-case safe (airborne input release)

---

## 🔌 Integration (Minimal Setup)

This component is designed to be **easy to integrate**.

### Required Steps

1. Add the `BPC_Stamina` component to your Player Character
2. Add the `BPI_StaminaSystem` interface to the Player Character
3. On `BeginPlay`, call the interface function `GetMovementReferences`

That’s it.

---

## 🧩 Required Setup (BeginPlay)

On the Player Character’s `BeginPlay`, call:
### Required Inputs

- Player (self)
- CharacterMovementComponent
- `F_CharacterSpeed` (Walking / Sprinting)
- MaxStamina
- Stamina Drain Amount
- Stamina Regen Amount
- Optional: Exhausted Sound

No other Player-side logic is required.

---

## 🧠 Design Philosophy

This system follows a **component-first, interface-driven design**.

- The Player provides references and configuration data
- The component owns all sprint, stamina, and movement logic
- No direct dependency on a specific Player Blueprint
- Easy to reuse across different characters or projects

> If you can call a Blueprint Interface on BeginPlay,
> you can use this stamina system.

---

## 🧪 Edge Cases Covered

- Sprint released while grounded
- Sprint released while airborne (momentum preserved)
- Sprint re-activated mid-air
- Speed applied only after landing
- Prevents mid-air velocity clamping

---

## 🎯 Use Cases

- FPS / TPS characters
- Fast-paced or parkour movement
- Prototype-friendly stamina systems
- UE5 learning projects with clean architecture

---

## 🧱 What This Component Does NOT Require

- No custom Player movement logic
- No velocity overrides
- No Character Blueprint rewrites
- No C++

---

## 🧩 Engine Version

Tested with Unreal Engine 5.3+

---

## 🚀 Future Improvements

- Network replication support
- Animation Blueprint synchronization
- Sprint buffering / coyote time
- Modular movement states

---

## 📄 License

MIT License – free to use and modify.
