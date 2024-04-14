# [[Gradient of a Scalar]] $\nabla V$
*Gradient of any scalar is the ==maximum space rate of change of that function==*
- ==Gradient of a scalar is a vector==

#eg If V represents electric potential $\nabla V$ represents the potential gradient, then 

- *Cartesian Coordinates*
$$
\nabla V = \frac{\partial V \hat a_ x }{\partial x}+\frac{\partial V \hat a_ y }{\partial y}+\frac{\partial V \hat a_ z }{\partial z}
$$
- *Cylindrical Coordinates*
$$
\nabla V = \frac{\partial V \hat a_ \rho }{\partial \rho}+ {1\over \rho} \frac{\partial V \hat a_ \phi }{\partial \phi}+\frac{\partial V \hat a_ z }{\partial z}
$$
- *Spherical Co-ordinates*

$$
\nabla V = \frac{\partial V \hat a_ r }{\partial r}+ {1 \over r}\frac{\partial V \hat a_\theta }{\partial \theta}+ {1\over r\sin\theta }\frac{\partial V \hat a_ \phi }{\partial \phi}
$$

#question
Find the gradient of the following 
1. $u=x^2y+xyz$
2. $v = \rho = \sin\phi + z^2\cos\phi + \rho^2$

1. $\nabla u =\frac{\partial }{\partial x}(x^2y+xyz) \hat a_{x}$
   $+\frac{\partial }{\partial y}(x^2y+xyz) \hat a_{y}$
    $+\frac{\partial }{\partial z}(x^2y+xyz) \hat a_{z}$ 
$$
= (2xy+yz) \hat{a_x} + (x^2 +xy)\hat a_y +(xy)\hat a_z
$$
