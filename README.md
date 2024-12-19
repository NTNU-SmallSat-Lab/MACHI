# MACHI
Minimal Atmospheric Compensation for Hyperspectral Images

Strictly speaking, only Numpy is required, but the demo relies on the [HYPSO package](https://github.com/NTNU-SmallSat-Lab/hypso-package). 

The atmospheric correction is written at R_surface = (R_ToA - S) / T, where S is the amount of sunlight scattered off the atmospher back to the satellite (as a fraction of solar irradiance) and T is the proportion of light transmitted through the atmosphere.  
The variable S is initialized with the *dark pixel subtraction* technique, and T is initiallized as 1-S_0. This initialization is expected to be updated in a future version. 
Then the MACHI algorithm alternately updates estimates of the transmission and scattering in order to minimize the derivative of the spectra with respect to wavelength, averaged over the whole image. 
This objective function roughly corresponds to the notion that the reflectance spectra of most materials are relatively smooth, while the gaseous transmission spectra through the atmosphere are not. 
