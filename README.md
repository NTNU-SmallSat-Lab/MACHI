# MACHI
Minimal Atmospheric Compensation for Hyperspectral Images:

![image](https://github.com/user-attachments/assets/fd193602-1a02-46cb-a037-13f6b04a1076)


Strictly speaking, only Numpy is required, but the demo relies on the [HYPSO package](https://github.com/NTNU-SmallSat-Lab/hypso-package). 

The atmospheric correction is written at R_surface = (R_ToA - S) / T, where S is the amount of sunlight scattered off the atmospher back to the satellite (as a fraction of solar irradiance) and T is the proportion of light transmitted through the atmosphere.  
The variable S is initialized with the *dark pixel subtraction* technique, and T is initiallized as 1-S_0. This initialization is expected to be updated in a future version. 

![image](https://github.com/user-attachments/assets/8a50dbc2-8a38-4ff8-aa3f-9dd6c72bff7b)


The the MACHI algorithm alternately updates estimates of the transmission and scattering in order to minimize the derivative of the spectra with respect to wavelength, averaged over the whole image. 
This objective function roughly corresponds to the notion that the reflectance spectra of most materials are relatively smooth, while the gaseous transmission spectra through the atmosphere are not. 

![image](https://github.com/user-attachments/assets/a96da8f0-e62f-48e1-93de-790732b635a0)

**Beware** of trusting MACHI too much:
1. Minimal in situ validation​ (we're working on this!)
2. Simplistic light propagation model​
3. Needs "expected minimum reflectance" input (default 1%)​
4. Can't (yet) handle AC varying across image, alhtough it does vary (aerosols, sun glint, water vapor)​
5. Problems with nearly complete absorption within a band​
6. No sun glint correction at all​
7. Poor estimation of Rayleigh and aerosol scattering​, because they are spectrally smooth


If you find this useful, please let us know and we'll share a draft of our upcoming paper. If you are interested in assisting with in situ validation, we'd be happy for you to join us. 
