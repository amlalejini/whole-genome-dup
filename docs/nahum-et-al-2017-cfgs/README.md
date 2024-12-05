# Recreating configuration files for "Improved adaptation in exogenously and endogenously changing environments"

by Nahum et al. <https://doi.org/10.1162/isal_a_052>

Notes
- I think we just want to recreate the "flipped treatment" configuration where the middle third of the run rewards different tasks as compared to the first and final thirds of the run.

Open questions / Assumptions
- (Alex) Paper specifies that tasks are rewarded proportionally to their complexity, but I'm not seeing the exact reward levels. Assuming defaults.
- (Alex) Assuming well-mixed environment.
- (Alex) Assuming default mutation rates.

Configuration details from paper:

- Population size 3600
- 100,000 updates
  - Phase changes 33,000, 66,000
- Fixed-length genomes, 100 instructions
- Population seeded with single injected organism (default ancestor)
- Environmental change
  - Every run broken into three equal-length periods where the environment in each period was either "rigid" or "malleable".
    - Rigid = unchanging resource concentrations, not influenced by the tasks performed. I.e., unlimited resource setup.
    - Malleable = resources flow into the world at a fixed rate in a chemostat-like manner and are consumed when tasks are performed. I.e., limited resources
  - Treatments:
    - Fixed treatment:
      - uses identical rigid environment for each period
    - Flipped treatment
      - First and third periods are "rigid" reference environment
      - Middle period is rigid has a different set of rewarded tasks.
    - Negative frequency dependent treatment
      - Middle period is malleable.
- Environment
  - Reference environment
    - Not, Nand, And, Nor, Xor, and Equals present, unlimited resources
  - Flipped treatment middle environment
    - Contains only OrNot, Or, and AndNot resources (unlimited)
  - Limited resources
    - Inflow: 100 units per update
    - Outflow: 0.01 proportion of concentration per update
    - Reward is proportion to concentration