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

### Nondimensionalize ?

$$
H = H^*H_0,\\ a = a^*a_0,\\ x = x^*x_0
$$

## Numerical solution to the equations. 

sia.ipynb solves the (dimensional) SIA equations 

## Analytical solution to the equations

## Vertical velocity

## Dating of crevasse burial (Wearing and Kingslake, 2020)