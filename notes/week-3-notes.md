# Notes from week 2

## Why are ice sheets steeper at the edges than in the middle?
Following on from the discussion last week, let's revisit the question of why ice sheets are stepper at the side than in the middle.

We will start with an example: 
In the slides we saw a radargram from Korff Ice Rise. It shows the classic ice sheet shape: higher in the middle than at the sides and steeper at the sides than in the middle. 
Radar measurements were used to get a "map" of the Korff ice rise's internal structure.
This observation for ice sheet concavity was the motivation for the following ice thickness model, under steady state conditions (and using conservation of mass):

$$
\frac{\partial H}{\partial t} = a - \frac{\partial q}{\partial x},
$$

where $H$ is ice thickness, $a$ is ice accumulation, and $q$ is ice flux. For simplicity we usd a toy model for $q$: 

$$
q = -H \frac{\partial H}{\partial x}.
$$


Note: 
this is an ill-posed problem on its own. 
So, the following boundary conditions are imposed for out problem to be well-posed:

$$
q(0,t) = 0 = H^{'}(0,t)
$$

$$
H(1,t) = H_{end}
$$

$$
H(x,0) = 1+ (-C)x 
$$

with $C$ representing some Real valued constant


### How can we solve this?

We can solve our model based on a depth-integrated mass balance numerically, using finite difference methods (See Python code from week 2).
When plotting $\frac{\partial q}{\partial x}$ we see that the spatial flux is initially uniform. We can write $q$ (using $q= -H \frac{\partial H}{\partial x}$ and the product rule):

$$
q = -H \frac{\partial H}{\partial x}  = - \frac{1}{2}[H \frac{\partial H}{\partial x} + H \frac{\partial H}{\partial x}]
\Rightarrow q = - \frac{1}{2} \frac{\partial H^2}{\partial x}
$$

Let $H(x,0) = 1- Cx$

$$
\Rightarrow [H(x,0)]^{2} = 1-2xC+C^{2}x^{2} 
\Rightarrow \frac{\partial^2}{\partial x^{2}} [H(x,0)]^{2} = 2C^{2}
$$

Given $$q = -\frac{1}{2} \frac{\partial H^{2}}{\partial x}$$ then 

$$
\frac{\partial q}{\partial x} = -\frac{1}{2} \frac{\partial^{2} H^{2}}{\partial x^{2}}
\Rightarrow \frac{\partial q(x,0)}{\partial x} = -\frac{1}{2} \frac{\partial^{2} H(x,0)^{2}}{\partial x^{2}} = -\frac{1}{2} (2C^{2}) = -C^{2}
$$

(the method of finite difference can be illustrated graphically. See here for a jupyter book explaining the finite difference method: https://pythonnumericalmethods.berkeley.edu/notebooks/chapter23.03-Finite-Difference-Method.html).

## Models can be simple or complex

An example of a simple model is that of a body falling (of mass m) in space, which has no other body force acting on it. According to Newtons second law, we can write

$$
F = ma
\Rightarrow mg = ma
\Rightarrow g = a
$$


This model illustrates that massive bodies require greater force acting on them.
This is a *very* simple model, but it demonstrates something fundamental about mathematical modelling: the process of getting to the final answer matters. THe asnwer $g=a$ expressing the importantresult --- that all objects accelerate at the same rateunder the same gravity field --- but the fact tha $m$ cancelled in the penultimate step provides the explanation why --- more massive objects take more force to accelerate at a given rate, but they also experience more force for a given gravity field and the two effects exactly cancel. 

## Ice flow (Rheological Properties)

To develop a more nuanced model of ice flowing (for example) we need to consider the rheological properties of ice.

Rheology = the study of the deformation and flow of a material (Hewitt pp. 2016; "Rheology". 
See: https://people.maths.ox.ac.uk/hewitt/slides/hewitt_karthaus_rheology.pdf ) 

Types of deformation include elastic, plastic, inelastic, brittle, etc.
We will define each of these terms as Maxwell did (see "The Viscosity of Ice" by Deeley, 1908):

- a viscous body = is considered one which undergoes permanent and continuous change in form under action of a given stress, however small (ex. water is a material with low viscosity)
- a plastic body = is one which requires a definite and often increasing stress to produce a continuous change in form; where such a material (under very small stress, and yields, at rates proportional to such stress) may be regarded as viscous, under this definition
- an elastic body = is one which returns to its original shape, after some applied stress, with no viscosity feature (if purely elastic) and which does not dissipate (heat) energy
- a viscoelastic body = is one that exhibits BOTH viscous and elastic characteristics under some applied stress, with a viscosity factor s.t. it has a time dependent strain rate (ex. solid water (ice) is viscoelastic)
- a brittle material = is one that experiences very little or NO recoverable deformation prior to fracture, and breaks when a great enough load is applied (ex. glass); i.e. it fractures with little to no elastic deformation when subjected to high enough stress (but how much stress depends on the material and its thickness)


Therefore, a constitutive (or flow) law is often used to explain a materials rheological properties (in our case, for ice). 
Such a flow law relates stress ( $\tau$ ) to strain ($\epsilon$) or strain rate ($\dot{\epsilon}$).

- stress ( $\tau$ ) = is the force per unit area applied to a body
- strain ($\epsilon$) = the normalize extension of the body
- strain rate ($\dot{\epsilon}$) = is the normalized stretching rate


The relationship between stress and strain can be represented through:

(1) uniaxial compression: a force $F$ is applied vertically to a block of area $A$ and length $L$ and the block is squished under the applied load. 
This type of stress is called normal stress. 
In this case it has a value $\tau = \frac{F}{A}$. The strain rate is defined as $\dot{\epsilon} = \frac{1}{L}\frac{dL}{dt}$. 

(2) simple shear: a force is applied horizontally on a block and across its upper surface and the its lower surface is held stationary. 
The block deforms and the upper surface moves relative to the bottom surface at a rate v(t) and it bottom surface stays stationary. 
This stress is a shear stress and is value is $\tau = \frac{F}{A}$ and $\dot{\epsilon} = \frac{v(t)}{L}$

Note:
strain = the deformation of a material from an applied stress 

$$
\epsilon = \frac{1}{H_0}\frac{dH}{dt}
$$

where $H_0$ is the non-deformed "real" material length under no applied stress, and $\frac{dH}{dt}$ is the change in material height in time

Many materials exhibit elasticity (i.e. a proportional relationship between stress and strain) up to a certain stress. 
The relationship between stress and strain is known as Hook's Law. 
The slope of stress vs. strain is the modulus of elasticity of the material (Young's modulus), E,

$$
E = \frac{\tau}{\epsilon}
$$

ex. E is approximately 10 GPa for ice. 
See page 10-3 here for a graph of this relationship: https://www.usna.edu/NAOE/_files/documents/Courses/EN380/Course_Notes/Ch10_Deformation.pdf

## Types of Deformation (as defined by stress vs. strain slopes)

-  "strain hardening" = the region in plastic deformation, which goes from the "yield strength" to the "ultimate strength"
- "elastic flow (deformation)" = the region from initial stress vs strain to the material's "yield strength"
- "plastic flow (deformation)" = the region from the material's "yield strength" to its "point of fracture"


Note:
Stress and strain relations are the same for the given material, regardless of if the material is undergoing tension or compression, as long as the applies stress is BELOW the proportional limit

### Maxwell  model for viscoelastic to plastic flow

We will consider a purely viscous Newtonian material $D$ and a purely elastic spring $S$ they are connected in series. See picture below. ![viscoelastic diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Maxwell_diagram.svg/2880px-Maxwell_diagram.svg.png?20160327183600)

Under an applied stress, the  total stress ($\tau_{tot}$) and total strain ($\epsilon_{tot}$) of the system can be defined, using Hooke's law for uni-axial OR shear stress (see above point), as follows

$$
\tau_{tot} = \tau_D = \tau_s
\epsilon_{tot} = \epsilon_D + \epsilon_S
$$

taking the derivative of total strain with respect to time, we obtain:

$$
\dot{\epsilon} = \frac{d \epsilon_{tot}}{dt} = \dot{\epsilon_D} + \dot{\epsilon_S} = \frac{\tau}{\eta} + \frac{1}{E} \frac{d \tau}{dt}
$$

where $\eta$ is the material property, viscosity.

Note: a Newtonian fluid is one in which stress is linearly related to strain rate under deformation, in short.
If a Maxwell material is subjected to a constrain strain rate then the stress increases until it reaches some constant value defined by:

$$
\tau = \eta \dot{\epsilon}
$$

More generally, this can be written as

$$
\tau (t) = \eta \dot{\epsilon} (1 - \exp(\frac{-Et}{\eta}))
$$

Where the time it takes the viscoelastic material to become plastic is known, in glaciology, as "Maxwell's time" when creep deformation occurs when a stress is applied for a sufficiently long time.

## Glen's flow law (and the viscoelastic properties of ice)

In ice (and other viscoelastic materials, like olivine, the human spine, or wood), different mechanisms dominate the characteristics of deformation at different applied stresses, temperatures, grain (in ice, for example) sizes, etc.
This can be seen, again, graphically !(see here, Fig, 5, https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2000JB900336 from the famous Goldsby & Kohldstedt; 2001, paper describing different values of $n$, talked about in turn). 

More specifically, this relationship, defined as Glen's flow law

$$
\dot{\epsilon} = A \tau^{n}
\dot{\epsilon_{ij}} = SA \tau^{n-1} \tau_{ij}
$$

Where $n$ is some positive value, $S$ is an enhancement factor (described on observations and varies with temperature, grain size, impurities, etc.) and $A$ is defined by the Arrhenius law (reasonably described for ice):

$$
A = A_0 e^{\frac{-Q}{RT}}
$$

where $R$ is the gas constant, $Q$ is the activation energy, and $T$ is the temperature.

## Tensor Notation
(we will go over this in a later seminar, but it here for reference)

We will quickly go over tensor notation for the sake of specificity of modeling stress and strain (which can be represented as tensors). See here for a more detailed description: https://mathworld.wolfram.com/Tensor.html
An $n$ rank tensor is an object with $n$ indices and $m^{n}$ components in $m$ dimensional space. The tensor obeys certain transformation rules but the dimension is largely irrelevant. 

- 0-rank tensor: is a scalar
- 1st-rank tensor: is a vector
- 2nd-rank tensor: is a matrix


We will look at 2nd-rank tensors (for example).
Let a 2nd rank tensor in 3-dimensional space of Real valued numbers be represented by A. 
Then A has 3 Principle Invariants:

- $I_1 = tr(A) = a_{11} + a_{22} + a_{33}$
-  $I_2 = \frac{1}{2}[tr(A)^{2} - tr(A^{2})]$
-  $I_3 = det(A)$

and 3 main invariants:

- $J_1 = I_1$
- $J_2 = I_1^{2} -2I_2$
- $J_3 = I_1^{3} - 3I_1 I_2 + 3I_3$


As an aside: we can exploit properties these invariants to get interesting results. As an example, see the Cayley-Hamilton theorem:

$$
A^{3} - I_1 A^{2} + I_2 A - I_3 I = 0
$$

where I is the identity tensor

### Ice Stress and Strain (in tensor notation)

We can represent stress and strain as tensors in terms of the strain rate tensor and the deviatoric stress tensor. 
Let $i$,$j$ be an element of positive integers. Using Glen's Flow Law for a Newtonian fluid (ice is a Newtonian fluid) we have:

$$
\tau_{ij} = 2 \eta \dot{\epsilon_{ij}}
\dot{\epsilon_{ij}} = \frac{1}{2} (\frac{\partial v_i}{\partial x_j} + \frac{\partial v_j}{\partial x_i})
$$

Let $c_{ijkl}$ be an effective viscosity tensor that may depend on invariants of $\tau_{ij}$, temperature, grain size, fabric (c-axis orientation), and/or impurities. Then, we can write

$$
\tau_{ij} = c_{ijkl} \dot{\epsilon_{kl}}
$$

Note: ice is assumed *isotropic* such that stress and strain rate are aligned. In other words,

$$
\dot{\epsilon_{ij}} = \lambda \tau_{ij}
$$

Glen's flow law is a power law and is most commonly used to describe the flow of ice in glaciers (*very generally*) and ice sheets. Without loss of generality, this can be written as

$$
\dot{\epsilon} = A \tau^{n}
$$

with n being an element of positive integers and A is approximately equal to $2.4x10^{-24} Pa^{-3}s^{-1}$ at 0 degrees C. Usually, n is set to 3, but this is not always the case (more in the next section).
In tensor form,

$$
\dot{\epsilon_{ij}} = A \tau^{n-1} \tau_{ij} 
$$

$$
\tau_{ij} = 2 \eta \dot{\epsilon}
$$

The *exact* values of A may also depend on temperature, grain size, stress regimes, impurities, etc. With $\eta$ being used to represent the effective viscosity s.t.

$$
\eta = \frac{1}{2 A \tau^{n-1}}
$$

where $\tau$ is the effective stress, defined as the second invariant of the stress tensor, $I_2$.

Note: a single crystal deforms easily if shear stress is applied along its basal plane. 
Deformation is, therefore, achieved through dislocations in the crystal lattice along basal planes (termed basal glide) and across basal planes (termed basal climb).

In ice, the basal plane is a result of hexagonal stacking of ice grains. See here for an illustration: https://johncarlosbaez.wordpress.com/2012/04/15/ice/

Generally, a single crystal of ice is made up of stacked rings (formed by tetrahedral H20 stacks) s.t. their plane *is the basal plane* and the normal to the basal plane is the c-axis. 
The orientation of c-axis for a set of grains (i.e. where the normal to the plane is oriented with respect to the c-axis) is usually referred to as the "fabric".
The c-axis orientation plays an important role in sliding behavior, ability to withstand compressive stress, and general properties of flow. When a compressive stress is applied to individual crystals, their c-axes rotate *toward* the compressive axis.


### Values of the n-exponent to describe ice flow

Most of ice deformation (ice is a polycrystalline material!!!) occurs via basal glide, but this is usually not a rate limiting process due to different c-axis orientations (using language from Hewitt, 2016; "Rheology").
Rate limiting processes are responsible for controlling macroscopic strain rate (described using Glen's flow law) and all depend on the magnitude of stress, temperature, and grain size of the material. 
Recall,

$$
\dot{\epsilon} = A \tau^{n}
$$

In tensor form,

$$
\dot{\epsilon_{ij}} = A \tau^{n-1} \tau_{ij}
\tau_{ij} = 2 \eta \dot{\epsilon_{ij}}
\eta = \frac{1}{2 A \tau^{n-1}}
$$

where n is an element of positive integers (usually between 2-4, this is important!). 

Under constant stress, we can see the evolution of strain and strain rate in log-log space (from experiments by Budd & Jacka, 1989). See here: https://www.sciencedirect.com/science/article/pii/0165232X89900141

- in the primary creep to secondary creep regime: we have material stiffening due to redistribution of stress between grains
- in the secondary creep to tertiary creep regime: we have material softening due to recrystallization and rotation of crystals
- in the tertiary creep regime onward: we have reached steady state orientation of grains


With different values of n-exponents we can define different stress regimes (generally):

- n = 3-4 : is the dislocation creep regime (disl), when climb (i.e. deformation through, and dislocation across the basal plane) enables *non-basal-plane* motion, this is mostly favored at high stress, and is independent of grain size
- n = 1.8 - 2.4: is the grain boundary sliding regime (GBS), mostly favored at low stresses, and very sensitive to (possibly dependent on) grain size
- n = 1: is the diffusion creep regime (diff), mostly favored at low stress, when molecules diffuse through crystals or along grain boundaries, and very sensitive to (possibly dependent on) grain size


"Normal" grain growth occurs in the absence of deformation, when grain boundaries are energetically unfavorable, and deviatoric stress causes individual c-axes to rotate towards the compression axis.
"Dynamic recrystallization" occurs during deformation and includes the subdivision of grains resulting from alignment of dislocations (called *polygonisation*), and when there is no initial strain energy and c-axis are at approximately 45 degrees to the compression axis. 
Under constant stress, a steady state between grain growth, c-axis rotation, and recrystallization is possible. BUT in general, grain size, fabric (c-axis orientation), and strain rate co-evolve. 
A favored c-axis orientation results in an *anisotropic* response of strain rate and deviatoric stress. 
When combining the effects of dislocation creep (disl), grain boundary sliding (GBS), diffusion creep (diff), and basal glide (basal) this suggests the following law:

$$
\dot{\epsilon} = \dot{\epsilon_{diff}} + \dot{\epsilon_{disl}} + \frac{\dot{\epsilon_{gbs}} \dot{\epsilon_{basal}}}{\dot{\epsilon_{gbs}} + \dot{\epsilon_{basal}}}
$$

More simply,

$$
\dot{\epsilon_{ij}} = A_{ij} \tau^{n_{ij}}
$$