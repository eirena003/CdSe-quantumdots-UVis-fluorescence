# Modeling CdSe Quantum Dot Growth: Synthesis, Characterization, and Cross-Dataset Validation of Emperical and Theoretical Models
All data of UV-Vis and fluorescence were collected at Dickinson College - Department of Chemistry

### I. Background
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

### II. General procedures: 
#### a. Synthesis
Selenium was dissolved in 1-octadecene, with trioctylphosphine being added as a ligand. Se solution was then combined with reaction solution containing proportionate amounts of CdO, oleic acid, and octadecene that had just been heated to 225 degrees Celsius. Ater that, Pasteur pipet was used to rapidly remove approximately 1 mL samples at frequent intervals. 9 CdSe quantum dot samples were successfully collected. Some samples were removed for their unreliable UV-Vis and/or Fluorescence values. Refer to [A Safer, Easier, Faster Synthesis for CdSe Quantum Dot Nanocrystals](https://doi.org/10.1021/ed082p1697) (Boatman and Lisensky, 2005) for further details about the synthesis conditions. 
#### b. Characterizations
UV-Vis and fluorescence measurements were performed on all samples to estimate the quantum dots' diameter value. The excited wavelength for fluorescence is 360 nm. Data were cleaned, processed, and analyzed with Python to generate visualizations.
### III. Diameter calculations: 
Quantum dots are treated as a particle in a box, so their energy is calculated based on this model. For UV-Vis, Brus equation (Quantum confinement effect) is used as the absorbance is directly related to QDs band gap energy, which is obtained by adding the band gap energy of CdSe bulk materials and particle-in-a-box energies of electron and hole. In the Brus equation, Column interaction is also considered, so the effective masses of the electron and hole are used, and the binding exciton energy is taken into account. 
For Fluorescence, emission energy is estimated by adding the ground state energy of CdSe with the particle-in-a-box energies of the free electron and hole. Fluorescence model is  simpler and open compared to the UV-Vis model.
### IV. Mathematical Models:
Relevant parameters that affect the synthesis process, such as reaction time, instantaneous temperature, and its rising time, are studied to generate models to predict UV absorbed wavelength. 
