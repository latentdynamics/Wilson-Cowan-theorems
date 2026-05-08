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
 theorem 1 is tested first by keeping a_e fixed and sweeping c1 0 to 30 and steady states are counted using scipy.optimize.fsolve. the second test involves choosing c1 and a_e is such that the condition is satisfied and P and Q are sweeped through. 

theorem2: five steady states exist when a_e * a_i * c2* c3 > (a_e*c1 - 9)(a_i * c4 +9). the condition requires that c2c3, which is the measure of negative feedback loop, be relatively strong in a population.
theorem 2 is tested by sweeping c3 0 to 30, keeping c2 fixed at 4. the steady states are counted by scipy.optimize.fsolve.

theorem_3 : claims that when c1*a_e > c4*a_i + 18 is not satisfied and the condition for theorem 2 is satisfied then multiple hysteresis will occur. if c1*a_e > c4*a_i + 18 and a_e*c2 > a_e*c1 -9, both are satisfied then for some values of P and Q, limit cycle will emerge. the theorem is tested by keeping a_e fixed and sweeping c1 0 to 25.

Theorem_4: for a different class of stimulus configurations, the population showing limit cycle will also show multiple hysteresis. P and Q are sweeped 0 to 10 and emergent dynamics are plotted. 


 
 
 

