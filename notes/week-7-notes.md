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


## Mass balance equation


### Simple derivation

The volume of the column of ice in the diagram below is $V= \delta x \delta y H$, where $H$ is the ice sheet thickness. The rate of change of the volume is 

$$
\dot{H}\delta x \delta y = \text{rate of mass in} - \text{rate of mass out}.
$$

![ice_column_mass_balance](https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/29fca4498ff512dc556ccdef2b03ccdd9195495f/images/ice_column_mass_balance.jpg)

Mass fluxes are the accumulation at the upper surface and the two ice flow fluxes labelled $q_x$ and $q_y$ in the diagram. The flux from accumulation is $a\delta x \delta y$, where $a$ is the net rate of snow fall expressed in units of distance per time, assuming the snow fall is instantaneously compacted to the density of ice. This is called the ice-equivalent accumulation rate. It is commonly used in ice-sheet modelling. 

The fluxes $q_x$ and $q_y$ are depth-integrated ice fluxes. They are defined as

$$
q_x = \int^H_0 u(z) dz;\quad q_y = \int^H_0 v(z) dz.
$$

They are the depth-integrated fluxes per unit width in the across flow direction. They have units of area per time (not volume per time, like you would assume a flux would have). (Additionally, you can treat them as the scalar component of a two-dimensional vector field $\underline{q}  = (q_x, q_y)$.) The total ice-flow flux into the column is therefore $q_x\delta y + q_y \delta x$.

Using the approach we have used several times before, the ice-flow fluxes out of the column on the opposite faces are $\delta y(q_x+ \delta x \frac{\partial q_x}{\partial x})$ and $\delta x(q_y+ \delta y \frac{\partial q_y}{\partial y})$ .

Bringing all these fluxes together we get

$$
\dot{H}\delta x \delta y = a\delta x \delta y + q_x\delta y + q_y \delta x - \delta y\left(q_x+ \delta x \frac{\partial q_x}{\partial x}\right) - \delta x\left(q_y+ \delta y \frac{\partial q_y}{\partial y}\right)
$$

The $q_y \delta x$ and $q_x\delta y$ cancel leaving

$$
\dot{H}\delta x \delta y = a\delta x \delta y - \delta y\delta x \frac{\partial q_x}{\partial x} - \delta x \delta y \frac{\partial q_y}{\partial y}
$$

Finally,  $\delta y \delta x$ cancels leaving
$$
\dot{H} = a -  \frac{\partial q_x}{\partial x} -  \frac{\partial q_y}{\partial y}.
$$

This can be represented by 

$$
\dot{H} = a -  \nabla_h\cdot\underline{q}, 
$$

where $\nabla_h$ is the del operator in the horizontal direction only: $\nabla_h = \frac{\partial}{\partial x} + \frac{\partial}{\partial y}$.







