# Agenda, week 5

With the WAIS meeting on last week we missed another week, so this ics actually our third meeting as a group. 

We will pick up where we left off, with some modifications to the original plan:


## relationship between strain rate and velocity fields

$$
\epsilon = \frac{\partial w}{\partial x}
$$

This is a chance to introduce tensors and tensor notation.

## driving stress
    - $\tau_d = -\rho g H \frac{\partial H}{\partial x}$ 
    - integrate total force acting on each side of a column
    - then take the difference between the two   

Also present this in two dimensions using $\nabla$

I would like to compute this over Antarctica. I made a start on pangeo in gradient.ipynb, but I cant run that locally for some reason. 


## perfectly plastic model 
    - $\tau_d = Y = 100$ kPa

## extras
- sometime in this week's session let's talk about some vector calculus, e.g.
   - $\nabla = \frac{\partial}{\partial x} \vec{i} + \frac{\partial}{\partial y} \vec{j} $
   - and what happens when this operates on a scalar field, or is 'dot producted' with a vector field.
- ... and tensor notation 