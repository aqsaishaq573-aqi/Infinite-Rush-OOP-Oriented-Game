# 🎮 Infinite Rush - OOP-Oriented Game

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![C#](https://img.shields.io/badge/C%23-Latest-239120?logo=csharp)](https://docs.microsoft.com/en-us/dotnet/csharp/)
[![Windows Forms](https://img.shields.io/badge/Windows%20Forms-Desktop-0078D4?logo=windows)](https://docs.microsoft.com/en-us/dotnet/desktop/winforms/)
[![License](https://img.shields.io/badge/License-Educational-green.svg)](LICENSE)

A comprehensive 2D game framework built with C# and Windows Forms, designed for teaching **Object-Oriented Programming (OOP)** concepts through game development. This project demonstrates core OOP principles including inheritance, polymorphism, interfaces, and composition patterns.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Architecture](#-architecture)
- [Key OOP Concepts](#-key-oop-concepts-demonstrated)
- [Getting Started](#-getting-started)
- [Game Features](#-game-features)
- [Educational Use](#-educational-use)
- [Development Guide](#-development)
- [Troubleshooting](#-troubleshooting)
- [Learning Outcomes](#-learning-outcomes)
- [Contact](#-contact)

---

## 🎮 Project Overview

This framework provides a complete game development foundation featuring:

- ✨ **Component-based architecture** for flexible game object management
- 🎯 **Physics and collision systems** for realistic game interactions
- 🎬 **Animation system** with state management
- 🔄 **Multiple movement patterns** demonstrating strategy pattern implementation
- ⏱️ **Game loop architecture** with proper timing and update cycles
- 🎭 **Entity management** with various game object types

---

## 🏗️ Architecture

### Core Components

```
FirstDesktopApp/
├── 🎮 Core/                    # Game Engine Foundation
│   ├── Game.cs                 # Main game container
│   └── GameTime.cs             # Timing system
│
├── 👾 Entities/                # Game Objects
│   ├── GameObject.cs           # Base class for all entities
│   ├── Player.cs               # Player character
│   ├── Enemy.cs                # AI-controlled enemies
│   ├── Collectible.cs          # Collectible items
│   ├── Obstacle.cs             # Static barriers
│   ├── Hazard.cs               # Dangerous objects
│   └── EnvironmentObject.cs    # Background elements
│
├── 🔌 Interfaces/              # Contracts & Polymorphism
│   ├── IDrawable.cs            # Rendering capability
│   ├── IUpdatable.cs           # Update loop participation
│   ├── ICollidable.cs          # Collision detection
│   ├── IMovement.cs            # Movement behavior
│   └── IAnimatable.cs          # Animation support
│
├── 🏃 Movements/               # Strategy Pattern
│   ├── KeyboardMovement.cs     # Player input
│   ├── HorizontalPatrolMovement.cs
│   ├── VerticalPatrolMovement.cs
│   ├── ZigZagMovement.cs
│   └── ChaseMovement.cs        # AI that follows targets
│
├── 🎬 Animation/               # Animation System
│   ├── Animation.cs            # Animation data
│   ├── AnimationComponent.cs   # Component for animations
│   └── AnimationState.cs       # State machine
│
├── ⚙️ Systems/                 # Game Systems
│   ├── CollisionSystem.cs      # Collision detection
│   ├── PhysicsSystem.cs        # Physics calculations
│   └── SoundManager.cs         # Audio playback
│
├── 🎯 Game/                    # Game Logic
│   ├── EndlessRunnerGameForm.cs
│   ├── AnimatedEndlessRunnerForm.cs
│   ├── ScoreManager.cs
│   ├── DataManager.cs
│   └── AudioManager.cs
│
└── 🖥️ UI/                      # User Interface
    └── MainMenuForm.cs
```

---

## 🎯 Key OOP Concepts Demonstrated

### 1️⃣ Inheritance

```
GameObject (base)
├── Player
├── Enemy
├── Collectible
├── Obstacle
├── Hazard
└── EnvironmentObject
```

### 2️⃣ Interfaces & Polymorphism

- **IDrawable** - Objects that can be rendered
- **IUpdatable** - Objects that update each frame
- **ICollidable** - Objects that participate in collision detection
- **IMovement** - Pluggable movement behaviors

### 3️⃣ Strategy Pattern

Movement behaviors are interchangeable, allowing game objects to change behavior at runtime:

```csharp
GameObject obj = new GameObject();
obj.Movement = new KeyboardMovement();  // Player control
obj.Movement = new ChaseMovement();     // AI control
```

### 4️⃣ Composition over Inheritance

- Animation components can be added to any game object
- Movement behaviors are composed rather than inherited

### 5️⃣ Component-Based Architecture

Objects are composed of reusable components (movement, animation, etc.)

---

## 🚀 Getting Started

### Prerequisites

- .NET 8.0 SDK or higher
- Windows OS (Windows Forms requirement)
- Visual Studio 2022 or Visual Studio Code with C# extensions

### Dependencies

The project uses the following NuGet packages:

- **EZInput** (v1.3.2) - Simplified input handling
- **Microsoft.Data.SqlClient** (v6.1.3) - Database connectivity

### Installation

1. **Clone or extract the repository**

   ```bash
   cd GameFramework-OOP-Course-master
   ```

2. **Restore NuGet packages**

   ```bash
   dotnet restore
   ```

3. **Build the project**

   ```bash
   dotnet build
   ```

4. **Run the application**

   ```bash
   dotnet run
   ```

   Or open `FirstDesktopApp.csproj` in Visual Studio and press **F5**.

---

## 🎮 Game Features

| Feature | Description |
|---------|-------------|
| 🏃 **Endless Runner Mode** | Complete implementation with scoring |
| 🎬 **Animation System** | Sprite-based animations with state management |
| 💥 **Collision Detection** | Robust collision system for all game objects |
| 🌍 **Physics** | Gravity and velocity-based movement |
| 🔊 **Audio** | Sound effects and music management |
| 💾 **Data Persistence** | High score tracking with database integration |
| ⌨️ **Input Handling** | Keyboard controls with EZInput library |

---

## 🎓 Educational Use

### Learning Objectives

This project is ideal for:

- Understanding class hierarchies and inheritance
- Implementing interfaces for polymorphic behavior
- Applying design patterns (Strategy, Component)
- Managing game loops and timing
- Handling collision detection
- Implementing state machines (animation states)
- Working with event-driven programming
- Understanding separation of concerns

### Suggested Exercises

| Level | Exercise |
|-------|----------|
| 🟢 **Beginner** | Create a new enemy type with custom behavior |
| 🟡 **Intermediate** | Implement a new movement pattern (e.g., circular, wave) |
| 🟠 **Advanced** | Add a weapon system with different projectile types |
| 🔴 **Expert** | Implement a particle system for visual effects |

---

## 🛠️ Development

### Adding a New Game Object

1. Create a class that inherits from `GameObject`
2. Override `Update()` and/or `Draw()` methods as needed
3. Implement `OnCollision()` for collision handling
4. Assign a movement behavior via the `Movement` property
5. Add to the game using `game.AddObject()`

### Creating a Custom Movement Behavior

1. Implement the `IMovement` interface
2. Define the movement logic in the `Move()` method
3. Assign to any `GameObject`'s Movement property

### Example Code

```csharp
// Create a player
var player = new Player
{
    Position = new PointF(100, 100),
    Size = new SizeF(32, 32),
    Movement = new KeyboardMovement()
};

// Create an enemy with chase behavior
var enemy = new Enemy
{
    Position = new PointF(400, 300),
    Size = new SizeF(32, 32),
    Movement = new ChaseMovement { Target = player }
};

// Add to game
game.AddObject(player);
game.AddObject(enemy);
```

---

## 🐛 Troubleshooting

### Game runs too fast/slow?

- ✅ Check `GameTime` delta calculations
- ✅ Verify timer intervals in the game form

### Collisions not working?

- ✅ Verify `IsRigidBody` is set correctly
- ✅ Check if objects are marked as `IsActive`
- ✅ Ensure bounds are correctly calculated

### Animations not playing?

- ✅ Verify animation states are set up correctly
- ✅ Check if `AnimationComponent` is attached
- ✅ Ensure `Update()` is being called

---

## ✅ Learning Outcomes

By completing this project, students will be able to:

- ✔️ Design a class hierarchy for a new game concept
- ✔️ Implement interfaces for polymorphic behavior
- ✔️ Apply at least 3 design patterns appropriately
- ✔️ Write SOLID-compliant code
- ✔️ Debug and optimize game performance
- ✔️ Create complete, playable game features
- ✔️ Document code and architecture decisions
- ✔️ Collaborate using version control
- ✔️ Review and improve peer code
- ✔️ Explain and justify design choices

---

## 📝 Assignment Details

- **Course:** Object-Oriented Programming (OOP)
- **Project Type:** Final Project
- **Institution:** Educational University Project

---

## 🙏 Acknowledgments

This framework is designed for teaching OOP principles in a practical, engaging context. It demonstrates industry-standard patterns and practices in game development while remaining accessible to students learning programming concepts.

---

## 📝 License

Educational university project — free to use and modify for learning purposes.

---

## 📧 Contact

**Ayesha Rauf** — [@ayesha189](https://github.com/ayesha189)

**Project Link:** [https://github.com/ayesha189/Infinite-Rush-OOP-Oriented-Game](https://github.com/ayesha189/Infinite-Rush-OOP-Oriented-Game)

---

## ⭐ Support

If you enjoyed playing this game or found the code helpful, please consider giving it a star!

---

<div align="center">

### 🎮 Happy Gaming! 🍔🐱💨

Made with ❤️ for learning OOP concepts

</div>
