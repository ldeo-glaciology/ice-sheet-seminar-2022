# Notes from week 6

## Vector calc review
  - gradient: $\vec{\nabla} h$
    - converts a scalar field (i.e. height) to a vector field
    - gives direction of steepest slope

  - divergence: $\vec{\nabla} \cdot \vec{u}$
    - converts a vector field (i.e. velocity) to a scalar field
    - intuitively, gives flux by summing together gradients in velocity components (i.e. strain rates)
       - $\vec{\nabla} \cdot \vec{u} = \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z}$
    - negative divergence indicates compression (mass accumulating) - can picture squishing a sponge if that helps
    - we generally assume ice is incompressible ( $\vec{\nabla} \cdot \vec{u} = 0$ ), but this isn't quite true because of air bubbles trapped in the ice
    - say we are looking at ice constrained in the y-direction, and assuming incompressibility:
        - $\frac{\partial w}{\partial z} + \frac{\partial u}{\partial x} = 0 \rightarrow \frac{\partial w}{\partial z} = - \frac{\partial u}{\partial x}$
        - can measure horizontal velocity $u$ at one location, and vertical velocity $w$ throughout a column of ice, to calculate $u$ everywhere (see Jonny's paper: [Ice-flow reorgnization in West Antarctica 2.5 kyr ago dated using radar-derived englacial flow velocities](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2016GL070278)) 

## Stress and strain rate tensors

### a note on notation

Consider a strain rate  tensor component, $\dot \varepsilon_{xy}$.
  - $\varepsilon$ indicates strain
  - the dot indicates a time derivative (i.e. strain rate)
  - the first subscript (x, in this example) denotes the **plane** in which the strain is acting
  - the second subscript (y, in this example) denotes the **direction** in which the strain is acting

### stress

We denote stress with a sigma, $\sigma$.

  - **normal stresses** exert force in the same direction as the face they are acting on, i.e. perpendicular to the surface ( $\sigma_{xx}$, $\sigma_{yy}$)
  - **shear stresses** exert force perpendicularly to the face they are acting on, i.e. changing the *shape* of an object, not the direction ( $\sigma_{xy}$, $\sigma_{yx}$)

A two-dimensional stress tensor can be expressed as follows:

$$
\underline{\underline{\sigma}} =
\left(\begin{array}{cc} 
\sigma_{xx} & \sigma_{zx}\\ 
\sigma_{xz} & \sigma_{zz}
\end{array}\right)
$$ 

### strain rate

A two-dimensional strain rate tensor can be expressed as follows:

$$
\underline{\underline{\dot \varepsilon}} =
\left(\begin{array}{cc} 
\dot \varepsilon_{xx} & \dot \varepsilon_{zx}\\ 
\dot \varepsilon_{xz} & \dot \varepsilon_{zz}
\end{array}\right)
$$

Recall from last week that each component of the strain rate tensor $\dot \varepsilon_{ij}$ for an ice sheet is equal to how velocity in the $j$ direction changes with distance in the $i$ direction.
  - $\dot \varepsilon_{xx} = \frac{\partial u}{\partial x}$
  - $\dot \varepsilon_{zz} = \frac{\partial w}{\partial z}$
  - $\dot \varepsilon_{xz} = \frac{\partial w}{\partial x}$
  - $\dot \varepsilon_{zx} = \frac{\partial u}{\partial z}$
    - this component is the most relevant in a slow-moving parts of an ice sheet, as it tells us how horizontal velocity changes with depth

## Driving stress

Driving stress drives ice flow.

Imagine a column of ice. The pressure at each depth $z$ can be expressed as $P = \rho g z$, where:
  - $\rho$ is the density of ice ( $~9.17 kg/m^3$)
  - $g$ is gravitational acceleration ( $~9.8 m/s^2$)
  - $z$ is the depth beneath the surface
  - $\partial y$ is the thickness of the ice column

Therefore, the pressure gradient with depth is $\frac{dP}{dz} = \rho g \partial y$.

![image](https://user-images.githubusercontent.com/90412051/196259608-df6514b0-1267-4b05-8365-447518651a39.png)

To calculate the force acting on one side of the ice column (blue arrow), with thickness H, we can consider that $F = P \times A = P(z) \times H \partial y$. Then, we can integrate over the height of the column to get the total force. We will call the force on the left-hand side of the column $F_1$:

$F_1 = \int_0^H P(z) \partial y dz$

$F_1 = \int_0^H \rho g z \partial y dz$

$F_1 = \frac{\rho g \partial y H^2}{2}$

Note that in this calculation, we have assumed constant $\rho$ and g, and that air pressure is negligible compared to ice pressure.

The more relevant quantity to consider here is not just the force acting on one side of the ice column, but rather the difference between the forces on either side. If we imagine that the ice column is part of an ice sheet with a sloping surface of grade $\frac{dH}{dx}$, and has thickness $\partial x$ in the x-direction, then the force acting on the opposite side of the ice column can be calculated as follows:

$F_2 = \frac{\rho g \partial y H_2^2}{2} = \frac{\rho g \partial y H^2}{2} + \partial x \frac{d}{dx}(\frac{\rho g \partial y H^2}{2})$

$\Delta F = F_1 - F_2 = \frac{\rho g \partial y H^2}{2} - (\frac{\rho g \partial y}{2}H^2 + \partial \frac{d}{dx}(\frac{\rho g \partial y H^2}{2}))$

$\Delta F = -\frac{\partial x \rho g \partial y}{2} \frac{\partial H^2}{\partial x} =$ net force on the column

We can now invoke the chain rule to rewrite this quantity as follows:

$\Delta F = -\frac{\partial x \rho g \partial y}{2} (2 H \frac{\partial H}{\partial x}) = -\partial x \rho g \partial y H \frac{\partial H}{\partial x}$

Now, we can solve for the driving stress $\vec{\tau_d}$:

$\vec{\tau_d} = \frac{\Delta F}{A} = \frac {\Delta F}{\partial x \partial y}$
$\vec{\tau_d} = - \rho g H \frac{\partial H}{\partial x}$

Note the similarities here to the ice flux equation in our toy model from week 2, where we said ice flux $q \propto -H'H$. This makes sense intuitively, as well; there is more driving stress where the ice is thicker (higher H) and steeper (higher $\frac{\partial H}{\partial x}$).

We can generalize this to two dimensions as follows:

$\vec{\tau_d} = - \rho g H (\frac{\partial H}{\partial x} \hat{i} + \frac{\partial H}{\partial y} \hat{j}) = - \rho g H \vec{\nabla} H$

The stress field will point in the direction in which slope changes the fastest.

## driving stress in the concept of a perfectly plastic model

In a perfectly plastic model, stress has to reach/exceed a yield stress value before there is any deformation. The material will then deform until it gets back to this yield stress value. So a steady state solution means that the stress on the material equals the yield stress.

The yield stress of ice ( $Y$) is often approximated as 100 kPa. If we say our driving stress $\tau_d$ is exactly the yield stress, we can do an order-of-magnitude calculation to determine a "typical" ice sheet slope.

$\tau_d = Y = 100 kPa$

$100 kPa = -\rho g H \frac{\partial H}{\partial x}$

For order-of-magnitude purposes, $\rho = 1000 kg/m^3$, $g = 10 m/s^2$, and $H = 1000m$. Therefore, we can solve for the slope of the ice sheet as:

$\frac{\partial H}{\partial x} = 0.01 \rightarrow 1$ % slope on "typical" ice sheet

Now, we can un-chain-rule our expression for driving stress in order to derive an expression for ice thickness $H(x)$ in a plastic model:

$\tau_d = Y = -\rho g \frac{\partial H}{\partial x}$

$Y = -\frac{1}{2} \frac{\partial H^2}{\partial x} \rho g$

$\frac{\partial H^2}{\partial x} = -\frac{2Y}{\rho g}$

$\int_0^{H^2} dH^2 = -\frac{2Y}{\rho g} \int_0^x dx$

$H^2 = -\frac{2Yx}{\rho g}$

$H(x) = \sqrt{\frac{2Yx}{\rho g}}$

After assigning a constant boundary condition for $H(0)$, the very simple profile described by the above equation makes a remarkably accurate picture of the Greenland Ice Sheet.

Note that ice is generally modeled/thought of as viscous, but some components may be plastic, and the plastic model does a surprisingly good job estimating the profile here.

## Preview of next week: shallow ice approximation

The shallow ice approximation assumes that all stresses except for *vertical shear stress* are negligible.  We can use Glen's Flow Law ( $\dot\varepsilon = A \tau^{n}$) to calculate the vertical strain rate, then express ice flux as follows:

$q = \frac{A}{n+2} (-\rho g \frac{\partial H}{\partial x})^n H^{n+2}$

And recall:

$\dot\varepsilon_{zx} = \frac{\partial u}{\partial z} = A \tau_d^n$

We can integrate this expression once to get $u(z)$, then a second time to get flux q. Note that this results in an incredibly strong dependence on thickness ( $H^5$). More on this next week...

