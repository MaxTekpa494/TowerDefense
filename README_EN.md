# Tower Defense - Real-Time Strategy Game

## 📋 Project Description

**Tower Defense** is a real-time strategy game developed in C, implementing advanced system and graphics programming concepts. Players must defend their base against successive waves of monsters by strategically placing towers equipped with elemental gems that possess unique properties.

The game features an element-based combat system (Pyro, Hydro, Dendro) where elements can interact with each other to create elemental reactions, adding significant tactical depth to the gameplay.

## 🎮 Gameplay Overview

Players have a mana reserve that allows them to:
- **Create gems** with random elements and properties
- **Build towers** on the game terrain
- **Upgrade gems** by fusing them to increase their power
- **Place gems on towers** to grant them attack capabilities

Monsters follow a predefined path and attempt to reach the player's base. Each eliminated monster rewards mana, allowing players to strengthen their defenses for subsequent waves, which progressively become more difficult.

## 🛠️ Technical Stack

### Language and Tools
- **Language**: C (C17 and GNU99 standards)
- **Compiler**: GCC with strict options (-Wall, -pedantic)
- **Graphics Library**: MLV (MultiMedia Library for C)
- **Math Library**: libm
- **Build System**: Make
- **Documentation**: Doxygen
- **Version Control**: Git

### Project Architecture

The project is structured in a modular way with clear separation of responsibilities:

```
progc-tekpa_tran/
├── src/           # Source code
│   ├── main.c           # Program entry point
│   ├── moteur.c         # Main loop and game logic
│   ├── graphique.c      # Graphics rendering and interface
│   ├── vague.c          # Monster wave management
│   ├── game.c           # Tower and projectile management
│   ├── gemmes.c         # Gem system and fusion
│   ├── mana.c           # Mana resource management
│   └── terrain.c        # Terrain generation and management
├── include/       # Header files (.h)
├── bin/           # Executables and object files
├── doc/           # Documentation (Doxygen and user.md)
├── makefile       # Compilation system
└── Doxyfile       # Documentation configuration
```

## ✨ Key Features

### 1. Elemental Gem System
- **Three elements**: Pyro (fire), Hydro (water), Dendro (nature)
- **Gem types**: Pure (single element) or Mixed (two elements)
- **Level system**: Gem fusion to increase power
- **Unique properties**: Each gem has specific tint and statistics

### 2. Combat System
- **Attack range**: Gem-equipped towers target monsters within range
- **Projectiles**: Shooting system with real-time trajectory calculations
- **Damage**: Calculated based on gem level, element, and monster tint
- **Splash damage**: Some attacks affect multiple enemies
- **Elemental reactions**:
  - Pyro + Hydro = Vaporization (bonus damage)
  - Hydro + Dendro = Rooting (slowdown)
  - Pyro + Dendro = Poison (damage over time)

### 3. Wave Types
The game generates different wave types with varying probabilities:
- **Normal Wave (50%)**: Moderate number of monsters with standard stats
- **Crowd Wave (20%)**: Many monsters with reduced HP
- **Agile Wave (20%)**: Fast but fragile monsters
- **Boss Wave (10%)**: Few monsters but highly resistant

### 4. Effect System
Monsters can be affected by various effects:
- **Slow**: Reduces movement speed
- **Poison**: Inflicts continuous damage
- **Vaporization**: Instant elemental damage
- **Rooting**: Temporary immobilization

### 5. Resource Management
- **Mana**: Primary resource for creating gems and building towers
- **Mana gain**: Obtained by eliminating monsters
- **Evolving cost**: Actions become more expensive as the game progresses

## 🎯 Notable Technical Aspects

### 1. Algorithms and Data Structures
- **Pathfinding**: Procedural path generation for monsters
- **Collision detection**: Euclidean distance calculation for tower range
- **Dynamic list management**: Efficient reorganization of projectile and monster arrays
- **States and effects**: State machine to manage monster effects

### 2. Event-Driven Programming
- **Game loop**: Architecture based on main loop with 60 FPS update
- **Input handling**: Keyboard (space, 't' key) and mouse (left/right clicks)
- **Timing system**: Use of timestamps for animations and cooldowns

### 3. Graphics Rendering
- **User interface**: Buttons, resource indicators, health bars
- **Animations**: Smooth movement of monsters and projectiles
- **Visual feedback**: Colors to represent elements and monster health
- **Game grid**: Coordinate system with 25x25 pixel cells

### 4. Memory Management
- **Static allocation**: Use of fixed-size arrays to optimize performance
- **Cleanup**: List reorganization to avoid memory leaks
- **Optimized structures**: Calculated sizes to minimize memory footprint

## 📥 Installation and Compilation

### Prerequisites
- **Operating System**: Linux (tested on Ubuntu/Debian)
- **GCC**: C compiler (recent version with C17 support)
- **MLV Library**: MLV graphics library
  ```bash
  sudo apt-get install libmlv3-dev
  ```
- **Make**: Build utility
- **Doxygen** (optional): To generate documentation

### Compilation

1. **Clone the repository**
   ```bash
   git clone https://github.com/MaxTekpa494/TowerDefense.git
   cd TowerDefense/progc-tekpa_tran
   ```

2. **Compile the project**
   ```bash
   make
   ```
   This command generates the `tower` executable in the `bin/` folder

3. **Clean compilation files**
   ```bash
   make clean
   ```

## 🚀 Usage

### Launch the Game
```bash
./bin/tower
```

### Display Help
```bash
./bin/tower -h
```

### Generate Documentation
```bash
doxygen Doxyfile
```
HTML documentation will be generated in `doc/html/`. Open `doc/html/index.html` in a browser.

## 🎮 Player Guide

### Controls

| Action | Command |
|--------|----------|
| **Trigger a wave** | Press `SPACE` |
| **Create a gem** | Click the "Create" button (bottom right) |
| **Upgrade a gem** | Click the "Upgrade" button (bottom left) |
| **Place a tower** | Press `T`, then left-click to confirm or right-click to cancel |
| **Equip a gem** | Left-click on the gem, then left-click on a tower to equip it |
| **Cancel an action** | Right-click |

### Basic Strategies

1. **Mana economy**: Don't create too many gems at the start, focus on the first towers
2. **Strategic fusion**: Merge gems to obtain higher levels and increased damage
3. **Positioning**: Place towers where monsters spend the most time
4. **Elemental synergy**: Use towers with different elements to trigger reactions
5. **Preparation**: Build your defense before triggering waves

## 📊 Project Statistics

- **Lines of code**: ~1,590 lines (.c files)
- **Modules**: 8 main modules
- **Data structures**: 10+ custom structures
- **Functions**: 50+ documented functions
- **Enumerated types**: 5 enumerations for state management

## 👥 Authors

- **TEKPA Max** - TP Group 1
- **TRAN Thien-Loc** - TP Group 1

## 🎓 Academic Context

This project was developed as part of a C programming course, demonstrating:
- Mastery of C language and its advanced concepts
- Ability to structure a medium-sized project
- Understanding of game algorithms (pathfinding, collision detection)
- Use of graphics libraries
- Best development practices (modularity, documentation, versioning)

## 🔍 Technical Highlights

1. **Modular architecture**: Clear separation of responsibilities between different modules
2. **Complex combat system**: Elemental interactions and sophisticated effect system
3. **Performance**: Efficient management of multiple entities (monsters, projectiles) in real-time
4. **Extensibility**: Structure allowing easy addition of new elements or wave types
5. **Documentation**: Commented code and complete Doxygen documentation

## 📝 License

This project was created for educational purposes.

---

*This project demonstrates a deep understanding of C programming, software project management, and implementation of complex game mechanics.*
