## Stress balance equations
For a body undergoing negligible acceleration compared to the magnitude of the forces involved, $F=ma$ simplifies to $\Sigma F_i = 0$, meaning that all the forces acting on the body must add up to zero.

Consider a cube with density $\rho$, sides with size $\delta x$, $\delta y$, and $\delta z$, and volume $V = \delta x \delta y \delta x$:

![image](https://user-images.githubusercontent.com/33917430/201834366-79cc03de-220d-4775-b9be-eb4973d6af16.png)

The cube's stress state can be described through the stress tensor $\underline{\underline{\sigma}}$ where the normal and shear stress components are denoted by $\sigma_{ij}$ and $\tau_{ij}$, respectively, such that: 

$$\underline{\underline{\sigma}}=\begin{bmatrix}
   \sigma_{xx} & \tau_{xy} &\tau_{xz} \\
   \tau_{yx} & \sigma_{yy} & \tau_{yz}\\
   \tau_{zx}&\tau_{zy}&\sigma_{zz}
\end{bmatrix}$$

Let's now consider the stresses on the cube's different faces and the gravitational force acting in the $z$-direction. Note that here we consider forces as positive upwards and we are considering the forces acting *on* the cube. So, for example, a force acting to push the cube upwards is considered positive. 

![image](https://user-images.githubusercontent.com/33917430/201834410-3954ce95-2b78-44d5-a583-6573990e96b8.png)



### Gravity

The force of gravity is simply the volume of the cube times its density times the acceleration due to gravity, $g$:

$$
\rho g \delta x \delta y \delta x
$$

### The $z$ faces
Next we will look at the forces acting on the two faces with normals in the $z$ direction (the top and bottom of the cube). The normal stress $\sigma_{zz}$  acts to stretch the material vertically, so at the bottom face the material around the cube is pulling the cube down - according to our sign convention this is $-\sigma_{zz}$. To get the force associated with this stress we simply multiply it by the area over which is acts:  

$$
-\sigma_{zz} \delta x \delta y
$$

At the top of the cube the stress is (in general) slightly different than $\sigma_{zz}$ in magnitude because we have moved a distance $\delta z$ from the bottom face. Using the same procedure we have used in several previous derivations, we express this difference using the $z$ derivative of $\sigma_{zz}$:

$$
\sigma_{zz}+\frac{\partial\sigma_{zz}}{\partial z}\delta z.
$$

Note that this is a positive stress because at this face the material around the cube is pulling the cube upwards.

Multiplying by the area over which this stress acts gives the force at the upper face of the cube:

$$
\left(\sigma_{zz}+\frac{\partial\sigma_{zz}}{\partial z}\delta z\right)\delta y \delta x.
$$

### The $x$ faces
At the other four faces shear stresses act in the $z$ direction. We apply the same procedure to the left face to get the force acting there:

$$
-\tau_{xz}\delta z \delta y
$$

In general, positive horizontal shear stress involves the right side of any interface pulling up and the left side pulling down. So in the case of the left face of our cube, positive shear pulls downwards on the cube, so that's why the expression above is negative. 

On the right face the force is 

$$
\left(\tau_{xz}+\frac{\partial\tau_{xz}}{\partial x}\delta x\right)\delta z \delta y
$$

### The $y$ faces
Applying the same approach to the $y$ faces gives

$$
-\tau_{yz}\delta z \delta x
$$

and

$$
\left(\tau_{yz}+\frac{\partial\tau_{yz}}{\partial y}\delta y\right)\delta z \delta x.
$$

## Bringing it together
Summing the forces defined in the six expressions above and equating to zero gives


$$
0 = -\rho g\delta x \delta y \delta z-\sigma_{zz}\delta y \delta x + \left(\sigma_{zz}+\frac{\partial\sigma_{zz}}{\partial z}\delta z\right)\delta y \delta x \\
-\tau_{yz}\delta z \delta x + \left(\tau_{yz}+\frac{\partial\tau_{yz}}{\partial y}\delta y\right)\delta z \delta x\\
-\tau_{xz}\delta z \delta y + \left(\tau_{xz}+\frac{\partial\tau_{xz}}{\partial x}\delta x\right)\delta z \delta y
$$

which simplifies to:

$$0 = -\rho g + \frac{\partial \sigma_{zz}}{\partial z}+\frac{\partial \tau_{yz}}{\partial y}+\frac{\partial \tau_{xz}}{\partial x}$$

Performing a similar analysis in the $x$- and $y$-directions yields:

$$
0 =  \frac{\partial \sigma_{xx}}{\partial x}+\frac{\partial \tau_{yx}}{\partial y}+\frac{\partial \tau_{zx}}{\partial z}
$$

$$
0 = \frac{\partial \sigma_{yy}}{\partial y}+\frac{\partial \tau_{xy}}{\partial x}+\frac{\partial \tau_{zy}}{\partial z}.
$$

Together, these three equations form the static stress balance equations, also known as Stokes equations.

## Deviatoric stresses
Given a mean (normal) stress defined as $\sigma_m = \frac{1}{3}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$, the deviatoric stress tensor, $\underline{\underline{\tau}}$, is defined as $\underline{\underline{\tau}}=\underline{\underline{\sigma}}-\sigma_m\underline{\underline{I}}$ such that:

$$
\underline{\underline{\tau}} = \begin{bmatrix}
   \sigma_{xx}-\sigma_m & \tau_{xy} &\tau_{xz} \\
   \tau_{yx} & \sigma_{yy}-\sigma_m & \tau_{yz}\\
   \tau_{zx}&\tau_{zy}&\sigma_{zz}-\sigma_m
\end{bmatrix}
$$

Note that only the normal stresses $\sigma_{ij}$ differ between $\underline{\underline{\tau}}$ and $\underline{\underline{\sigma}}$ -- shear stresses $\tau_{ij}$ are the same. 

$\sigma_m$ is the component of the stress that does not vary with direction (i.e. its isotropic). It tries to change the volume of our material. Removing it from the total stress $\underline{\underline{\sigma}}$ leaves only the component of stress that does vary with direction, $\underline{\underline{\tau}}$, which tries to change the shape of our material.

$\underline{\underline{\tau}}$ is particularly useful for glaciology because we can often assume that ice is incompressible, so to a first approximation, $\sigma_m$ does not affect flow, whereas $\underline{\underline{\tau}}$ does. It is $\underline{\underline{\tau}}$ which appears in ice flow laws.  

## Glen's flow law
Glen's flow law is the most common flow law used to describe the viscous flow of ice in glaciology. So far we have written is as $\dot{\epsilon} = A\tau^n$, without specifying which stress $\tau$ and strain rate $\dot{\epsilon}$ are involved. A more complete formulation is:

$$
\dot{\epsilon_{ij}} = A\tau_E^{n-1}\tau_{ij}
$$

where $\tau_{ij}$ are the elements of the deviatoric stress tensor $\underline{\underline{\tau}}$ and $\tau_E$ is the so-called effective stress, defined as the second invariant of the deviatoric stress tensor as:

$$
\tau_E^2 = \frac{1}{2}(\tau_{xx}^2+\tau_{yy}^2+\tau_{zz}^2)+\tau_{xz}^2+\tau_{xy}^2+\tau_{yz}^2
$$
