# Best evolved genotypes

Open either file in Framsticks with **File → Open…**. Each genotype's *info* field records the
run it came from (seed, fitness, number of evaluations) and, for Phase 3, the world it was
evolved in.

Task codes: `line` straight line, `sine` sinusoid bounce, `vel` forward velocity, `jump` jump
height, `dist` distance (organisers' function 3), `tall` tall runner (organisers' function 4).
Algorithm codes: `baseline` NSGA-II, `gene` / `graph` / `hybrid` DE-NSGA-II, `adaptive`
Adaptive DE-NSGA-II, `simpleEA` the organisers' Simple EA.

## best_phase1.gen (72 creatures)

The best run of every task × encoding × algorithm combination from Phase 1. All were evolved in
the reference world (flat, gravity 1, no water) with Energy0 = 2500. Names follow
*task, encoding, algorithm, fitness, run*, e.g. `jump f0 hybrid 5.573 r4`.

## best_phase3.gen (92 creatures)

The best run of every setting × algorithm × encoding combination from Phase 3, i.e. the 14
reconstructed competition-style settings. Names start with the setting, e.g.
`S07 vel f0 adaptive 19.172 r8`, so the list sorts by setting in Framsticks.

A Phase 3 creature only behaves as it did during evolution if Framsticks' world matches the
setting. Set these parameters before simulating it (all other values as in the reference world,
Energy0 = 2500):

| Setting | Task | World | Parameters |
|---|---|---|---|
| S01 | line | Standard evaluation world (the Phase 1/2 training world) | reference world |
| S02 | sine | Shorter lifespan: 60% of the base starting energy (fewer steps to act) | energy0 = 1500 |
| S03 | jump | Half gravity -- jumps last longer, walking gaits slip | gravity = 0.5 |
| S04 | vel | 1.5x gravity -- heavier bodies, harder to lift the COG | gravity = 1.5 |
| S05 | sine | Water 0.5 deep: bodies partly submerged, buoyancy + drag | water_level = 0.5 |
| S06 | line | Water 3.0 deep: fully aquatic, agents must swim | water_level = 3.0 |
| S07 | vel | Blocky rough terrain (5x5 blocks of +-1 height) on a 20x20 world | world_type = 1; world_size = 20; world_map = m 5 5 56565 65656 56565 65656 56565 |
| S08 | line | Smooth heightfield rising 2 units along +x (uphill locomotion) | world_type = 2; world_size = 20; world_map = M 5 5 0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2 |
| S09 | jump | Body constraint: joints between 0.3 and 1.6 long (2023/24 'body constraints') | min_joint = 0.3; max_joint = 1.6 |
| S10 | vel | Target direction rotated 90 deg (= agent born rotated -90 deg) at gravity 0.8 | gravity = 0.8; target_heading_deg = 90 |
| S11 | dist | Smooth heightfield rising 2 units along +x (uphill locomotion) | world_type = 2; world_size = 20; world_map = M 5 5 0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2  0 0.5 1 1.5 2 |
| S12 | dist | Water 0.5 deep: bodies partly submerged, buoyancy + drag | water_level = 0.5 |
| S13 | tall | Half gravity -- jumps last longer, walking gaits slip | gravity = 0.5 |
| S14 | tall | Blocky rough terrain (5x5 blocks of +-1 height) on a 20x20 world | world_type = 1; world_size = 20; world_map = m 5 5 56565 65656 56565 65656 56565 |

The Framsticks parameter names are: `world_type` = World type (0 flat, 1 blocks,
2 heightfield), `world_size` = World size, `world_map` = World map, `water_level` = Water
level, `gravity` = Gravity, `energy0` = Energy0 (lifespan), `min_joint` / `max_joint` =
minimum / maximum joint length. `target_heading_deg` is not a simulator setting: it only
rotates the direction the fitness function rewards, so those creatures run as normal.
