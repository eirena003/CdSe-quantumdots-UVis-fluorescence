# Modeling CdSe Quantum Dot Growth: Synthesis, Characterization, and Cross-Dataset Validation of Emperical and Theoretical Models
All data of UV-Vis and fluorescence were collected at Dickinson College - Department of Chemistry

## I. Background
Quantum dots (QDs) are nanoscale semiconductor particles with unique optical and electronic properties due to their small size. In **Band Theory** (Fig. 1), the number of orbitals is proportional to the number of atoms bound to each other. Bulk materials have countless combined atoms, so is the number of bands, meaning that the energy gap between bands is very small or almost negligible. 
For nanomaterials, every particle has only several hundred to thousands of atoms, making their energy gap much wider. The specific color of quantum dots can be tuned by modifying their size: a smaller size (fewer atoms) comes with fewer bands and thus larger band gaps and higher energy emitted when the electron recombines after being excited. This explains why quantum dots turn more from blue to red as they become larger (Fig. 2) - as the red wavelength has smaller energy than blue one. 
For bulk semiconductors, the emitted energy is much smaller (larger wavelengths), which is below the visible light range, explaining why the color displayed at nanosize does not occur in bulk semiconductors. 

<div align="center">

![image](https://github.com/user-attachments/assets/ff7a2778-a8fc-45a8-9390-4342223ef03b)

**Fig. 1**: [Band Structure](https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Supplemental_Modules_(Physical_and_Theoretical_Chemistry)/Chemical_Bonding/Fundamentals_of_Chemical_Bonding/Band_Structure), LibreTexts, accessed May 7, 2025. Licensed under CC BY-NC-SA 4.0.

![image](https://github.com/user-attachments/assets/988d62e3-6e8e-44f5-b81c-524c660fb102)

**Fig. 2**: [Engineered Nanomaterials and Their Properties: A Review](https://bbrc.in/engineered-nanomaterials-and-their-properties-a-review-2/), Bioscience Biotechnology Research Communications, accessed May 7, 2025.
</div>
In this experiment, we use the particle-in-1D-box model (Fig. 3) to simplify the calculations of the QDs size. We treat the QDs diameter as the box length for the derivation of energy from the Schrödinger Equation, and while the energy of the box can be calculated with measured UV-Vis absorbed or Fluorescence emitted wavelengths, the diameter can be estimated.

<div align="center">
  
![image](https://github.com/user-attachments/assets/d4d666c5-1f9d-4fde-9341-40185a4a54f5)

**Fig. 3**: [Particle in a Box](https://en.wikipedia.org/wiki/Particle_in_a_box), Wikipedia, accessed May 7, 2025. Licensed under CC BY-NC-SA 4.0.
</div>

#### Note
You can refer to this source for more details about Schrödinger Equation and the quantization of energy: [Particle in a 1-Dimensional Box](https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Supplemental_Modules_(Physical_and_Theoretical_Chemistry)/Quantum_Mechanics/05.5%3A_Particle_in_Boxes/Particle_in_a_1-Dimensional_box), LibreTexts.
The Band Theory used to explain the color change in nanomaterials for this experiment is only applied to semiconductor materials. For metals, such as gold and silver, their color also changes as size decreases to the nanoscale, but the mechanism behind is called **Surface Plasmon Resonance**, which is different from **Band Theory**. Further details about nanometal particles can be explored via this link [Nanoscale Metal Particles](https://chem.libretexts.org/Bookshelves/Inorganic_Chemistry/Introduction_to_Inorganic_Chemistry_(Wikibook)/11%3A_Basic_Science_of_Nanomaterials/11.06%3A_Nanoscale_Metal_Particles), LibreTexts.

## II. General procedures: 
### a. Synthesis
Selenium was dissolved in 1-octadecene, with trioctylphosphine being added as a ligand. Se solution was then combined with reaction solution containing proportionate amounts of CdO, oleic acid, and octadecene that had just been heated to 225 degrees Celsius. Ater that, Pasteur pipet was used to rapidly remove approximately 1 mL samples at frequent intervals. 9 CdSe quantum dot samples were successfully collected. Some samples were removed for their unreliable UV-Vis and/or Fluorescence values. Refer to [A Safer, Easier, Faster Synthesis for CdSe Quantum Dot Nanocrystals](https://doi.org/10.1021/ed082p1697) (Boatman and Lisensky, 2005) for further details about the synthesis conditions. 
### b. Characterizations
UV-Vis and fluorescence measurements were performed on all samples to estimate the quantum dots' diameter value. The excited wavelength for fluorescence is 360 nm. Data were cleaned, processed, and analyzed with Python to generate visualizations.

## III. Radius calculations
Quantum dots are treated as a particle in a box, so their energy is calculated based on this model. For UV-Vis, Brus equation (Quantum confinement effect) is used as the absorbance is directly related to QDs band gap energy, which is obtained by adding the band gap energy of CdSe bulk materials and particle-in-a-box energies of electron and hole. In the Brus equation, Column interaction is also considered, so the effective masses of the electron and hole are used, and the binding exciton energy is taken into account. 
For Fluorescence, emission energy is estimated by adding the ground state energy of CdSe with the particle-in-a-box energies of the free electron and hole. Fluorescence model is  simpler and open compared to the UV-Vis model. Below is the detailed derivation  of the two equations.
### A. Overview
This document derives two approaches to calculate the radius of a semiconductor quantum dot: the **Brus equation** using UV-Vis absorbance data (including the Coulomb interaction term) and a simplified **fluorescence equation** using emission energy (neglecting the Coulomb term). Both derivations build on the particle-in-a-box model. For the fluorescence approach, we use the free electron mass for both the electron and hole (denoted \( m_e \) and \( m_h \), where \( m_e = m_h = 9.11 \times 10^{-31} \, \text{kg} \)), ignoring lattice effects typically accounted for by effective masses. We explain why neglecting the Coulomb term is a reasonable approximation in this context. A comparison of the two approaches is provided at the end.
### B. Particle in a Box: Energy Quantization
For a particle confined in a 1D cubic box with side length L and infinite potential barriers, the Schrödinger equation yields quantized energy levels. The wavefunction is:

$$ \psi(x, y, z) = \left( \frac{2}{L} \right)^{1/2} \sin\left( \frac{n_x \pi x}{L} \right) $$

where n is quantum numbers.

The energy is:

$$ E = \frac{\hbar^2 \pi^2}{2 m L^2} (n^2) $$

For the ground state (n = 1):

$$ E = \frac{ \hbar^2 \pi^2}{2 m L^2} $$

### C. Quantum Dot as a Spherical Box
A quantum dot is approximated as a spherical potential well with radius r. Solving the Schrödinger equation in spherical coordinates (with infinite barriers) gives the ground state energy for a particle of mass \( m \), with this conversion: $\hbar^2=\frac{h^2}{4\pi^2}$

$$ E \approx \frac{h^2 \pi^2}{8 m r^2} $$

This is the confinement energy for a single particle, where r is the radius of the quantum dot.

### D. Confinement Energy
- Electron confinement energy:
  $$E_e = \frac{\hbar^2 \pi^2}{2 m_e r^2}$$
- Hole confinement energy:
  $$E_h = \frac{\hbar^2 \pi^2}{2 m_h r^2}$$
- Total confinement energy:
  $$E_{\text{confinement}} = \frac{\hbar^2 \pi^2}{2 r^2} \left( \frac{1}{m_e} + \frac{1}{m_h} \right)$$

### E. Comparison of Fluorescence and Brus Equation Approaches
| **Aspect**               | **Fluorescence Approach**                                      | **Brus Equation Approach (UV-Vis)**                           |
|--------------------------|---------------------------------------------------------------|-------------------------------------------------------------|
| **Measurement**          | Uses emission energy $E_{\text{emission}} = \frac{h c}{\lambda_{\text{max}}}$ from fluorescence. | Uses absorption energy $E_g^{\text{nano}}$ from UV-Vis absorbance. |
| **Coulomb Term**         | Neglected, justified by Stokes shift and free mass approximation. | Included (\( -\frac{1.8 e^2}{4 \pi \epsilon_0 \epsilon r} \)), critical for accuracy. |
| **Masses Used**          | Free masses $m_e = m_h$, ignoring lattice effects.      | Uses effective masses ($m_e^*$, $m_h^*$), material-specific. |
| **Equation**             | $$r = \sqrt{\frac{h^2}{4 m_e \left( \frac{h c}{\lambda_{\text{max}}} - E_g \right)}}$$ | $$\frac{h^2}{8 r^2} \left( \frac{1}{m_e^*} + \frac{1}{m_h^*} \right) - \frac{1.8 e^2}{4 \pi \epsilon_0 \epsilon r} + (E_g^{\text{bulk}} - E_g^{\text{nano}}) = 0$$ |
| **Complexity**           | Simpler, linear in \( 1/r^2 \), analytical solution.          | More complex, nonlinear due to \( 1/r \) term, often requires numerical solution for \( r \). |
| **Accuracy**             | Less accurate due to neglected Coulomb term and free masses, but Stokes shift compensates somewhat. | More accurate, as it includes Coulomb interaction and uses effective masses. |
| **Use Case**             | Quick estimate using fluorescence data, simplified model.     | Precise calculation using absorbance data, standard in literature. |

### E. Conclusion
The Brus equation for UV-Vis absorbance is:

$$\frac{h^2}{8 r^2} \left( \frac{1}{m_e^*} + \frac{1}{m_h^*} \right) - \frac{1.8 e^2}{4 \pi \epsilon_0 \epsilon r} + (E_g^{\text{bulk}} - E_g^{\text{nano}}) = 0$$

The fluorescence equation, using free masses, is:

$$r = \sqrt{\frac{h^2}{4 m_e \left( \frac{h c}{\lambda_{\text{max}}} - E_g \right)}}$$

Both equations use a denominator of 8 in the confinement term when written in the standard form (\( \frac{h^2}{8 r^2} \left( \frac{1}{m_e} + \frac{1}{m_h} \right) \)). The fluorescence approach neglects the Coulomb term, simplifying the calculation, and is justified by the Stokes shift and the use of free masses, which ignore lattice effects like dielectric screening. The Brus equation is more accurate for precise calculations, as shown in the comparison table.



