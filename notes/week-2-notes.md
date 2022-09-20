# Notes from week 2

Wednesday Sep 14th

## Introductions

Sam: PhD student working with Jacky and Billy. Did JIRP. Here because of JIRP. Limited math experience. Doing an ODEs class in the math department.

Kris: Here because I want to go to grad school to study subglacial processes and am interested in theory.

Danny: Experience in radar/seismic imaging of geothermal reservoirs etc., but is now applying it to glaciology. No formal glaciology education, so I am taking this class. 

George: Background in engineering physics, took those courses, but they didn't really stick with me. I get a lot out of iterating over the key concepts.

Emily: physics background, interested in how the math applies to glaciers. For example, I want to see derivation of stokes equations. Similar experience with mathematical physics as George, in that I didnt get a lot out of it. 

Stacy: civil engineering - felt like I was just given equations. New to glaciology, want to learn more about ice sheets.  

Evelyn: physics undergrad, want to know more about an ice sheet than just a data file (which is how it comes into play in the GIA world). Interested most in *applications* of the math. 

Caitlin: Only education in glaciology has been going to the field with the Polar Geophysics Group. Math is more limited. Calc 3 (which has vector calculus) 

Indrani: If we dont use equations we forget how to use them (like any tool). Will be popping in and out of the class.


## What we want the class to be like

Definite interest in including some lecture material. 
  - a mix of lectures and discussion of equations. 

Interest in reading some classic papers. 

Important to highlight where something is not known by anyone, vs something that we just don't personally understand. 

## First-order questions

Some first-order questions about ice sheets that we spent some time on today are
- what causes the ice to flow?
- why are ice sheets higher in the middle than at the edges?
- why are they dome shaped? (i.e. why is the slope lower in the middle than the edges?)


### What causes the ice to flow?
Answers include: 
- ice has finite viscosity, 
- gravity, 
- they have to because flow moves ice from places where it accumulates to places where is ablates, and
- the surface is sloped.

These are all parts of the answer. All 4 of these are true and are required to explain ice flow.

### Why are ice sheets higher in the middle than at the edges?

Here we started to play with some equations to answer these questions. 

We wrote down an equation based on a depth-integrated mass balance:

$$
\frac{\partial H}{\partial t} = a - \frac{\partial q}{\partial x},
$$
where $H$ is the ice thickness, $t$ is time, $a$ is the accumulation rate in units of distance per time, $q$ is the depth-integrated ice flux in units of volume (or area if our model ice sheet is 2D) of ice moving past a location per time, and $x$ is distance along flow. 

We should derive and analyze this equation in a later class, but for now we will take it as given.

In the case when $\dot{H} = 0$ this shows that in the accumulation zone (where $a>0$), $q' > 0$. In other words, $q$ has to increase in the direction of flow in the accumulation zone. Also, given the $q = 0$ at the ice divide (or the top of the glacier, whichever geometry we consider), $q > 0$ everywhere. 
(Note that $\dot{H} \equiv \frac{\partial H}{\partial t}$ and $q' \equiv \frac{\partial q}{\partial x}$.)

The flux is related to the depth-averaged speed $u$ and $H$ simply by

$$
q = u H L
$$

where $L$ is the width of the glacier, which we assume is unit length. 
This equation can be understood by thinking about the volume of the box that is swept out by a rectangle aligned perpendicular to the flow direction and covering the whole cross-sectional of the glacier/ice stream, as it moves with the ice at a speed $u$. After unit time (a year say) the length of the box is $u$ in the along flow direction and so the volume of the box is $u H L$. 

Now we need to know how $u$ is related to geometry. We haven't derived this yet, but for now let's just recognize that the speed is going to increase with the negative of the ice surface slope. In reality, it is a relatively complex function of the slope, the thickness, gravity, ice density and ice rheology, but for now let's just say 

$$
u \propto -H'.
$$ 

Therefore 

$$
q \propto -H' H
$$

Because $q$ is larger than zero everywhere, these equations explains why ice sheets are thicker in the middle than the edges: the equations shows that if $q>0$ then $H'<0$, i.e. the thickness decreases with $x$. This is really just a manifestation of the fact that ice flows in the direction of decreasing surface slope (represented here by the minus sign in the equation above), but it is good to see it represented in this simple model.  


### Why are ice sheets dome shaped?

These equations also explain why ice sheets are dome shaped (at least in the accumulation zone): if $q' > 0$, then as $H$ decreases towards the edges, the equations above shows that $H'$ has to increase to compensate for that. 

In other words, as the ice gets thinner towards the edges, it moves less ice for a given slope, but we know that the ice flux increases in the direction of flow, so the slope has to increase in the flow direction, to increase the flux despite the decrease in $H$. 


### Why does the ice sheet *have to* do this or that?

The explanations above include statements about how the ice sheet surface *has to* do this or that. E.g., '...so the slope has to increase to increase the flux...". Its useful to note what this really means, in this context and pretty much whenever we say a system *has to* do this or that to obey some equation in geoscience.

In each case above where we use this language we mean that if this wasnt the case then the state of the system would evolve until it was the case. Note that we were considering steady states and therefore we were, in effect, saying 'in a steady state, the slope *has to* be this or that'. What we mean is that if the wasn't the case we wouldnt be in a steady state and the time derivative in the top equation would be non-zero and move the system towards a steady state where it is true. 

For example, consider a scenario when the ice-surface is such that the flux does not increase towards the edge ($q'=0$, for example) in the accumulation zone ($a>0$). The top equation shows that $\dot{H} > 0 and so the ice surface would increase in this region, increasing the surface slope and increasing $q$ until $q'=a$ and a steady state is reached. 

**The ice sheet 'relaxes' towards a state in which the gradient in flux balances the accumulation.** 

Side note: in general, in a 3D ice sheet $q$ is a vector quantity in this scenario and has components $q_x$ and $q_y$ and it is not just the gradient of $q$ in one direction that we are interested in, but the sum of the gradients in both horizontal directions. This is usually represented using the del operator $\nabla = \frac{\partial}{\partial x} \vec{i} + \frac{\partial}{\partial y} \vec{j} $. To get the sum of the gradients of $q$ in each direction we use $\nabla \cdot q =  \frac{\partial q_x}{\partial x}  + \frac{\partial q_y}{\partial y} .$

So the bold statement above can be generalized to **In a steady state the horizontal flux divergence balances the accumulation rate.**


## PLaying with the toy model numerically
I wrote some code in a jupyter notebook which solves our toy ice model numerically to understand how the curvature happens. If you start with an liner $H$, $\dot{H} is initially uniform. It is the boundary conditions that break that uniformity and allow a curved surface to form. This notebook can be found [here](https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/main/code/toy_model_w2.ipynb).


## Next week
We should probably go through the fundamental findings from today again.

We should make sure we come back to these equations and derive them properly at some point in the course. Not clear what order to do them in yet. 

We didnt get a chance to talk about the jupyterbook idea https://ldeo-glaciology.github.io/glaciology-intro-book/book-intro.html  . We can do this next week. 