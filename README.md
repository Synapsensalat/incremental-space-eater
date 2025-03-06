# Supermass

## Core Concept

**Supermass** is a two-stage, cross-platform incremental evolution game that blends idle progression with active, physics-based gameplay.

In the first stage, a meteor impact triggers the emergence of a single biomass seed on a planet's surface. From this fixed starting point, the biomass grows outward, absorbing the planet's mass and gradually unlocking upgrades and milestones in a classic idle/incremental fashion.

Once the planet is fully consumed, the game transitions to the second stage: an active, space-based evolution. In this phase, you control your evolved organism in real-time, moving around a vast, physics-driven cosmos much like in *Solar 2* or *Agar.io*. Here, randomly spawning celestial objects such as asteroids and debris provide mass and biomass, which you must actively collect to continue your evolution. Although the same incremental upgrade system remains, the gameplay becomes more dynamic and interactive as you navigate, combat, and consume in an open, ever-changing space environment.

---

## Technical Stack

### Game Framework & Physics
- **Phaser.js** (with included Matter.js physics)
- Custom **n-body physics** code

### Big Numbers
- **break_infinity.js**

### Spatial Partitioning & Optimization
- **RBush**
- **kdbush** (or a similar algorithm)

### 3D Visualization & Effects
- **Three.js**

### State Management & Web Technologies
- **Zustand**
- **Next.js**
- **Tailwind CSS & SCSS**

---

## Game Progression

### Phase 1: Planetary Evolution

#### Gameplay
- A meteor impact spawns a biomass seed at a fixed point on the planet's surface.
- The biomass grows outward from this point until it covers the entire planet and consumes its mass.

#### Visualization
- Utilize a **space colonization algorithm** (or a similar method) to map the 2D growth pattern onto a 3D planet surface in **Three.js**, with **kdbush** optimizing spatial queries.
- Use a second growth algorithm (**Eden Growth, DLA,** etc.) to fill the space between branches at the end.

#### Transition
- **Complete planetary consumption** triggers the shift to space-based gameplay.

### Phase 2: Space Evolution

As the organism evolves and gains mass, it progresses through several stages, each with a distinct **main weapon upgrade**:

#### Evolution Stages & Weapons
1. **Planet-Sized Stage**  
   - **Main Weapon:** *Tentacles* – Extendable appendages used for combat and resource collection.

2. **Gas Giant Stage**  
   - **Main Weapon:** *TBD*

3. **Star (Sun) Stage**  
   - **Main Weapon:** *Coronal Mass Ejection / Solar Flare* – A burst of high-energy plasma that impacts nearby objects.

4. **Red Giant Stage**  
   - **Main Weapon:** *TBD*

5. **Neutron Star Stage**  
   - **Main Weapon Options:**
     - **Pulsar:** Laser beams emitted from the polar ends with rapid rotation and cooldown intervals.
     - **Magnetar:** A constant, strong magnetic field that damages nearby objects.

6. **Black Hole Stage**  
   - **Main Weapon:** *Hawking Radiation and Time Dilation* – Radiation emission combined with a field that slows down nearby objects.

7. **Supermassive Black Hole / Quasar Stage**  
   - **Main Weapon:** *Enormous Jet of Light* – A powerful, focused beam that shoots in one direction, reminiscent of quasar jets.

---

## Core Systems to Implement

### **Planetary Systems (Phase 1)**

#### Evolution Mechanics
- Incremental upgrades to enhance **biomass growth speed** and **resource efficiency**.
- Resource management and dynamic visualization via the **space colonization algorithm**.

#### Transition Mechanics
- **Triggering space evolution** upon complete planetary consumption.

---

### **Physics Engine**
#### Implementation
- Simplified **n-body gravitational physics** using **Matter.js**, with gravity scaling based on mass.
- **Spatial optimizations** using **RBush** and **kdbush**.
- **Object pooling** to maintain performance with a cap of *x* active physics bodies.

---

### **Movement & Controls**
#### Phase 1
- Static gameplay focused on **resource distribution** and **biomass expansion**.

#### Phase 2
- **Space movement** with basic **thrust controls** and a **mobile-friendly virtual joystick**.
- **Screen wrapping** to simulate an **infinite space environment**.

---

### **Upgrades System**
#### Phase 1 Upgrades
- **Boost biomass growth rate** and **resource consumption efficiency**.

#### Phase 2 Upgrades
- Enhance **propulsion, maneuverability**, and implement **main weapon upgrades**.

---

### **Resource System**
#### Core Resources

1. **Mass**
   - Represents the fixed **raw material** of the planet.
   - In **Phase 1**, mass is gradually **consumed** by the expanding biomass until the entire planet is absorbed.
   - In **Phase 2**, mass becomes an **actively collected** resource from celestial objects (like asteroids) for further evolution.

2. **Biomass**
   - The evolving **life force** of your organism.
   - Produced by converting **mass** via the expanding biomass.
   - Tracked both as a **cumulative total** (for unlocking milestones) and as a **spendable currency** for upgrades.

3. **Energy**
   - A secondary resource essential for **powering conversion processes** and **temporary boosts**.
   - Initially generated from **biomass exposed to sunlight**.
   - Energy production is **tied to sunlight exposure**, rewarding **strategic positioning** and **growth that maximizes sunlit biomass**.

#### Growth Curve
- **Resources scale exponentially** to match progression, with upgrades affecting **production rates** and **conversion efficiencies**.

---

### **Visual Effects**
- Minimalist art style refined with **Tailwind CSS** and **SCSS**.
- Dynamic effects for **biomass growth, planet consumption**, and advanced **Three.js** integrations (*gravitational lensing, particle systems*).

---

## Technical Challenges

1. **Phase Transition**
   - Smoothly shifting from planetary to space gameplay while managing **state transitions** using **Zustand**.

2. **Physics Performance**
   - Balancing **n-body calculations** with **mobile performance** and handling **extreme mass differences**.

3. **Scale Management**
   - Adjusting **camera scaling** and **physics** across **exponential size differences**.

4. **Memory Management**
   - Efficient **object pooling** and **resource cleanup** for prolonged gameplay sessions.

---

## Initial Implementation Plan

1. **Develop planetary phase mechanics** focused on **biomass growth** from a meteor impact.
2. Establish a **robust upgrade system** to enhance growth and resource efficiency.
3. Implement visualization using a **space colonization algorithm** mapped onto a 3D planet with **Three.js**.
4. Create **planet consumption dynamics** and define **phase transition triggers**.
5. Integrate **Zustand** for **state management** during phase transitions.
6. Implement **space movement and physics** using **Phaser.js** with Matter.
7. Progress through **evolution stages** with their corresponding **main weapon upgrades**.
8. Optimize performance in **physics calculations, spatial partitioning, and state management**.
9. Enhance **visual effects** and polish the interface using **Next.js, Tailwind CSS, and SCSS**.
