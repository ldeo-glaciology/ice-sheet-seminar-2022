# Notes from week 7



## Shear strain rate

Consider the initially square material in this figure

![shear_diagram](https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/8e01bdd20c3a2ce6da583e3336396285c8fd1ccd/images/shear_diagram.jpg)

It undergoes some shear over a time $\delta t$ and the angle in the interior of bottom left corner of the square is reduced from a right angle to an angle of $\pi/2 - \theta_1 - \theta_2$.

We define the shear strain as half the reduction in this angle 

$$ 
\epsilon_{xy} = \frac{1}{2}\left(\theta_1 + \theta_2\right).
$$

We assume that $\underline{u} = 0$ at the bottom left corner of the element. From the geometry of the system, i.e. using 'tan = opposite of adjacent', 

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


### A more complicated derivation of mass balance

Another form of the depth-integrated mass balance equation can be derived, starting with $\nabla\cdot\underline{u} = 0$. 

Shifting to two spatial dimensions we have 

$$
\underline{u} = (u(x,z), w(x,z)); \quad \underline{q} = q_x = \int^{s(x)}_{b(x)} u(z) dz.
$$

and
$$
\nabla\cdot\underline{u} = \frac{\partial u}{\partial x} + \frac{\partial w}{\partial w}=0,
$$

where $b$ is the elevation of the base of the ice sheet and $s$ is the elevation of the ice surface. Rearranging gives 
$$
\frac{\partial w}{\partial z} = - \frac{\partial u}{\partial x}.
$$

Integrating between the bed and the surface gives

$$
\int^{w_s}_{w_b} dw = - \int^{s(x)}_{b(x)}\frac{\partial u}{\partial x} dz,
$$

where $w_s$ is the vertical velocity at the surface and $w_b$ is the vertical velocity at the base. The rate at which the ice surface goes up or down, $\dot{s}$, is related to the ice-equivalent accumulation rate $a$, the vertical velocity at the surface $w_s$, and advection of upstream ice-surface-height: 

$$
\dot{s} = w_s + a - u_s \frac{\partial s}{\partial x}.
$$

or, rearranging,

$$
w_s = \dot{s}-a+u_s \frac{\partial s}{\partial x}.
$$

To understand the last term in the equation above, consider that the slope $\frac{\partial s}{\partial x}$ shows how much the surface height changes for every meter you move in the $x$ direction. So if the ice is moving in that direction a distance $u$ every second, the height of the ice changes due to this 'advection' effect by $u \frac{\partial s}{\partial x}$ every second. 

Note that the above equation is sometimes called a kinematic equation for the ice surface height, $\dot{s}$. In a non-depth-integrated ice-sheet model, this is the equation used to move the ice-surface up and down. 

The same arguments applies at the bottom of the ice sheet (or 'ice base') where it is in contact with rock, sediment, or water. If we define melting $m$ as positive if mass is being removed, we get: 

$$
\dot{b} = w_b + m - u_b \frac{\partial b}{\partial x}.
$$

or, rearranging,

$$
w_b = \dot{b}-m+u_b \frac{\partial b}{\partial x}.
$$

Evaluating the integral on the left of our main equation above gives. 

$$
w_s - w_b = - \int^{s(x)}_{b(x)}\frac{\partial u}{\partial x} dz,
$$

and substituting in the two expressions for $w_s$ and $w_b$ gives

$$
\dot{s}-a+u_s \frac{\partial s}{\partial x} - \left(\dot{b}-m+u_b \frac{\partial b}{\partial x}\right) = - \int^{s(x)}_{b(x)}\frac{\partial u}{\partial x} dz. 
$$

To evaluate the integral on the right, we need to be careful of the limits because they are functions of $x$, so we cannot just move the differential operator out of the integral. To make progress we use the [Leibniz integration rule](https://en.wikipedia.org/wiki/Leibniz_integral_rule) to show

$$
-\int^{s(x)}_{b(x)}\frac{\partial u}{\partial x}\,dz = u_s \frac{\partial s}{\partial x} - u_b \frac{\partial b}{\partial x}  - \frac{\partial}{\partial x} \int^{s(x)}_{b(x)} u\, dz.
$$

To understand what this rule means, we can rearrange by moving the last term of the right over to the left and the left side over to the right, leading to

$$
\frac{\partial}{\partial x} \int^{s(x)}_{b(x)} u\, dz
 = u_s \frac{\partial s}{\partial x} - u_b \frac{\partial b}{\partial x}  + \int^{s(x)}_{b(x)}\frac{\partial u}{\partial x}\,dz.
$$

This says that the derivative with respect to $x$ of an integral with limits that are functions of $x$, is equal to the sum of the integral of the derivative of the function and two additional terms that take account of the dependence of the limits on $x$.

The left side is the flux divergence and we can see that is increases with the surface slope and decreases with the slope of the bed. This makes sense because, all else being equal, if the surface slope is larger (i.e. more positive, or less negative) the flux divergence increases - the flux increase for $x$ more rapidly.

Applying the Leibniz integration rule, our full equation is 

$$
\dot{s}-a+u_s \frac{\partial s}{\partial x} - \left(\dot{b}-m+u_b \frac{\partial b}{\partial x}\right) = u_s \frac{\partial s}{\partial x} - u_b \frac{\partial b}{\partial x}  - \frac{\partial}{\partial x} \int^{s(x)}_{b(x)} u\, dz.
$$

We see that the slope terms cancel, i.e. the flux divergence and the rate of change of surface elevation both depend on the surface and basal slopes in exactly the same way and the two effects cancel. This leaves

$$
\dot{s}-a - \left(\dot{b}-m\right) =  - \frac{\partial}{\partial x} \int^{s(x)}_{b(x)} u\, dz.
$$

Recongnizing that $s-b = H$, so $\dot{s}-\dot{b} = \dot{H}$, leaves
$$
\dot{H}-a  +m =  - \frac{\partial}{\partial x} \int^{s(x)}_{b(x)} u\, dz.
$$

Rearranging and using our definition of flux we finally get

$$
\dot{H} = a-m - \frac{\partial q}{\partial x},
$$

which in two hrizontal dimensions is 

$$
\dot{H} = a -  m - \nabla_h\cdot\underline{q}. 
$$

This is the same as we had before except that it includes the minor addition of basal melting $m$. However, the slightly more rigorous derivation does four things for us: 
1. it shows that this equation does not assume that the base and surface are flat, which isn't obvious from the simpler derivation,
2. it links the general mass balance equation ($\nabla\cdot\underline{u} = 0$) to this depth-averaged version used in ice sheet models, 
3. it highlights the fact that we indeed need to integrate vertically (i.e. 'depth-integrate') to derive it, and 
4. it lead us to also derive the kinematic condition for the ice surface ($\dot{s} = w_s + a - u_s \frac{\partial s}{\partial x}.$).





