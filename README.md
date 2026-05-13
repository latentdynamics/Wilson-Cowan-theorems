# Wilson-Cowan-theorems
Numerical verification of the four theorems from Wilson and Cowan (1972) on emergent dynamics in coupled excitatory-inhibitory neural populations.


in 1972, Wilson and Cowan derived ODEs, describing the behavior of exhitatory and inhibitory neurons in a population. They also gave four theorems, which depending upon the parameters, predicts stable states, predicts hysteresis, and limit cycles.
The present project aims to implement the equations given in the original paper as well as numerically test whether the theorem conditions actually predict the system's behavior in simulation.

parameters include: 
 c1 - E->E connection weight
 c2 - I->E connection weight
 c3 - E->I connection weight
 c4 - I->I connection weight
 a_e, a_i - sigmoid steepness
 theta_e, theta_i - firing threshold
 P, Q - external inputs
 r_e, r_i - refractory terms


 theorem 1 : claims that when c1 > 9/a_e, nullclines will have at least three intersections, giving at least three steady state solutions. 
 theorem 1 is tested by choosing c1 and a_e is such that the condition is satisfied and P and Q are swept through. 

theorem2: five steady states exist when a_e * a_i * c2* c3 > (a_e*c1 - 9)(a_i * c4 +9). the condition requires that c2c3, which is the measure of negative feedback loop, be stronger than the interactions between excitatory and inhibitory populations.
theorem 2 is tested by fixing all the parameters such that the condition is met, and P and Q values are swept through.

Note: for theorem 1 and 2, fsolve was used to find out the fixed points. however, unstable points cannot be identified since no trajectories flow into them. 

theorem_3 : claims that when c1*a_e > c4*a_i + 18 is not satisfied and the condition for theorem 2 is satisfied then multiple hysteresis will occur. if c1*a_e > c4*a_i + 18 and condition a_e*c2 > a_e*c1 -9, both are satisfied then for a class of P and Q values, limit cycle will emerge. the theorem is tested first by choosing c1 and a_e values such that a_e*c2 > a_e*c1 -9 and c1*a_e > c4*a_i + 18 are satisfied and P and Q values are swept through. the second test involves condition a_e * a_i * c2* c3 > (a_e*c1 - 9)(a_i * c4 +9) being met and c1*a_e > c4*a_i + 18 not, and P and Q values are swept.
Note: The Fig 11a parameters from Wilson & Cowan (1972) do not satisfy the paper's own sufficient conditions for limit cycle dynamics. The limit cycle is nonetheless reproduced numerically.

Theorem_4: for a different class of stimulus configurations, the population showing limit cycle will also show multiple hysteresis. same parameters as theorem 3 for limit cycle are chosen and fixed, P and Q are swept through.


 
 
 

