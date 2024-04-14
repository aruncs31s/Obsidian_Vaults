<!--toc:start-->
  - [Electric Fields](#electric-fields)
  - [Electric Flux](#electric-flux)
- [Gauss Divergence Theorem](#gauss-divergence-theorem)
<!--toc:end-->

- If $\overrightarrow A . \overrightarrow B = 0$ then $\overrightarrow A$ and $\overrightarrow B$ are said to be `Orthogonal` or `perpendicular`

- [[DEL Operator]]

#### Electric Fields

#### Electric Flux
The electric flux through an area is defined as the number of electric field lines passing through that area normally.

If the electric field at a certain point be $\overrightarrow E$

Then, the electric flux through an infinitesimal area with an area vector $\overrightarrow{dS}$ around that point will be given by:

$d \phi = \overrightarrow E . \overrightarrow dS$

**Electric Field Intensity**

The electric field intensity at a point in an electric field is the electric force experienced by a unit positive point charge located at that particular point.

**Electric Flux Density**

Electric flux density is the electric flux passing through a unit area normal to the direction of the flux.

**Relation between Electric Field Intensity and Electric Flux Density**

The electric flux density (D→) is equal to the electric field intensity (E→) multiplied by the permittivity (ε) of the medium concerned.

This, we write:

D→=εE→.

The electric field intensity at a distance r from a point charge

E→=14πε⋅qr2 r^.

The electric flux density at the same point will be given by:

D→=εE→D→=ε×14πε⋅qr2 r^D→=q4πr2 r^

### Gauss Divergence Theorem
- It can be used to see the location of `source` and `sink`
- It explains rate of change of function with respect to position
- It is a flux density, it explains how much flux is entering or leaving the source or sink
- If divergence is positive then that acting like a source and if negative it acting like a sink

> [!INFO] Source and Sink
> ***Source*** : A source is a ==component or device that provides power to a circuit==. This could be a battery, a power supply, or any other device that generates electrical energy. In a circuit, the source is where the electrical energy begins its journey. It is the ==starting point for the flow of current==.
>
> ***Sink*** : A sink is a ==component or device that consumes power from a circuit==
 
#statement
$$
\oint P.dS = \oint \overrightarrow \nabla . \overrightarrow P \ dV 
$$

> [!NOTE] Relation
> *surface intetegral of that function is = volume intetegral of  [[Divergence of a Vector|Divergence]] of that function* 
> So it explains the relationship between surface intetegral and volume intetegral



#proof 
1. Divergence of $\overrightarrow P$ can be calculated by the following expression

$Div(P) = \overrightarrow \nabla . \overrightarrow P = \underset{\Delta V  \to \infty}{\lim} \frac{\oint \overrightarrow P\, dS}{\Delta V}$

2. This calculation can be done by

$\underset{\Delta V \to \infty}{\lim}  \overrightarrow \nabla . \overrightarrow P \ \Delta V$ = $\underset{\Delta V  \to \infty}{\lim} \oint \overrightarrow P \ dS$

3. And says that ==Volume Integration of Divergence of P = Surface intetegral of Function P==

$$
\oint P.dS = \oint \overrightarrow \nabla . \overrightarrow P \ dV 
$$


> [!important] Summary
> 		This proof comes form the basic definition of divergence as in stage 1 and it basically says that ==taking volume integral of divergence of a function is same as taking the surface integral of that function==


#uses
1. It is used in application of fluid mechanics
2. It is used to understand electromechanics
3. It is used to understand the flaw of fields (eg : [[Quantum Mechanics/Gravitational Field|Gravitational Fields]],[Electric Field](#electric%20fields) 
4. Used in aerodynamics


### Stokes theorem
- Stokes theorem explains relationship in between ==line Integration== and ==surface integration==
- Stokes theorem is based on [[Curl.md|Curl]] of the function

#statement 
$$
\oint \overrightarrow P.dl = \int \overrightarrow \nabla \times \overrightarrow P \ dS
$$

#proof
1. Curl of a function $\overrightarrow P$ is

$Curl(\overrightarrow P) =  \overrightarrow \nabla \times \overrightarrow P = \underset{\Delta S \to 0}{\lim} \frac {\oint \overrightarrow P dl}{\Delta S}$ 

2. 

=> $\underset{\Delta S \to 0}{\lim} \overrightarrow \nabla \times \overrightarrow P \ \Delta S = \underset{\Delta S \to 0}{\lim} \oint \overrightarrow P dl$

*Which is basically [[Maths/Integration.md|integration]]*
> [!NOTE] Integration 
> $\underset{\Delta S \to 0}{\lim} a \ function = its \ integral$

3. 

$$
\oint \overrightarrow P.dl = \int \overrightarrow \nabla \times \overrightarrow P \ dS
$$

