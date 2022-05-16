CLAMP_25: Mesh independence test 1: 2x x 2y

Mesh: 2 x super coarse mesh (10920 cells)
OpenFOAM version: 9
Solver: clampPimpleFoam v6 and pimpleFoam

A time series from earlier in the season, with higher temperatures. 2011-11-18 06:15:00 to 2011-11-23 23:00:00
0/Tf and 0/Ts are not the same, but 0/Ts is consistent at points _1, _2, and _7.
A new probe at 5 cm from the top of the clamp has been added (4.5 2.95 0.05)

This case is built on clamp_22.
- D&F reduced by a factor of 10 compared to experimental data (Talib et al 2003)
- The following modifications were made to the solver:
-- TsEqn:
--- dTs/dt is now multiplied by invPor
--- the terms of the inter-phase transfer are no longer divided by por/ invPor
--- Qr is now multiplied by 2 instead of 4
--- Conduction within the cover zone is defined as per in the clamp zone, times 100
--- Conduction within the inner domain zone is defined as per in the clamp zone, times 100
--- Inter-phase transfer Ts within the outer domain zone is defined as explicit, using a factor of 0.01 to ensure no crazy divergence.
-- TfEqn:
--- dTf/dt is now multiplied by por

The following modification were made to the clamp_22 case:
-- data for Tf at inlet has been updated to be that recorded at the site. U remains that recorded for Borgeby.
-- cover_zone, inner_zone, outer_zone all added to topoSetDict
-- covDummy, inDummy, outDummy all added to setFieldsDict
-- covDummy, inDummy, outDummy all added to the 0_orig directory
