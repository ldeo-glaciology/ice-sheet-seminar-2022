# Agenda, week 3

- summary and further discussion of what we were discussing at the end of last class:

How

$$
\frac{\partial H}{\partial t} = a - \frac{\partial q}{\partial x},
$$

and 

$$
q = -H' H
$$

lead to a concave surface profile. 

- go through notebook: https://github.com/ldeo-glaciology/ice-sheet-seminar-2022/blob/main/code/toy_model_w2.ipynb

- discussion of jupyter book idea for synthesizing what we learn and disseminating it
  - a few unfinished chapters of a jupyter book are here: https://ldeo-glaciology.github.io/glaciology-intro-book/book-intro.html  
  - this will require understanding git. Here's a tutorial. https://fperez.github.io/demo-jupyter-git/intro-git/Git-Tutorial.html 

- intro to mathematical modeling
    - $g = a$



- rheology
    - elastic vs viscous vs plastic
        - $\epsilon = \frac{\tau}{E}$
        - $\dot{\epsilon} = \frac{\tau}{E}$
        - $\tau = Y$

- driving stress
    - $\tau_d = -\rho g H \frac{\partial H}{\partial x}$ 
    - integrate total force acting on each side of a columne
    - then take the difference between the two  

- perfectly plastic model 
    - $\tau_d = Y = 100$ kPa


- sometime in this week's session let's talk about some vector calculus, e.g.
   - $\nabla = \frac{\partial}{\partial x} \vec{i} + \frac{\partial}{\partial y} \vec{j} $
   - and what happens when this operates on a scalar field, or is 'dot producted' with a vector field.
- ... and tensor notation 
   
