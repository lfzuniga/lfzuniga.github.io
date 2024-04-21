---
layout: note
title: "Transport Phenomena - Continuity and Species Conservation"
date: 2024-02-20
---

Note: The content is this note is based on [Professor Amir Haji-Akbari](ttps://haji-akbari.yale.edu)'s lecture notes for Transport Phenomena II (CENG 315).

## Introduction
Transport phenomena is about determining extent and direction where qunatities. such as mass, energy, and momentum are transferred in a system. We need the following properties to do that:
1. *Conservation Laws*. Essentially laws from first principles. Laws of physics
2. *Constitutive Laws*. Laws determined empirically. They tell us how fluxes scale with driving forces.
3. *Equation of State*. This allows us to use local thermodynamic equilibrium in really small volumes, even if stuff is out of equilibrium.

This mathematical machinery can also be used for entropy, electric charge, and magnetization.

## Conservation Laws for Scalar Quantities

#### Integral Forms

We say our total quantity of stuff is $\mathscr{B}_{\mathscr{V}}(t)$ . Counting it over all the volume of the system (to get the actual value of stuff we have):

$$\mathscr{B}_{\mathscr{V}}(t)=\int_{\mathscr{V}} \underbrace{b(\mathbf{r}, t)}_{scalar \ intensity} d V$$

Where $b(\mathbf{r}, t)$ is *volumetric density* (like $\rho=\frac{mass}{m^3}$ (density), $\text{M}=\frac{mol}{m^3}$ (molarity), etc   .). So something over volume.

The stuff we have $\mathscr{B}_{\mathscr{V}}(t)$ will change on time based on 3 different terms:

$$
\begin{equation}
\frac{d}{dt}\mathscr{B}_{\mathscr{V}}(t)=\underbrace{\frac{d}{d t} \int_{V(t)} b d V}_{d \mathscr{B_V} / d t}=\underbrace{\int_{V(t)} B_V d V}_{\text {generation }}-\underbrace{\int_{S(t)} \mathbf{F} \cdot \mathbf{n} d S}_{\text {convection and/or diffusion }}+\underbrace{\int_{S(t)} b \mathbf{n} \cdot \mathbf{v}_S d S}_{\text {moving boundary }}\end{equation}$$

- Stuff being generated inside the volume
- Stuff crossing the surface of the volume
- Stuff that leaves the volume as $\mathscr{V}(t)$ changes with time.

Using Reynolds Transport Theorem: [^1]

$$\begin{equation} \int_{V(t)} \frac{\partial b}{\partial t} d V=\int_{V(t)} B_V d V-\int_{S(t)} \mathbf{F} \cdot \mathbf{n} d S \end{equation}$$

#### Multiphase Flow
When $\mathscr{V}(t)$ is not continues we get

$$\begin{aligned} \frac{d}{d t} \int_{V(t)} b d V= & \underbrace{\int_{V_A(t) \cup V_B(t)} B_V d V}_{\text {volumetric generation }}+\underbrace{\int_{S_I(t)} B_S d S}_{\text {internal surface generation }}+ \\ & \underbrace{\int_{S_A(t) \cup S_B(t)}\left[b \mathbf{v}_S-\mathbf{F}\right] \cdot \mathbf{n} d S}_{\text {external surface flow }}\end{aligned}$$

Here the only extra term is $\underbrace{\int_{S_I(t)} B_S d S}_{\text {internal surface generation }}$ , which refers to the amount of $\mathscr{B}$ created per unit surface. The tricky part here is that we have two generation terms. One is simply for the generation in the *volume* and the other one is for a generation in the *surface* as the surface might be the actual thing making the reaction happen. It is an extra nuance because I assume in most cases we have either one term or the other one.

#### Differential Forms
Shrinking the volume to have a tiny tiny volume: $V(t) \rightarrow 0$ and using the Gauss Theorem [^2]

$$\int_{V(t)} \frac{\partial b}{\partial t} d V=\int_{V(t)} B_V d V-\int_{S(t)} \mathbf{F} \cdot \mathbf{n} d S \rightarrow \int_{V(t)}\left[\frac{\partial b}{\partial t}+\nabla \cdot \mathbf{F}-B_V\right] d V=0$$

And we can chop off the volume integral as if the whole expression goes to zero for a big volume, it should go to 0 to for a really small $V(t)$.

$$\frac{\partial b}{\partial t}+\nabla \cdot \mathbf{F}-B_V=0$$

And for multiphase we will have 

$$\left[\left(\mathbf{F}-b \mathbf{v}_I\right)_B-\left(\mathbf{F}-b \mathbf{v}_I\right)_A\right] \cdot \mathbf{n}_I=B_S$$

#### Convective and Diffusive Transport
Our total flux $\mathbf{F}$ is a result of stuff being carried in or out with an *average* velocity $\mathbf{v}$ as well as stuff *moving* in or out the control volume due to a *species related phenomena*. Meaning, flux will vary from species to species and thus using $\mathbf{v}$ does not catch all of the stuff coming in of $\mathscr{B}$. And that flux $\mathbf{f}$ we use to "catch up" we call if diffusion.

$$\underbrace{\mathbf{F}}_{\text{Total \ Flux}}=\underbrace{b \mathbf{v}}_{\text{convective \ flux}} +\underbrace{\mathbf{f}}_{\text{diffusive flux}}$$

Velocity is kind of important here since we can define it based on *mass*, *molar*, and *volumetric* units. And the **key** here is that these are NOT just conversations. They are not just scaling factors:

>**Note** - On the subtle difference between $mass$ and $mol$
>
>The reason why $mol$ is not just a "scaling factor" is because the amount of moles we use per each species is **different** on a species basis. Meaning, going from $g \rightarrow  kg$ is NOT the same as going from $g \rightarrow mol$ since the scalar associated with the $g \rightarrow mol$ changes **on a species basis.** Which is to say, each species will have a different molar mass $M_i  \ [\frac{g}{mol}]$ . 
>
And the fact that the conversion from $g \rightarrow mol$ varies from species, it means that $moles \neq mass \ [g]$. So some of the main tricks we used with mass, we can't use with moles. 

So the key here is that the definition of $\mathbf{J}$ **will depend** on what $\mathbf{v}(\mathbf{r},t)$ we use.

## Major Conservation Laws in Transport Phenomena

#### Continuity ($b=\rho$)
For $b=\rho \ \left[\frac{mass}{L^3}\right]$ we will not have diffusion as we are dealing with **total mass**. Mass is king in the sense that mass is neither created nor conserved (at least in out systems) and mass is like the be all end all. Mass is directly matter, directly stuff. So our formula reduces nicely to:

$$\frac{\partial \rho}{\partial t}+\nabla \cdot(\rho \mathbf{v})=0$$
And I say nicely because mass is directly stuff means $B_V=0$ (mass is not created or consumed) and $\mathbf{f}=\mathbf{0}$ (mass does not diffuses or anything. Mass just flows with velocity) [^3]

And for incompressible fluids, where $\nabla \rho=\mathbf{0}$ and $\frac{\partial \rho}{\partial t}=0$ (density is constant throughout time AND space)

$$\nabla \cdot \mathbf{v}=0$$

###### Material Derivative
The continuity equation is related to the material derivative in that it allows us to write the general formula of $\frac{\partial b}{\partial t}$ we got earlier as

$$\frac{\partial b}{\partial t}+\nabla \cdot(b \mathbf{v})=\rho \frac{D \hat{B}}{D t}$$

where $\hat{B}:=\frac{b}{\rho} =\frac{something}{\cancel{m^3}} \cdot \frac{\cancel{m^3}}{mass}\Rightarrow \hat{B}=\frac{something}{mass}$

The material derivative is

$$\frac{D}{D t}:=\frac{\partial}{\partial t}+\mathbf{v} \cdot \nabla$$

###### Interfacial Boundary Conditions for $b=\rho$
Since $\mathbf{f}=\mathbf{0}$ for $b=\rho$, for two phases we will have

$$\rho_B\left(\mathbf{v}_B-\mathbf{v}_I\right) \cdot \mathbf{n}_I=\rho_A\left(\mathbf{v}_A-\mathbf{v}_I\right) \cdot \mathbf{n}_I$$

For most cases, $\mathbf{n}_I \cdot \mathbf{v}_I=\mathbf{n}_I \cdot \mathbf{v}_A=\mathbf{n}_I \cdot \mathbf{v}_B=0$, which means that  the velocity of our surface $\mathbf{v}_I$ will be orthogonal to the orientation of the surface. In some cases though, the velocity is going *towards* the interface, so we get something like the question 4 of pset 3. 

#### Species Conservation in Mixtures ($b=c_i$)

$$\frac{\partial c_i}{\partial t}+\nabla \cdot \mathbf{N}_i=R_i$$

In this case we will have different fluxes. We will have in particular

$$\text{Molar flux} := \mathbf{N}_i =\left[\frac{mol}{m^2\cdot s}\right]$$

$$\text{mass flux}:= \mathbf{n}_i=M_i\mathbf{N}_i =\left[\frac{g}{m^2\cdot s}\right]$$

**Both will have convective and diffusive subparts**

Of course, for the *exact velocity* per species, we will have

$$\mathbf{v}_i:=\frac{\mathbf{N}_i}{c_i}=\frac{\mathbf{n}_i}{\rho_i}=\left[\frac{m}{s}\right]$$

where $\rho_i=\rho \omega_i$ and $\omega_i$ is the *mass fraction*

###### Specific Velocities

$$\text{Molar averaged velocity}\ (M):= \mathbf{v}^{(M)}:=\frac{\sum c_i \mathbf{v}_i}{\sum c_i}=\sum x_i \mathbf{v}_i=\frac{\sum \mathbf{N}_i}{\sum c_i}$$

$$\text{mass averaged velocity}\ (m):=\mathbf{v}^{(m)}:=\frac{\sum \rho_i \mathbf{v}_i}{\sum \rho_i}=\sum \omega_i \mathbf{v}_i=\frac{\sum \mathbf{n}_i}{\sum \rho_i}$$

We usually say $\mathbf{v}^{(m)}=\mathbf{v}$ because we deal with **mass** averaged velocity. And again, here is where the nuance with moles and mass gets finicky, as the proportions between moles and mass are just not the same.

And because we can have different velocities, in the same way we can have similar fluxes.

$$\text{Molar} \ \text{diffusive flux} \ (M):= \mathbf{J}_i:=\mathbf{N}_i-c_i \mathbf{v}^{(m)}=\left[\frac{mol}{m^2\cdot s}\right]$$

$$\text{mass} \ \text{diffusive flux} \ (m):=\mathbf{j}_i:=\mathbf{n}_i-\rho_i \mathbf{v}^{(m)}=\left[\frac{g}{m^2\cdot s}\right]$$

And we use $\mathbf{v}^{(m)}$ so that 
$$\sum_{i=1}^{n_s} \mathbf{j}_i=\mathbf{0}$$

Meaning, when we are working with the mass average velocity $\mathbf{v}^{(m)}$ and get the mass diffusive flux $\mathbf{j}$, the addition of all of the species will be 0. Which makes sense as the total flux is given by the total mass coming in.

#### Fick's Law
Fick's law is the following *constitutive equation*:

$$\mathbf{j}_A=-\mathbf{j}_B=-\rho \underbrace{D_{A B}}_{diffusivity} \nabla \omega_A$$

And remember that $\mathbf{j}_A+\mathbf{j}_B=\mathbf{0}$

And for the Molar flux

$$\mathbf{J}_A=-D_{A B} \nabla c_A$$

---
A few handy identities

$$\omega_A=\frac{\rho_A}{\rho_A+\rho_B}=\frac{c_A M_A}{c_A M_A+c_B M_B}=\frac{x_A M_A}{x_A M_A+x_B M_B}$$

$$\nabla \omega_A=\frac{c^2 M_A M_B}{\rho^2} \nabla x_A$$

$$\mathbf{J}_A=-\frac{\rho D_{A B}}{M_A} \nabla \omega_A$$

---

For dilute solutions we assume that different solutes behave independently and so we have 

$$\mathbf{J}_i=-D_i \nabla c_i$$

So returning to our species concentration we have

$$\begin{align} \frac{\partial c_i}{\partial t} &= -\nabla \cdot \mathbf{N}_i+R_i \\ \frac{\partial c_i}{\partial t} &= -\underbrace{\nabla \cdot\left(c_i \mathbf{v}\right)+\nabla \cdot\left[D_i \nabla c_i\right]}_{\nabla \cdot \mathbf{N}_i}+R_i \end{align}
$$

which yields

$$\frac{\partial c_i}{\partial t}=-\nabla \cdot\left(c_i \mathbf{v}\right)+D_i \nabla^2 c_i+R_i$$

And for incompressible flow: $\frac{D c_i}{D t}=D_i \nabla^2 c_i+R_i$ since $\nabla \cdot\left(c_i \mathbf{v}\right)=\mathbf{v} \cdot \nabla c_i+c_i \nabla \cdot \mathbf{v}=\mathbf{v} \cdot \nabla c_i$

##### Interfacial Boundary Conditions for $b=c_i$
###### Local Equilibirum
At thermodynamic equilibrium the chemical potentials need to be the same:

$$\left.\mu_{i, A}\left(P_A, T_A, c_{1, A}, \cdots, c_{n_s, A}\right)\right|_{\text {interface }}=\left.\mu_{i, B}\left(P_B, T_B, c_{1, B}, \cdots, c_{n_s, B}\right)\right|_{\text {interface }}$$

We can have two scenarios
1. our species $i$ is soluble in two phases and we have to solve for both chemical potentials (but can make some approximations). And we can assume that solutions are ideal and so: 

$$c_{i, B}=K_i c_{i, A}$$

2. One phase **only** has one component. and that phase will have the equilibrium solubility of $c_i^*$

###### Two-Phase Flux Balance

$$\left\{\left[\mathbf{J}_i+c_i\left(\mathbf{v}-\mathbf{v}_I\right)\right]_B-\left[\mathbf{J}_i+c_i\left(\mathbf{v}-\mathbf{v}_I\right)\right]_A\right\} \cdot \mathbf{n}_I=R_{S, i}$$

Where $R_{S, i}$ is the molar per area rate at which we make $i$ at the interface.

We again have two scenarios here
1. Heterogeneous Reaction at interface between $A$ and $B$. There is no flow through the interface so we can simplify our equation to: 
$$\mathbf{J}_{i, B} \cdot \mathbf{n}_I-\mathbf{J}_{i, A} \cdot \mathbf{n}_I=R_{S, i}$$

   If phase $B$ is also impermeable to $i$, then 

   $$\mathbf{J}_{i, B}=\mathbf{0}$$ 

   $$\mathbf{J}_{i, A} \cdot \mathbf{n}_I=R_{S . i}$$

2. Convective Boundary.

## Other useful Conversions and Relations

$$\frac{\rho}{c}=\left[\frac{g}{\cancel{m^3}}\right]\cdot \left[\frac{\cancel{m^3}}{mol}\right]=\left[\frac{g}{mol}\right]=\underset{\text{Molar Mass}}{M}=x_A M_A + x_B M_B$$

partial mass ($m$) fraction:
$$\omega_A=\frac{\rho_A}{\rho_A+\rho_B}=\frac{\rho_A}{\rho}$$

partial molar ($M$) fraction:
$$x_A=\frac{c_A}{c_A+c_B}=\frac{c_A}{c}$$

---

[^1]: Reynolds Transport Theorem: $$\frac{d}{d t} \int_{V(t)} b d V=\int_{V(t)} \frac{\partial b}{\partial t} d V+\int_{S(t)} b \mathbf{n} \cdot \mathbf{v}_S d S$$ Which basically tells us that the rate of change of the *total stuff* in a volume ($\frac{d}{dt}\mathscr{B}_{\mathscr{V}}(t)$) is the same as the rate of change of the stuff per unit volume ($\frac{d}{dt}b$) counted in the volume plus the stuff that is leaving the surface ($b \mathbf{n} \cdot \mathbf{v}_S$) as a result of the surface moving ($\mathbf{v_S}$). 

[^2]: Gauss Theorem to convert a surface integral to volume integral $$\int_{S(t)} \mathbf{n} \cdot \mathbf{F} d S=\int \nabla \cdot \mathbf{F} d V$$

[^3]: This is based on the definition that $\mathbf{F}_\rho=\rho \mathbf{v}$. Meaning, we define flux as $\left[\frac{mass}{L^2 \cdot t}\right]=\left[\frac{mass}{area \cdot t}\right]$
