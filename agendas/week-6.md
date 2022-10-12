# Agenda, week 6

Picking up where we left off from last week with driving stress, then use this tp get the perfectly plastic model and then the SIA. 


## 1. driving stress

- $\tau_d = -\rho g H \frac{\partial H}{\partial x}$ 
- integrate total force acting on each side of a column
- then take the difference between the two   

Also present this in two dimensions using $\nabla$

I would like to compute this over Antarctica. I made a start on pangeo in gradient.ipynb. This runs nicely on the cluster in m2lines.


## 2. perfectly plastic model 
- $\tau_d = Y = 100$ kPa

## 3. derive mass balance eqn or SIA from $tau_d$?
(up to us which one we do!)

Take the expression for the driving stress and put it in Glen's flow law to get the vertical gradient of horizontal velocity $\frac{\partial u}{\partial z}$. Then integrate vertically to get $u$. Then integrate again to get $q$. 

The result should be 

$$
q = \frac{A}{n+2} \left(-\rho g \frac{\partial H}{\partial x}\right)^n H^{n+2}
$$
