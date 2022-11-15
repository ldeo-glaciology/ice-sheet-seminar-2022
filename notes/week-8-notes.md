## Stress balance equations
For a body undergoing negligible acceleration (compared to the magnitude of the forces involved), $F=ma$ simplifies to $\Sigma F_i = 0$, meaning that all the forces acting on the body must add up to zero.

Consider a cube with density $\rho$, sides with size $\delta x$, $\delta y$, and $\delta z$, and volume $V = \delta x \delta y \delta x$:

![628255f7cb3f213bb6b73de6c60c0232.png](../../_resources/628255f7cb3f213bb6b73de6c60c0232.png)
The cube's stress state can be described through the stress tensor $\underline{\underline{\sigma}}$ where the normal and shear stress components are denoted by $\sigma_{ij}$ and $\tau_{ij}$, respectively, such that: 
$$\underline{\underline{\sigma}}=\begin{bmatrix}
   \sigma_{xx} & \tau_{xy} &\tau_{xz} \\
   \tau_{yx} & \sigma_{yy} & \tau_{yz}\\
   \tau_{zx}&\tau_{zy}&\sigma_{zz}
\end{bmatrix}$$
Let's now consider the stresses on the cube's different faces and gravitational force acting in the $z$-direction. Note that here we consider stresses (i.e., forces) exerted by the cube onto its surroundings as positive:

![729605f84fb89c8a3f9015e7b50808e3.png](../../_resources/729605f84fb89c8a3f9015e7b50808e3.png)
We can compute the sum of forces acting in the $z$-direction by multiplying each stress component $\sigma_{ij}$ by the area on which it is acting:
$$ 0 = -\rho g\delta x \delta y \delta z-\sigma_{zz}\delta y \delta x + \left(\sigma_{zz}+\frac{\partial\sigma_{zz}}{\partial z}\delta z\right)\delta y \delta x \\
-\tau_{yz}\delta z \delta x + \left(\tau_{yz}+\frac{\partial\tau_{yz}}{\partial y}\delta y\right)\delta z \delta x\\
-\tau_{xz}\delta z \delta y + \left(\tau_{xz}+\frac{\partial\tau_{xz}}{\partial x}\delta x\right)\delta z \delta y$$
which simplifies to:
$$0 = -\rho g + \frac{\partial \sigma_{zz}}{\partial z}+\frac{\partial \tau_{yz}}{\partial y}+\frac{\partial \tau_{xz}}{\partial x}$$
Performing a similar analysis in the $x$- and $y$-directions yields:
$$0 =  \frac{\partial \sigma_{xx}}{\partial x}+\frac{\partial \tau_{yx}}{\partial y}+\frac{\partial \tau_{zx}}{\partial z}$$
$$0 = \frac{\partial \sigma_{yy}}{\partial y}+\frac{\partial \tau_{xy}}{\partial x}+\frac{\partial \tau_{zy}}{\partial z}$$
Together, these 3 equations form the static stress balance equations also known as Stokes equations.

## Deviatoric stresses
Given a mean (normal) stress defined as $\sigma_m = \frac{1}{3}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$, the deviatoric stress tensor, $\underline{\underline{\tau}}$, is defined as $\underline{\underline{\tau}}=\underline{\underline{\sigma}}-\sigma_m\underline{\underline{I}}$ such that:
$$\underline{\underline{\tau}} = \begin{bmatrix}
   \sigma_{xx}-\sigma_m & \tau_{xy} &\tau_{xz} \\
   \tau_{yx} & \sigma_{yy}-\sigma_m & \tau_{yz}\\
   \tau_{zx}&\tau_{zy}&\sigma_{zz}-\sigma_m
\end{bmatrix}$$
Note that only the normal stresses $\sigma_{ij}$ differ between $\underline{\underline{\tau}}$ and $\underline{\underline{\sigma}}$ -- shear stresses $\tau_{ij}$ are the same. 

## Glenn's flow law
Glenn's flow law is often written as $\dot{\epsilon} = A\tau^n$ without specifying which stress $\tau$ and strain rate $\dot{\epsilon}$ are involved.  A more complete formulatio is:
$$\dot{\epsilon}_{ij} = A\tau_E^{n-1}\tau_{ij}$$
where $\tau_{ij}$ are the elements of the deviatoric stress tensor $\underline{\underline{\tau}}$ and $\tau_E$ is the so-called effective stress defined as the second invariant of the deviatoric stress tensor as:
$$\tau_E^2 = \frac{1}{2}(\tau_{xx}^2+\tau_{yy}^2+\tau_{zz}^2)+\tau_{xz}^2+\tau_{xy}^2+\tau_{yz}^2