# VUMAT-3D-Compoaite-
VUMAT for Composite for solid elements based on hashin
What is the reference I used to develop my VUMAT?
[1] joy Pederson thesis 

What are the errors that I solved?
1)	lDmg = 0 is not define instead lfail =0 is defined may be intentionally, that is corrected.
What is my contribution:
2)	Once the four failure criteria is met, the stiffness of the elements is reduced to zero
(dmgFiberT(k) = one , etc) in line 436,444,457,467
Instead dmdxxxx(x) is degraded as per 0.5(failure evaluation (rft etc)-1) as suggested in one of the forums and in [2].
3)	The failure evaluation equations are all in plane stresses (contain only s11,s12,s13,s22) 

These failure evaluations are changed to equations presented in [3]

               rft = (s11*f1tInv )**2
               rfc = abs(s11) * f1cInv
            rmt = ( ( s22 + s33 )**2 * f2tInv**2 )
     *            + ( ( s23**2 - (s22 * s33 ) ) * ( f23Inv**2 ) )
     *           + ( s12 * f12Inv )**2 
     *           + ( s13 * f13Inv )**2

           rmc = ( ( f2c ) * ( s22 + s33 ) * haf * half * f23Inv**2 )
     *           - ( ( f2cInv ) * ( s22 + s33 ) )
     *           + ( ( s23**2 - (s22 * s33 ) ) * ( f23Inv**2 ) )
     *           + ( ( s23**2 - (s22 * s33 ) ) * ( f23Inv**2 ) )
     *           + ( s12 * f12Inv )**2 
     *           + ( s13 * f13Inv )**2


4)	Fail condition based on principal normal strain is removed
References:
[1]	Pederson J. Finite Element Analysis of Carbon Fiber Composite Ripping Using ABAQUS, 2008.
[2]	Khallouf A, Richter M, Duddeck PF. Software Lab Progress Report-1 Project Title : Development of The Failure Criteria for Composites Group Members : Supervisors : Ani Khaloian Date Submitted : Abstract : 2019:1–18.
[3]	Guo W, Xue P, Yang J. Nonlinear progressive damage model for composite laminates used for low-velocity impact. Appl Math Mech (English Ed 2013;34:1145–54. https://doi.org/10.1007/s10483-013-1733-7.

