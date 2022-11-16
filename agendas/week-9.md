# Agenda, week 9

## Shallow ice approximation 

Starting with the stress balance equations

$$
\frac{\partial \sigma_{xx}}{\partial x}+\frac{\partial \tau_{yx}}{\partial y}+\frac{\partial \tau_{zx}}{\partial z} = 0\\
$$


$$
\frac{\partial \tau_{xy}}{\partial x} + \frac{\partial \sigma_{yy}}{\partial y} +\frac{\partial \tau_{zy}}{\partial z} = 0
$$


$$
\frac{\partial \tau_{xz}}{\partial x}+\frac{\partial \tau_{yz}}{\partial y}+\frac{\partial \sigma_{zz}}{\partial z} = \rho g
$$




we will derive an equation for the ice flux $q$ in one horizontal dimension:  

$$
q = \int^H_0 u(z) dz
$$

(This is the volume of ice passing a flow horizontally past a location per unit time, per unit width across flow.)

The depth integral in the expression above is a hint that this is a depth-integrated ice-flow model, meaning that the final model ill consider the stresses, fluxes, and velocities in a depth integrated/averaged sense, which does not resolve variations in these properties with depth.(Although some of the equations that we see along the way *can* be used to compute some of these as functions of $z$.)

Note that in the stress balance equations above we have three equations and nine unknowns - we cannot solve this system of equations without more information. In the a 'full-stokes' model this information comes from the rheology. In our case we will make simplifications until we have two equations and two unknowns. 


## Reduce to two dimensions, $x$ and $z$
The first step is drop the $y$ dimension. We are just considering how properties vary in $x$ and $z$, so all terms in the stress balance that include a $y$ are assumed to be zero: 

$$
\frac{\partial \sigma_{xx}}{\partial x}+\frac{\partial \tau_{zx}}{\partial z} = 0\\
$$

$$
\frac{\partial \tau_{xz}}{\partial x}+\frac{\partial \sigma_{zz}}{\partial z} = \rho g
$$

You can think of this as an assumption that the ice is a vertical slice of ice with zero thickness in the $y$ direction, or (probably more helpfully) you can think of it as an assumption that the ice has infinite across-flow width and no properties vary in that across-flow direction. The latter assumption is a good one in some real-world scenarios, so it seems reasonable to make this assumption here to simplify the maths. 

## Substitute in deviatoric stress
As defined in last week's session, the deviatoric stress is the component of the stress tensor that varies in direction. It is related to the total stress by

$$
\underline{\underline{\tau}}=\underline{\underline{\sigma}}-\sigma_m\underline{\underline{I}}
$$

where the mean stress $\sigma_m = \frac{1}{3}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$ and $\underline{\underline{I}}$ is the identity tensor. Element-wise this means 

$$
\sigma_{xx} = \tau_{xx} + \sigma_{m}
$$

$$
\sigma_{zz} = \tau_{zz} + \sigma_{m}
$$

and therefore 
$$
\frac{\partial \sigma_{xx}}{\partial x} = \frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \sigma_{m}}{\partial x}
$$

$$
\frac{\partial \sigma_{zz}}{\partial z} = \frac{\partial \tau_{zz}}{\partial z} + \frac{\partial \sigma_{m}}{\partial z}
$$

Substituting these two expressions into the stress balance equation gives

$$
\frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \sigma_{m}}{\partial x}+\frac{\partial \tau_{zx}}{\partial z} = 0\\
$$

$$
\frac{\partial \tau_{xz}}{\partial x}+\frac{\partial \tau_{zz}}{\partial z}+\frac{\partial \sigma_{m}}{\partial z} = \rho g
$$


## Drop stress terms - the 'Shallow Ice Approximation'
Next, we make *part of* what is called the 'Shallow Ice Approximation'. Based on the assumption that the ice is much wider than it is tall (i.e. the aspect ratio is very large), we neglect the variation of stresses in the $x$ direction. We also assume the vertical stress is hydrostatic (i.e. $\frac{\partial \tau_{zz}}{\partial z} =0$).


These is a serious simplifications. They means that our model will not be applicable to places where the bed slope varies rapidly, the bed is very slippery, at the grounding line, in ice shelves, or at ice divides. In all these cases, the terms we are about to neglect are likely to be very important and should not be ignored. We would need to retain some (or all) of these terms in the stress balance to have a hope of realistically simulating ice flow in those places. Nonetheless, neglecting them here can help us to understand the basics of ice sheet flow and we can come back to more sophisticated models later. 

Neglecting the variation of stresses in the $x$ direction and $\frac{\partial \tau_{zz}}{\partial z}$ in the stress balance equations leaves

$$
 \frac{\partial \sigma_{m}}{\partial x}+\frac{\partial \tau_{zx}}{\partial z} = 0\\
$$

$$
\frac{\partial \sigma_{m}}{\partial z} = \rho g
$$

We started with three equations and nine unknowns. The simplifications above have reduced the model to two equations and two unknowns. Therefore, as long as have boundary conditions, we can solve this system of equations to get the stresses, then use the result with the flow law to get ice flux. 

## Integrate the $z$ equation vertically 
Our first challenge is to combine these equations so that we get an expression for $\tau_{zx}$. The first step is to integrate the $z4 equation vertically. Integrating both sides gives

$$
\int^0_{\sigma_m} d \sigma_m = \rho g \int^H_z dz
$$

where we have used the limits of integration to impose a boundary condition at the upper surface, $z=H$, of $\sigma_m(z=H) = 0$.

Evaluating ths integrals gives

$$
\sigma_m = -\rho g (H-z)
$$

i.e. as expected, the mean normal stress is negative (compressive) and increasing with depth from the surface at a rate proportional to the strength of gravity and the density of ice.

## Differentiate horizontally
Next we differentiate this expression horizontally to get

$$
\frac{\partial \sigma_{m}}{\partial x} =- \rho g \frac{\partial H}{\partial z}
$$

Substituting this into the $x-direction stress balance equation shows

$$
\frac{\partial \tau_{zx}}{\partial z} = \rho g \frac{\partial H}{\partial z}
$$

Noting that $\frac{\partial H}{\partial z}$ is usually negative, this expression suggests that the vertical shear stress $\tau_{zx}$ decreases with $z$. 

## Integrate vertically 
To get an expression for $\tau_{zx}$ we need to integrate this vertically: 

$$
 \int^{\tau_{zx}}_0 \tau_{zx} dz = \rho g H \int^z_H  dz
$$

where we have imposed the boundary condition $\tau_{zx}(z=H) = 0$, i.e.  there is no shear stress exerted by the air on the ice sheet at the surface. 
