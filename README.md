# Wilson-Cowan-theorems
Numerical verification of the four theorems from Wilson and Cowan (1972) on emergent dynamics in coupled excitatory-inhibitory neural populations.

## Background
in 1972, Wilson and Cowan derived ODEs, describing the behavior of exhitatory and inhibitory neurons in a population. They also presented four predictions, which depending upon the parameters, predicts emergence of stable states, multiple hysteresis, and limit cycles.
The present project aims to implement the equations given in the original paper as well as numerically test them..

parameters include: 
 c1 - E->E connection weight
 c2 - I->E connection weight
 c3 - E->I connection weight
 c4 - I->I connection weight
 a_e, a_i - sigmoid steepness
 theta_e, theta_i - firing threshold
 P, Q - external inputs
 r_e, r_i - refractory terms


## Theorems
theorem 1 : When c1 > 9/a_e, the nullclines will have at least three intersections, giving at least three steady state solutions. Tested by choosing c1 and a_e such that the condition is satisfied, then sweeping P and Q.

theorem2: Five steady states exist when: a_e * a_i * c2 * c3 > (a_e * c1 - 9)(a_i * c4 + 9). The condition requires that c2*c3 (the negative feedback loop strength) exceeds the interaction strength between subpopulations. Tested by fixing 
parameters to satisfy the condition and sweeping P and Q

Note: For Theorems 1 and 2, scipy.optimize.fsolve is used to find fixed points. Unstable fixed points cannot be identified since no trajectories flow into them and therefore only stable fixed points are detected.

Theorem 3: 
Two cases-
- If c1*a_e > c4*a_i + 18 is NOT satisfied but Theorem 2's condition is met → multiple hysteresis occurs for some (P, Q)
- If c1*a_e > c4*a_i + 18 AND a_e*c2 > a_e*c1 - 9 are both satisfied → limit cycle dynamics emerge for some (P, Q)
Both cases are tested by fixing the appropriate parameters and sweeping P and Q.

Note:The Fig 11a parameters from Wilson & Cowan (1972) do not satisfy the paper's own sufficient conditions for limit cycle dynamics. The limit cycle is nonetheless reproduced numerically.

Theorem 4: Any circuit showing limit cycle activity for some (P, Q) will also show simple hysteresis for a different (P, Q). The same parameters used for the limit cycle case in Theorem 3 are fixed, and P and Q are swept through to show both regimes coexist in stimulus space.


 ## How to Run

The script was written in Google Colab. To run it:

**In Google Colab:**
- Upload wilson_cowan.py to Colab and run all cells
- All dependencies are pre-installed in Colab

**On your local machine:**
- Install dependencies: pip install numpy scipy matplotlib
- Run: python wilson_cowan.py

Note: The (P,Q) parameter sweeps take several minutes to complete.
 
 

