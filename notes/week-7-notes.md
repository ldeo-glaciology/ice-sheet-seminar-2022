# Notes from week 7



## Shear strain rate

Consider the initially square material in this figure

![shear_diagram](https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/8e01bdd20c3a2ce6da583e3336396285c8fd1ccd/images/shear_diagram.jpg)

It undergoes some shear over a time $\delta t$ and the angle in the interior of bottom left corner of the square is reduced from a right angle to an angle of $\pi/2 - \theta_1 - \theta_2$.

We define the shear strain as half the reduction in this angle 

$$ 
\epsilon_{xy} = \frac{1}{2}\left(\theta_1 + \theta_2\right).
$$

We assume that \underline{u} = 0 at the bottom left corner of the element. From the geometry of the system, i.e. using 'tan = opposite of adjacent', 

$$
\tan(\theta_1) = \frac{\frac{\partial v}{\partial x}\delta x \delta t}{\delta x}.
$$

The 'opposite' length is the distance the right hand side of the bottom face of the square has moved, which is equal to the rate of change of the y-component of velocity with $x$ times the distance moved in the $x$ direction ( $\frac{\partial v}{\partial x}\delta x$ ), multiplied by the time $\delta t$. The adjacent part is simply $\delta x$. 

We make the assumption that the angle is small and $\tan(\theta_1) \approx \theta_1$, leaving

$$
\theta_1 = \frac{\partial v}{\partial x} \delta t.
$$

Repeating for $\theta_2$ gives

$$
\theta_2 = \frac{\partial u}{\partial y} \delta t.
$$

Substituting into the top equation give

$$ 
\epsilon_{xy} = \frac{1}{2}\left(\frac{\partial v}{\partial x} \delta t + \frac{\partial u}{\partial y} \delta t\right).
$$

Dividing by the time interval gives us the expression for shear strain rate

$$ 
\dot{\epsilon}_{xy} = \frac{1}{2}\left(\frac{\partial v}{\partial x}  + \frac{\partial u}{\partial y} \right).
$$

More generally if we have $i, j = \{1,2,3\}$ and defining $u_1 = u$, $u_2 = v$, and $u_3 = w$ and $x_1 = x$, $x_2 = y$, and $x_3 = z$, we have 

$$ 
\dot{\epsilon}_{ij} = \frac{1}{2}\left(\frac{\partial u_j}{\partial x_i}  + \frac{\partial u_i}{\partial x_j} \right),
$$

meaning that you can substitute 1, 2, and 3 in as $i$ and $j$ to get the different components of strain rate. Note that when $i=j$ you get our old expression for normal strain rate, e.g., 

$$ 
\dot{\epsilon}_{xx} = \frac{\partial u}{\partial x}.
$$












