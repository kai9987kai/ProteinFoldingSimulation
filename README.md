# ProteinFoldingSimulation
Single-file website with 3D protein visualization, a neural network prioritizer, and folding simulation
What This Includes
🧠 Neural Network Priority System
12-input feature extraction from amino acid sequences (hydrophobicity, charge distribution, complexity/Shannon entropy, disorder propensity, medical relevance, etc.)
4-layer neural network (12→24→16→8→1) with ReLU activations and sigmoid output
Live NN visualization showing node activations and connection weights
Proteins are sorted in queue by priority score — the NN decides what gets folded first
🔬 Protein Folding Simulation
Physics-based folding with spring forces, thermal noise, simulated annealing (temperature decreases over time), and bond constraints
Hydrophobic collapse — hydrophobic residues are pulled toward the protein core
Secondary structure prediction (α-helix, β-sheet, turns, coils) based on Chou-Fasman-style propensities
Target structures generated from predicted secondary structure
🎨 3D Visualization
Three rendering modes: Backbone, Ribbon, and Space-fill
Interactive camera — drag to rotate, scroll to zoom
Auto-spin toggle, depth-sorted rendering with painter's algorithm
Per-atom coloring by amino acid type with glow effects
📊 Analytics Dashboard
Energy trajectory chart showing free energy minimization over time
Ramachandran plot (φ/ψ dihedral angle distribution)
Per-residue confidence map (pLDDT-style)
Secondary structure bar with composition percentages
Real-time RMSD, temperature, and step counter
🧬 Preset Proteins
Insulin, Myoglobin, Lysozyme, Ubiquitin, GFP, Hemoglobin, Collagen, and random sequence generator
