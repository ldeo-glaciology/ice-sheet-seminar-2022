# Agenda, week 10. 

We have a SIA equation. What shall we do with it?

## SIA as a diffusion equation

Diffusion of heat leads to 


$$
\frac{\partial T}{\partial t} = S + \frac{\partial^2 T}{\partial x^2}
$$

The SIA can be thought of as a nonlinear diffusion equation:

$$
\frac{\partial H}{\partial t} = a - \frac{\partial q}{\partial x},
$$

$$
q = -\frac{2A}{n+2} \left(\rho g  \right)^n  H^{n+2}  \left(\frac{\partial H}{\partial x}\right)^n
$$

$$
\frac{\partial H}{\partial t} = a + \frac{2A}{n+2} \left(\rho g  \right)^n  \frac{\partial }{\partial x} H^{n+2}  \left(\frac{\partial H}{\partial x}\right)^n
$$


## Numerical solution to the equations. 

sia.ipynb solves the (dimensional) SIA equations 



## Vertical velocity

$$
u(\zeta)=  -\frac{2A}{n+1} \left(\rho g  \right)^n  H^{n+1}  \left(\frac{\partial H}{\partial x}\right)^n \left( 1- \zeta^{n+1} \right).
$$

$$
\frac{\partial u}{\partial x} = \frac{\partial w}{\partial \zeta}
$$


$$
w = w_s*\left(1 - \frac{n+2}{n+1}  \zeta + \frac{1}{n+1} \zeta^{n+2}\right)
$$


## Dating of crevasse burial (Wearing and Kingslake, 2020)