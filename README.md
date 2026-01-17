# Big Sky Ski Cop 🎿🚔

An HTML5 3D skiing game where you escape from ski patrol at Big Sky Resort!

## Game Description

You've just gotten off the tram at the top of Lone Mountain (11,166 ft) at Big Sky Resort in Montana. All the runs are closed, but you decide to ski down anyway. As soon as you start, you get a 1-star wanted level and ski patrol in black and green uniforms begins pursuing you, Grand Theft Auto style!

## Features

### Realistic Terrain
- Uses actual elevation data from Lone Mountain at Big Sky Resort
- Fetches terrain tiles from Terrarium DEM service (same as the Leaflet_3d_terrain_maps repo)
- Real mountain coordinates: 45.2849°N, 111.4008°W

### Advanced Skiing Physics
- Realistic downhill acceleration based on terrain slope
- Edge control with Q/E keys for carving turns
- Speed control with W (push) and S (brake/pizza)
- Jump mechanics with Space bar
- **Ragdoll physics** when you crash or land too hard
- Speed displayed in MPH, elevation in feet

### GTA-Style Wanted System (1-5 Stars)

**⭐ Level 1:** Initial wanted level - patrol skis in front to block you

**⭐⭐ Level 2:** More patrol units spawn and pursue aggressively

**⭐⭐⭐ Level 3:** Patrol starts shooting tazers at you

**⭐⭐⭐⭐ Level 4:** Snowmobiles deployed to ram you

**⭐⭐⭐⭐⭐ Level 5:** Ski cats (groomers) join the chase

### Ski Patrol AI
- Patrol wears authentic black and green ski patrol uniforms
- Early tactics: Ski in front to block and tackle you
- Advanced tactics: Chase, shoot tazers, deploy vehicles
- You can make them crash by skiing close and dodging
- Track "Patrol Evaded" count as you cause them to wipe out

### Controls
- **W** - Speed up (push/tuck)
- **S** - Slow down (pizza/brake)
- **A** - Turn left
- **D** - Turn right
- **Q** - Edge left (carve)
- **E** - Edge right (carve)
- **Space** - Jump
- **Mouse** - Look around (camera control)

## Technology Stack

- **Three.js** - 3D rendering engine
- **Cannon.js** - Physics engine for realistic skiing and ragdoll physics
- **Terrarium Terrain Tiles** - Real elevation data from AWS S3
  - Source: `https://s3.amazonaws.com/elevation-tiles-prod/terrarium/{z}/{x}/{y}.png`
  - Encoding: Terrarium format (height = R×256 + G + B/256 - 32768)

## How It Works

### Terrain Loading
The game fetches real Digital Elevation Model (DEM) data for Big Sky Resort from Terrarium tiles at zoom level 13. The elevation data is decoded from RGB values and converted from meters to feet, then applied to a Three.js PlaneGeometry to create a realistic 3D mountain terrain.

### Physics System
- Gravity-driven downhill acceleration
- Slope-based physics using terrain normals
- Edge control affects turn radius based on current speed
- Ragdoll physics activate on hard landings or high-speed crashes
- Collision detection with patrol and vehicles

### AI Behavior
Ski patrol uses simple pathfinding to:
1. **Block** - Position themselves in your path (Wanted 1-2)
2. **Chase** - Pursue you directly (Wanted 3+)
3. **Shoot** - Fire tazers when in range (Wanted 3+)
4. **Ram** - Use vehicles to intercept (Wanted 4-5)

## Running the Game

Simply open `index.html` in a modern web browser. No build process required!

The game loads external libraries from CDN:
- Three.js r128
- Cannon.js 0.6.2

## Game Over Conditions

You get busted if:
- Ski patrol tackles you (gets within 5 ft)
- You get hit by a tazer
- A snowmobile or ski cat rams you
- You crash in ragdoll mode and can't recover

## Stats Tracked

- **Speed** - Current velocity in MPH
- **Altitude** - Current elevation in feet
- **Patrol Evaded** - Number of patrol members you've caused to crash
- **Distance** - Total distance skied in feet

## Tips for Success

1. **Control your speed** - Too fast and you'll crash on jumps
2. **Use edge control** - Q/E keys help you carve tight turns at high speed
3. **Make patrol crash** - Get close then dodge to increase your evaded count
4. **Watch your landings** - Landing too hard triggers ragdoll physics
5. **Keep moving downhill** - Momentum is your friend

## Future Enhancements

- Sound effects (swoosh, crashes, tazer zaps)
- More detailed skier models
- Better terrain textures (snow trails, trees, rocks)
- Multiple runs and route choices
- Multiplayer mode
- Leaderboard system
- Weather effects (powder snow, visibility)
- Trick system (grabs, spins, flips)

## Credits

- Terrain data: [Terrarium RGB Tiles](https://github.com/tilezen/joerd/blob/master/docs/formats.md)
- Inspired by: GTA wanted system, Shred Sauce skiing controls
- Location: Big Sky Resort, Montana

## License

MIT License - Feel free to modify and share!

---

**Warning**: This is a game. Don't actually ski closed runs in real life - respect ski patrol and mountain safety!
