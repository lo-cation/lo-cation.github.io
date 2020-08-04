---
layout: post
title:  How to write a UMAT for hyperelastic
date:   2019-11-10 22:00:00 +0800
tags: FEM
---
ABAQUS provided powerful API like UMAT/UHYPER for users to define constitutive equations by theirselves.
UHYPER is designed for user-defined hyperelastic materials in particular.
It requires strain energy function of materials in the format of invariants and corresponding derivatives in the scripts and ABAQUS will calculate and update stress and material stiffness automatically.
Although UHYPER is a very convenient tool for user-defined material, it is restricked to hyperelastic material and only in format of invariants.
_Not sure so far if it is capable of dealing with anisotropic hyerslastic material because the strain energy fucntion of anisotropic material may not be expressed using invariants_.
Compared with UHYPER, UMAT is more difficult to implement, it a more general tool with much flexibility to define complex constitution like plasticity and viscoplasticity.
Using hypereslastic material as an example, below is an introduction to write a UMAT scripts.

## Formulations
1. Defining strain energy function ___W___
2. Calculating ___Cauchy stress tensor___ (sigma). Usually, ___second Piola-Kirchhoff stress tensor___ ( ___S___ ) is obtained fisrt by calculating derivatives of ___W___ with respect to ___Green strain tensor___ ( ___E___ ) or ___righ Cauchy-Green deformation tensor___ ( ___C___ ). Then push ___S___ to sigma.
3. Calculating material tangent. Second derivatives of ___W___ with repect to ___C___ gives ___Lagrangian elasticity tensor___ then ___Eulerian elasticity tensor___ can be obtained through push forward procedure. Zienkiewicz gives detailed derivation in his book ___The Finite Element Method for Solid and Structural Mechanics___, please see ___Chapter 6 Material Constitution for Finite Deformation___ for details.
4. Transfer ___Eulerian elasticity tensor___ which is based on Truesdell rate to tangent moduli for Jaumann rate by requirement of ABAQUS.
See detailed relationship in ___Section 5.4.4 Hypoelastic___ of Belytschko's book ___Nonlinear Finite Elements for Continua and Structures___.
However, the equation has asymmetric part in Jaumann moduli.
If removing the asymmetric part, the equation will lead to the same Jaumann moduli expression of new-hookean material as displayed in manual ___Writing User Subroutines with ABAQUS___.

Although users could write either UMAT or UHYPER for the same strain energy function, the simulation results using these two methods are not exactly the same.
UHYPER deals the energy function by full variable form while UMAT treats hyperelastic material as hypoelastic material in incremental form.
Loading steps will lead errors into results obtained from UMAT.

_There are still several questions need to be cleared._
- A deep understanding of strain rate.
- What is the correct relationship between Jaumann moduli and Truesdell moduli? Should the asymmetric part be there?
- What is the difference between hypoelastic and hyperelastic?
- Why and how does UMAT treat hyperelastic as hypoelastic?
- What is the difference between full variable form and incremental form? How do these differences affect?


## Coding
UMAT/UHYPER is coded in Fortran language.
It will be easier to find an example script from ABAQUS documentation and take it as a template to make sure the interface is correct.
While coding, there are several notes for Fortran:
1. Pay attention to the length of each line. Fortran only allow for limited length (72 columns).
2. If one line is to long, seperate it into several lines.
Remember to keep the first 5 characters as space the put "&" at the 6 position.
3. Claim variables used.
Fortran will take variables beginning with I-N as integer by default.

For better coding, please learn more basic knowledge of Fortran.


## Reference
1. ___Bonet - Nonlinear Continuum Mechanics for Finite Element Analysis___
2. ___Zienkiewicz - The Finite Element Method for Solid and Structural Mechanics___
3. ___Belytschko - Nonlinear Finite Elements for Continua and Structures___
4. ___Manual - Writing User Subroutines with ABAQUS___
5. ___ABAQUC - Documentation___
