# README

## Dataset
Our study utilized variants of TEM-1 β-lactamases and their corresponding Minimum Inhibitory Concentration (MIC) values from the dataset (reference). This dataset includes MIC values for 990 variants, classified as resistant or susceptible based on their MIC relative to the wild type (WT) for amoxicillin. Resistance is indicated by positive MIC values, while susceptibility is indicated by negative MIC values. X et al. have compiled a set of clinically occurring variants. We identified variants such as A237T, G238S, and E104K, which have significantly lower MIC values than the WT and were classified as susceptible. In contrast, variants like E240K, N175S, and Q39K, with higher MIC values, were classified as resistant (10.1073/pnas.1215206110). This classification enabled us to create a balanced and representative dataset for our analysis, facilitating the investigation of structural features associated with resistance and susceptibility. By incorporating these MIC values, we ensured that our dataset accurately reflects the experimental resistance profiles of the TEM-1 β-lactamase variants. This approach provides a robust basis for our machine learning models to discern the structural determinants underlying antibiotic resistance.

## REMD Simulations
Each of the six variants and the wild-type protein were subjected to Replica Exchange Molecular Dynamics (REMD) simulations. The OPLS4 force field was used to represent the interaction parameters of the protein atoms, while the TIP3P water model represented solvent interactions. To maintain system neutrality, counter ions were incorporated. Each variant underwent 10 replicate simulations spanning temperatures from 310 K to 328 K, each lasting 100 ns with coordinates recorded every 5 ps. The last 50 ns was utilized to extract dihedral angles as features. The acceptance ratio for temperature shifts in the REMD simulations was found to be between 0.2 and 0.3 for all the simulated systems.

## Dataset & Feature Extraction from REMD Simulations
The φ (phi) and ψ (psi) dihedral angles of each of the 263 amino acid residues in the protein were used as features. These dihedral angle features were extracted for the last 50 ns of each simulation, resulting in 10,000 records per mutant. In total, the dataset comprised 70,000 frames, with 40,000 frames corresponding to susceptible variants and 30,000 frames representing resistant variants. Data balancing techniques were applied to address this discrepancy. Center scaling was performed using Standard Scaler to normalize the data, ensuring consistent scaling across all features for improved model performance.

## Classification Methods for Phenotype Prediction
### (a) Linear Regression
Linear Regression was applied to model the linear relationship between dihedral angles and mutation effects, enabling quantification of the directional impact of structural changes.

### (b) Support Vector Machines (SVM)
Support Vector Machines (SVM) were employed as a classification tool to identify complex, nonlinear patterns within the high-dimensional feature space, allowing for differentiation of subtle variant-induced structural modifications.

### (c) Random Forest
Random Forest, an ensemble-based learning method, was used to enhance prediction accuracy and robustness against noise and overfitting. By training multiple decision trees on the dihedral angle features, Random Forest provided a more stable and generalized model for predicting variant effects.

By integrating these machine learning approaches, we aimed to develop predictive models that reveal the intricate relationship between protein structural dynamics and mutation-induced structural changes.

## Essential Dynamics Analysis
Essential Dynamics Analysis was conducted based on the last 50 ns to examine the dynamics of the protein. This involved calculating the covariance matrix based on the coordinates of C-alpha atoms and performing a principal component analysis to obtain the eigenvectors and their corresponding eigenvalues. The eigenvectors denote the principal directions of motion, while the eigenvalues represent the amplitude of motion along the corresponding eigenvector. To quantify the similarity in the directions of motion between two different protein trajectories, an inner product matrix was plotted using GROMACS 2023.3. For the Root Mean Square Inner Product (RMSIP) analysis, we extracted the PDB structure every 100 ps during the final 50 ns.

## Residue Interaction Network
The residue interaction network was constructed using RING 4.0 [ref]. The conformations in the last 50 ns were used for network construction. The interaction network was constructed using hydrogen bonds. We analyzed the hydrogen bond frequency network using RING 4.0 for the retrieved PDB structure over the last 50 ns.

