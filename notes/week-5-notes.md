# Notes from week 5

## Examples of visco-elastic rheologies in our research areas (and systems which behave kind of viscoelasticly)
   - GIA -- the mantle is viscos and elastic, the lithosphere is elastic
   - ice sheets on tidal timescales
   - poroelastic deformation in aquifers (the time delayed behavior comes from water flow)
   - firn models which get viscous-like behavior from air flow through the firn. 

## What does 'instantaneous' mean in the context of elastic deformation?

 - its not really instantaneous and all the talk of seismic/sound waves propagating through materials being evidence of them deforming elastically was confusing, because it makes it sound like sounds wave should have infinite speed. 
- what our discussion neglected was the acceleration terms in the equations. 


## Fields

Fields are functions/variables that have a value defined at every point in space or time. Common fields in glaciology at temperature $T$, velocity $\underline{u}$, stress $\sigma$. These are vary in the three spatial dimensions $x$, $y$, and $z$, and time $t$.

### Scalar fields
Scalar fields are fields that only need one value in each location in space and time to define them. Examples are temperature $T$, ice-surface slope $S$, age $A$, and speed. 

We denote a scalar field simply as $T(x,y,z,t)$.

### Vector fields
Vector fields are more complicated. At each point in space, rather than just a scalar quantity we have a vector pointing in a specific direction in space. Therefore at each point in space and time, we require as many values as we have spatial dimensions. 

Examples of vector fields in glaciology as velocity $\underline{u}$, the gradient of the ice-surface, 

We denote vector fields with an underline as tend (at least when we first define them) write out their components, e.g.,

$$
\underline{u} = (u, v, w)
$$

These are typical symbols for the three components in glaciology, with $u$ as the horizontal component of velocity in direction of the large scale flow of the ice sheet (i.e. along the $x$ axis), $v$ being the horizontal component perpendicular to this (i.e. along the $y$ axis), and $w$ being hte vertical component (i.e. along the $z$ axis). Note the potential for confusion between the vector field $\underline{u}$ and its $x$-component $u$.

Each of the components are functions of space and time, so we could write the whole thing verbosely as

$$
\underline{u}(x,y,w,t) = (u(x,y,w,t), v(x,y,w,t), w(x,y,w,t)).
$$

## The del operator
The del operator is a vector of differential operators. A differential operator can operate on functions and the result of the operation is the differential of the function. 

We can also think of it as a vector which has one component for each spatial dimension. So if we are considering a two-dimensional model del has two components corresponding to this two directions. 

Each component is the differential operator corresponding to differentiation *in the corresponding direction*. So in two dimensions del is defined as 

$\underline{\nabla} = \left(\frac{\partial}{\partial x} , \frac{\partial}{\partial y} \right)$

This notation with a comma in the middle is used to denote the two components of the vector $\frac{\partial}{\partial x}$ and $\frac{\partial}{\partial y}$. Individually, these two components caneach act on a scalar field and when they do they compute how rapidly the scalar field varies (i.e. is gradient) in the corresponding direction. 

For example, if our ice sheet surface elevation is defined by the sclar field $h(x,y)$ (i.e. is it a function of our two coordinates $x$ and $y$), then the two components of del can individually act on $h$ giving us the gradients of $h$ in the two directions:  $\frac{\partial h}{\partial x}$ and $\frac{\partial h}{\partial y}$. The gradients are themselves scalar fields because they vary in $x$ and $y$. 

### Grad

Instead of having each component of del operate on our scalar field individually, we can simply write $\underline{\nabla} h$, which is the same as writing 

$\underline{\nabla}h = \left(\frac{\partial h}{\partial x} , \frac{\partial h}{\partial y} \right)$

The gradients of $h$ in each direction (which, remember, are scalar fields) have been inserted in as the two components of the *vector* field $\underline{\nabla}h$. In other words, $\underline{\nabla}h$ is a vector field in which the $x$-component is $\frac{\partial h}{\partial x}$ and the $y$-component is $\frac{\partial h}{\partial y}$. This is referred to as the grad operator. 

### Divergence
Del is also useful for analyzing vector fields. One way to apply it to a vector field is to use the dot product. The dot product is the sum of the products of the components of two vectors. For example, for two vectors $\underline{A}$ and $\underline{B}$, each with components in the $x$ and $y$ direction denoted with subscripts ($A_x$, $A_y$, $B_x$, and $B_y$), the dot product is 

$$
\underline{A} \cdot \underline{B} = A_x B_x + A_y B_y
$$

Let's use the velocity field defined above as our vector field $\underline{u} = (u,w)$.


Remembering that the $x$ and $y$ components of del are $\frac{\partial h}{\partial x}$ and $\frac{\partial h}{\partial y}$, we can write down 

$$
\underline{\nabla} \cdot \underline{u} = \left(\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} \right)
$$

This is called the divergence of the velocity field. Later we will show using mass conservation that is proportional to the rate of change of porosity, $\phi$:

$$
\frac{\partial \phi}{\partial t} = (1- \phi) \underline{\nabla} \cdot \underline{u} 
$$

We usually we assume that porosity is zero everywhere. In other words we assume that in a bulk sense the ice is incompressible. This means that we can usually assume 

$$
\underline{\nabla} \cdot \underline{u} =0, 
$$

which is really useful in many ice sheet modelling and data analysis tasks. 


## Relationship between normal strain rate and velocity fields
Normal strain is deformation which changes the length, or volume, of a material element. It is defined as fractional change in length:

$$
\epsilon_{xx} = \frac{\Delta L}{L}
$$

THe rate of change of strain (the strain rate) is denoted $\dot{\epsilon}$ and this is related to gradients in the velocity field as follows


$$
\dot{\epsilon}_{xx} = \frac{\partial u}{\partial x}
$$


Proof if this: Consider a segment of ice within a glacier ice that is $L$ long in the $x$ direction. It is in a velocity field $\underline{u}(x) = u(x)$ which only varies in the $x$ direction. Arbitrarily we say that the velocity at the left side of the block is $u$ Therefore the ends of the block move at different speeds. Let's define the $x=0$ at the left side of the block. 

After a time $\Delta t$, the left side of the block has moved from $x=0$ to $x = u\Delta t$. 

The right side of the block moves at a velocity of $u + L\frac{\partial u}{\partial x}$. To understand this, consider that the spatial gradient in $u$ ($\frac{\partial u}{\partial x}$) expresses how much $u$ increases for every meter you shift in the $x$ direction. So to get the difference in the velocity between the left side of the block and the right is simply this gradient times the length of the block $L$. This approach is valid as long as we consider the distance $L$ small enough that $u$ varies linearly. 

In the $\Delta t$ the right side of the block has moved $\Delta t(u + L\frac{\partial u}{\partial x})$. It started at $x = L$, so its new position is $L + \Delta t(u + L\frac{\partial u}{\partial x})$


Now, if the left side is at  $x = u\Delta t$ and the right side of the block is  at $x = L+ \Delta t(u + L\frac{\partial u}{\partial x})$, the new length of the block, after this period of time $\Delta t$ it has spent in this velocity field is 
$$
L + \Delta t(u + L\frac{\partial u}{\partial x}) - \Delta t u = L + \Delta t L\frac{\partial u}{\partial x}
$$

and the change in length is

$$
\Delta L = L + \Delta t L\frac{\partial u}{\partial x} - L = \Delta t L\frac{\partial u}{\partial x}.
$$

Rearranging shows that the total strain in a time $\Delta t$ is

$$
\epsilon_{xx} = \Delta t \frac{\partial u}{\partial x}.
$$

Dividing through by the time gives us the relationship between strain rate and velocity gradients

$$
\dot{\epsilon}_{xx} = \frac{\partial u}{\partial x}.
$$


[We will go over tenor notation next week]

## Computing the slope of the ice sheet surface from data in the cloud. 

This notebook demonstrates how to compute the gradient field of the ice sheet surface from continent-wide data using cloud computing. 

https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/main/code/gradient.ipynb
