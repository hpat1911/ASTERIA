# ASTERIA


SYNOPSIS


1. Abstract 
 
Interacting eclipsing binaries exhibit strongly coupled orbital, gravitational, thermodynamic, and mass-transfer processes, making their physical properties difficult to reconstruct directly from observations. While advanced packages such as PHOEBE provide powerful numerical modelling and optimization, their complexity can make it difficult to independently trace how observational measurements propagate into derived stellar parameters and diagnose faulty data beforehand. This study tested if a diagnostic first-principles computational pipeline designed to provide a transparent first-pass reconstruction of interacting binary systems and facilitate assessment of observational data and reduction quality could be developed.  ASTERIA integrates photometric Fourier decomposition and flux analysis with spectroscopic radial-velocity constraints, Keplerian dynamics, Roche-potential geometry, gravity-darkening, and ballistic mass-transfer modelling. Its principal computational innovations include a parameter-sweep approach that handles data without requiring exact orbital geometry, a 3D modelling approach based on Roche potentials without relying on Doppler Imaging and a continuous gravity-darkening formulation that evaluates the thermal structure across the distorted stellar surface rather than imposing a fixed global treatment, allowing regions approaching L1 to be modelled continuously. The pipeline was validated against six diverse eclipsing binaries: β Lyrae, β Persei, V356 
Sagittarii, RY Scuti, TT Hydrae, and U Cephei. Derived parameters showed a mean deviation of 2.88% and a median deviation of 2.87% from accepted literature values, with all six systems within 5%, demonstrating the breadth of this pipeline. These results demonstrate that ASTERIA can provide physically interpretable preliminary models, enabling professional and amateur astronomers to evaluate observations and data-reduction pipelines before applying more computationally intensive packages. 
 
 
2. Introduction 
 
Eclipsing binaries (especially ones like Beta Lyrae) are cosmic laboratories in which theoretical knowledge can be applied to quantify and explain complex phenomena such as evolution, mass transfer, accretion physics and temperature variations. 
 
Modern binary modelling relies on numerical optimization software packages such as PHOEBE and Wilson–Devinney (Wilson & Devinney 1971; Prša et al. 2016). These programmes are powerful, employing advanced numerical machinery to optimise physical parameters, but they require vast datasets to generate high-quality results. Errors in data collection and reduction frameworks can lead to flawed modelling, wasting costly data. This is especially inconvenient for amateur and professional astronomers on a tight monetary and time budget. 
 
Asteria solves this by generating precise estimates (validated via trials) based on minimum data points for semi-detached/Roche-filling systems.  

 This framework is in no way intended to replace packages like PHOEBE, but instead to complement them by helping students and astronomers. 
 
 
3. Innovation 
 
Software packages such as PHOEBE require extensive and well-distributed photometric spectroscopic radial velocity data points ideally. ASTERIA bypasses this requirement by employing geometric constraints and a parameter-sweep approach that avoids requiring fixed inclination and eccentricity values for preliminary reconstruction. 
 
ASTERIA reconstructs the three-dimensional stellar geometry directly from the Roche potential rather than requiring surface information to be inferred through spectroscopic imaging-based techniques, significantly reducing spectroscopic data requirements.  
 
Lastly, ASTERIA utilises a continuous sigmoid gravity darkening function w.r.t. surface temperature to reliably switch between fully convective or radiative gravity darkening coefficient values, rather than imposing a globally fixed value, in cases of immense point distortion (like L1 teardrop geometry).  
 
 
4. Methodology 
 
Asteria was developed by assessing the properties of Beta Lyrae as a model system and later generalised. 
 
All parameters determined are calculated as a sensitivity range by ASTERIA by sweeping the orbital inclination from 80 to 90 degrees and the orbital eccentricity from 0 to 0.2. 
 
The ratio of the semi-amplitudes gives the mass ratio, q.  The semi-major axis has been calculated using the relation between individual orbital radii and the orbital time period. The total mass is calculated using Kepler’s Third Law, relating the orbital period, semi-major axis, and total mass. This subsequently gives the individual masses of the stars. 
 
Roche potentials have been used to calculate the geometry of the donor. The points in the orbital plane where the gradient of the Roche potential is null are the Lagrangian points. 
 
For systems showing mass transfer, the ballistic trajectory of material leaving the inner Lagrangian point is modelled by simulating the motion of a unit-mass particle. As established by fluid dynamics, the maximum steady flux flow occurs at Mach 1 (Lubow and Shu 1975). The local speed of sound at the L1 point is calculated using thermodynamics. This simulation is used to estimate the accretion disk boundary and dimensions. 
 
Using von Zeipel’s Theorem of gravity darkening and the Stefan-Boltzmann Law, the surface temperature map of the donor has been determined (von Zeipel 1924). The gravity-darkening coefficient is taken as a continuous sigmoid function of surface temperature that matches modern interferometry based on Antonio Claret’s formulation. 

 
5. Results and Conclusion 
 
The mean absolute deviation of the derived parameters from PHOEBE’s model is only 1.09% for Beta Lyrae*. 
 
To test for the generalisability of the framework, it was validated against β Persei, V356 Sgr, RY Scuti, TT Hydrae, and U Cephei as well. The produced parameters were tried against published ones for stellar masses, mass ratio, semi-major axis, equivalent donor radius, effective donor surface temperature and accretion disk size (if applicable); and the following deviations were obtained: 
 
1. β Persei deviated 1.467% on average against the parameters published by Baron et al. 2012, Kolbas et al. 2015 and Hill et al. 1971. 2.  V356 Sgr deviated 4.398% on average against the parameters published by Dominis et al. 2005. 3. RY Scuti deviated 4.562% on average against the parameters published by Gehrz et al. 1995, Grundstrom et al 2007 and Djurašević et al. 2008. 4. TT Hydrae deviated 3.388% on average against the parameters published by Kulkarni & Abhayankar 1981, Budaj et al. 2005, Popper 1979 and Hamme & Wilson 1993. 5. U Cephei deviated 2.348% on average against the parameters published by Tomkin 1981, Olson 1982 and Rensbergen 2011. 
 
 
  6. Limitations 
 
1. The ballistic trajectory simulation approximates the trajectory by neglecting multi-particle gas magnetohydrodynamics. Systemic mass loss via bipolar jets and unstable equilibrium is widely neglected. 
 
2. Magnetic and electric forces and fields are neglected due to the little impact on the parameters concerned. 
 
3.  The parameter sweep technique is currently applied to a relatively small range to preserve reliability. 
 
4. ASTERIA has been tested against a relatively small set of six systems, albeit the fact that this was done to demonstrate the breadth of the programme. 
 
5. ASTERIA employs geometrical assumptions which work in our favour, but should be considered as limitations. The gaining star (often shrouded by an optically thick accretion disk) is especially difficult to model and the prototype currently assumes a constant geometry for it. 
 
6. Comparison and validation has been performed against published literature values rather than independent observation of every system.  
 
 
     7.  Future Scope 
 
Future work will involve refining the current prototype of ASTERIA and adding the following features: 
 
1. An MCMC based Bayesian inference neural network trained by the light curves available in the GAIA Catalog to estimate orbital inclination and eccentricity reliably. 2. Magnetohydrodynamics and multi-particle gas dynamics for better ballistic trajectory simulation and accretion disk modelling and determination of non-conservative mass loss. 3. Non-linear limb-darkening for more accurate temperature mapping 4. Time dependent evolutionary modelling via hybrid computational analysis and Bayesian Inference based on existing data. 

Ak, H., et al. 2007, Astronomy and Astrophysics, 463, 233-241 
Baron, F., et al. 2012, The Astrophysical Journal, 752, 20 
Budaj, J., et al.. 2005, Contributions of the Astronomical Observatory Skalnaté Pleso, 35, 2, 61–74.  
De Greve, J. P., & Linnell A. P. 1994,  Astronomy and Astrophysics, 291, 786-794 
Djurašević, G., et al.  2008, The Astronomical Journal, 136, 2, 767–772 
Dominis, D., et al. 2005, Astrophysics and Space Science, 296, 189–192 
Gehrz, R. D., et al. 1995, The Astrophysical Journal, 439, 417  
Grundstrom, E. D.,  et al. 2007,  The Astrophysical Journal, 667, 1, 505–519  
Hill, et al. 1971, The Astrophysical Journal, 168, 443.  Kolbas, et al. 2015,  Monthly Notices of the Royal Astronomical Society, 451, 4, 4150–4162  
Kulkarni, A. G., & Abhyankar, K. D. 1981, Journal of Astrophysics and Astronomy, 2, 2, 119–132  
Lubow, S. H., & Shu, F. H. 1975, The Astrophysical Journal, 198, 383–405 
Mennickent, R. E., & Djurašević, G. 2013, Monthly Notices of the Royal Astronomical Society, 432(1), 799–809 
Mourard, D., et al. 2018, Astronomy and Astrophysics, 618, A112 
Olson, E. C. 1982,  The Astrophysical Journal, 259, 702–711  
Prša, A., et al. 2016, The Astrophysical Journal Supplement Series, 227, 29 
Tomkin, J. 1981, The Astrophysical Journal, 244, 546–551  
Van Hamme, W., & Wilson, R. E. 1993, Monthly Notices of the Royal Royal Astronomical Society, 262, 1, 220–228  
Van Rensbergen, W., et al. 2011  Astronomy & Astrophysics, 528, A16  
von Zeipel, H. 1924, Monthly Notices of the Royal Astronomical Society, 84, 665  
Wilson, R. E., & Devinney, E. J. 1971, The Astrophysical Journal, 166, 605–619 


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The code uses the photometry_data.csv file to process the photometric data by generating a flux Fourier fit and extracting donor luminosity from the total system luminosity using extrema depth and height of the fit. The photometry_data.csv data in this repository is self collected photometric data of Beta Lyrae using differential photometry.

The current prototype contains some hardcoded parameters such as time period, system luminosity and orbital inclination which must be changed manually when testing binaries other than Beta Lyrae.

The gravity-darkening temperature-map implementation remains under development. Numerical convergence and physical consistency require further validation.

Note some program changes and debugging may lead to slightly different outcomes than those described in the synopsis. The presented results (based on input data from cited sources and AAVSO VSX and AVSPEC) of the synopsis are based on slightly older prototypes of the code.
## Validation and Development Status

Earlier development versions of ASTERIA were compared with published parameters for six eclipsing binary systems: β Lyrae, β Persei, V356 Sagittarii, RY Scuti, TT Hydrae,
and U Cephei.

The reported deviations reflect those earlier versions and should not be assumed to be reproducible with the current prototype without further testing. The current implementation is undergoing continued debugging and validation.

The mathematical framework, modelling objectives, and computational workflow were designed by the author. AI tools were used to assist in translating this framework into a Python implementation due to time and skill constraints.

The resulting code is undergoing testing and validation. The implementation and its numerical outputs should be interpreted in light of the assumptions and limitations documented in this repository.
 
