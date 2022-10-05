# Agenda, week 5

With the WAIS meeting on last week we missed another week, so this is actually our third meeting as a group. 

We will pick up where we left off, with some modifications to the original plan:

## 1. note that what we mean when we talk about 'instantaneous' deformation in the context of elastic deformation
- its not really instantaneous and all the talk of seismic/sound waves propagating through materials being evidence of them deforming elastically was confusing, because it makes it sound like sounds wave should have infinite speed. 
- what our discussion neglected was the acceleration terms in the equations. 

## 2. relationship between strain rate and velocity fields

$$
\epsilon = \frac{\partial w}{\partial x}
$$

This is a chance to introduce tensors and tensor notation.

## 3. driving stress

- $\tau_d = -\rho g H \frac{\partial H}{\partial x}$ 
- integrate total force acting on each side of a column
- then take the difference between the two   

Also present this in two dimensions using $\nabla$

I would like to compute this over Antarctica. I made a start on pangeo in gradient.ipynb, but I cant run that locally for some reason. 


## 4. perfectly plastic model 
- $\tau_d = Y = 100$ kPa

## 5. SIA from $tau_d$

Take the expression for the driving stress and put it in glen's flow law to get the vertical gradient of horizontal velocity $\frac{\partial u}{\partial z}. Then integrate vertically to get $u$. Then integrate again to get $q$. 

The result should be 

$$
q = \frac{A}{n+2} \left(-\rho g \frac{\partial H}{\partial x}\right)^n H^{n+2}
$$


## extras
- sometime in this week's session let's talk about some vector calculus, e.g.
   - $\nabla = \frac{\partial}{\partial x} \vec{i} + \frac{\partial}{\partial y} \vec{j} $
   - and what happens when this operates on a scalar field, or is 'dot producted' with a vector field.
 