# NeuroFold Pro — AI-Driven Protein Folding Simulator

**NeuroFold Pro** is a browser-based, single-file protein folding simulator and research-inspired visual analysis tool. It turns amino-acid sequences into an interactive 3D folding experience with neural-network-style prioritisation, sequence feature extraction, confidence visualisation, energy tracking, mutation scanning, contact-map analysis, and export tools.

> **Important:** NeuroFold Pro is an educational and exploratory simulator. It does **not** run AlphaFold, ESMFold, Boltz, RoseTTAFold, Rosetta, molecular dynamics, quantum chemistry, or wet-lab validation. Its outputs are heuristic visual approximations designed for learning, prototyping, and interface experimentation.

---

## Preview

NeuroFold Pro runs entirely in the browser as one HTML file.

```text
Protein sequence → feature extraction → heuristic folding → 3D visualisation → confidence + analytics → export
```

Recommended filename for deployment:

```text
index.html
```

---

## Key Features

### Protein Input & Presets

- Paste raw amino-acid sequences or FASTA-style text.
- Automatic sequence cleaning for valid 1-letter amino-acid codes.
- Built-in preset proteins and fragments, including:
  - Insulin B-chain
  - Myoglobin fragment
  - Lysozyme fragment
  - Ubiquitin
  - GFP fragment
  - Hemoglobin α
  - Collagen fragment
  - Random sequence generator

### Sequence Quality Gate

The app gives immediate feedback before folding:

- Residue count
- Valid amino-acid percentage
- Sequence diversity / entropy
- Low-complexity warnings
- Proline-rich warnings
- Disulfide-link hints from cysteine pairs
- Large-sequence performance warnings

### Interactive 3D Protein Viewer

The centre canvas renders a simplified protein structure with:

- Backbone view
- Ribbon view
- Space-fill view
- Mouse drag rotation
- Scroll zoom
- Auto-spin toggle
- Camera reset
- Folding play/pause control
- Grid-style depth reference
- Residue colour coding by amino-acid properties
- Dashed long-range cysteine/disulfide-style bonds

### Heuristic Folding Simulation

The folding engine includes:

- Secondary-structure-informed target generation
- Alpha-helix, beta-sheet, turn, and coil behaviours
- Hydrophobic-collapse-style target adjustment
- Spring-like movement toward folded targets
- Thermal noise and damping
- Bond length constraints
- Energy trajectory tracking
- RMSD-like distance-to-target feedback
- Temperature-style annealing display

### Neural Network Priority Analysis

NeuroFold Pro includes a lightweight in-browser neural-network-style scoring system using sequence-derived features:

- Hydrophobicity index
- Charge distribution
- Complexity score
- Disorder propensity
- Sequence length normalisation
- Aromatic residue ratio
- Polar residue ratio
- Hydrophobic run detection
- Proline content
- Cysteine content
- Medical relevance heuristic
- Priority score for simulation attention

### Research-Inspired Modes

The upgraded research layer adds multiple prediction lenses:

| Mode | Purpose |
| --- | --- |
| **AlphaFold-style confidence** | pLDDT-style local confidence, contact maps, PAE-style uncertainty, calibrated warnings |
| **ESM-style fast sequence lens** | Fast sequence-only interpretation focused on residue features and sequence-derived heuristics |
| **Diffusion ensemble explorer** | Adds flexible-region noise and multiple plausible conformational basin behaviour |
| **Complex / ligand-aware flags** | Highlights cysteine, charged, aromatic, and surface-like regions that may matter for interactions |

### Confidence & Structure Analytics

The right-side panel provides:

- pLDDT-style confidence meter
- Per-residue confidence strip
- Contact map
- PAE-style uncertainty map
- Predicted secondary-structure bar
- Alpha-helix / beta-sheet / turn / coil percentages
- Energy trajectory chart
- Ramachandran-style plot
- Domain / region sketch
- Contact density estimate
- Heuristic warning report

### Mutation Scanner

Run simple mutation comparisons such as:

```text
A12G
V45D
K8A
```

The scanner compares:

- Priority score change
- Hydrophobicity change
- Disorder change
- Local confidence change
- Whether the original residue matches the selected position

It can also suggest stabilising mutation ideas based on low-confidence, proline-heavy, or strongly polar/charged regions.

### Export & Local Save

NeuroFold Pro can export:

- JSON analysis reports
- Pseudo-PDB CA-only coordinate files
- Locally saved project state via `localStorage`

Keyboard shortcuts:

| Key | Action |
| --- | --- |
| `Space` | Fold / pause |
| `S` | Save project locally |
| `E` | Export JSON analysis |
| `R` | Reset camera |

---

## How to Use

### 1. Open the App

Download or clone the project, then open the HTML file directly in a browser:

```bash
open index.html
```

Or on Windows, double-click the file.

No installation, server, API key, or build step is required.

### 2. Enter a Protein Sequence

Use either a preset or paste your own sequence:

```text
MVLSPADKTNVKAAWGKVGAHAGEYGAEALERMFLSFPTTKTYFPHFDLSH
```

The app accepts only the 20 standard amino-acid one-letter codes:

```text
A C D E F G H I K L M N P Q R S T V W Y
```

### 3. Choose a Prediction Lens

Select one of the research-inspired modes:

- AlphaFold-style confidence
- ESM-style fast sequence lens
- Diffusion ensemble explorer
- Complex / ligand-aware flags

### 4. Analyse & Fold

Click **Analyze & Fold** to:

- Extract sequence features
- Score the protein with the priority network
- Predict simplified secondary structure
- Generate a folded target
- Start the visual simulation
- Populate the analytics panels

### 5. Explore the Result

Use the viewer controls to switch between structural display modes, spin the model, pause folding, or reset the camera.

### 6. Export

Use the export buttons to download:

- A JSON analysis report
- A pseudo-PDB file containing generated CA-only coordinates

---

## Project Structure

Current version is intentionally simple:

```text
neurofold-pro/
├── index.html      # Complete app: HTML, CSS, and JavaScript in one file
└── README.md       # Project documentation
```

The single-file design makes it easy to host on GitHub Pages, Netlify, Vercel static hosting, or any normal web server.

---

## Scientific Framing

NeuroFold Pro is inspired by ideas from modern protein-structure prediction and protein-design interfaces, including:

- Local confidence visualisation similar to pLDDT-style interpretation
- Pairwise uncertainty visualisation similar to PAE-style maps
- Sequence-only embedding approaches inspired by protein language models
- Diffusion-style ensemble thinking for uncertain conformations
- Mutation scanning and propose-score-review protein-design workflows
- Contact-map-style structural interpretation

However, the app does not perform real deep-learning inference with trained biological models. It uses browser-friendly heuristics so the concepts are visible, interactive, and fast.

---

## Limitations

NeuroFold Pro should not be used for:

- Clinical decisions
- Drug discovery decisions
- Real mutation pathogenicity prediction
- Real protein stability prediction
- Experimental structure replacement
- Publication-grade structural biology
- Docking, binding-affinity, or ligand-screening conclusions

Main technical limitations:

- Uses simplified CA-like residue points, not full atomic coordinates
- Uses heuristic secondary-structure prediction
- Does not use multiple sequence alignments
- Does not call external model APIs
- Does not run molecular dynamics
- Does not validate stereochemistry
- Ramachandran and energy plots are educational approximations
- PAE/contact/confidence maps are heuristic, not model-calibrated outputs

---

## Browser Support

Recommended:

- Chrome / Chromium
- Edge
- Firefox
- Safari

Best experience is on a modern desktop browser. Very long sequences may slow down canvas rendering because all analysis runs locally in the browser.

---

## Deployment

### GitHub Pages

1. Rename the app file to `index.html`.
2. Put it in the root of the repository.
3. Commit and push.
4. Open repository **Settings → Pages**.
5. Set source to the main branch root.
6. Visit the generated Pages URL.

### Static Hosting

You can also upload `index.html` to any static host:

- Netlify
- Vercel
- Cloudflare Pages
- GitHub Pages
- Itch.io HTML project page
- Any normal web server

---

## Development Notes

The app is currently dependency-free and uses:

- Plain HTML
- CSS custom properties
- Vanilla JavaScript
- Canvas 2D rendering
- Browser `localStorage`
- Browser `Blob` downloads

There is no package manager or build tool required.

---

## Possible Future Improvements

High-impact next steps:

- Add optional WebGL or Three.js rendering mode
- Add real PDB import/export support
- Add mmCIF parsing
- Add chain support for multi-protein complexes
- Add ligand placeholder objects and binding-pocket sketches
- Add side-chain rotamer visualisation
- Add real model integration through optional APIs
- Add Web Worker simulation loop for smoother performance
- Add WebGPU acceleration for pairwise maps
- Add screenshot/export image tools
- Add shareable project URLs
- Add comparison mode for wild type vs mutant structures
- Add sequence annotation tracks
- Add accessibility improvements for colour-blind confidence maps
- Add unit tests for sequence parsing and feature extraction

Research-level future ideas:

- Optional AlphaFold/Boltz/RoseTTAFold API connector layer
- Protein language model embedding visualiser
- Diffusion trajectory playback
- Real multiple-sequence-alignment import
- Evolutionary conservation track
- Binding-site probability heatmap
- Stability-change scoring panel
- Molecular dynamics-style relaxation preview

---

## Educational Use Cases

NeuroFold Pro is useful for:

- Learning how amino-acid properties influence folding
- Teaching protein secondary structures
- Demonstrating confidence and uncertainty concepts
- Exploring mutation effects visually
- Prototyping scientific UI ideas
- Building portfolio projects around computational biology
- Showing the difference between educational simulation and validated prediction

---

## Example Sequence

```text
MVLSPADKTNVKAAWGKVGAHAGEYGAEALERMFLSFPTTKTYFPHFDLSH
```

Suggested mutation test after analysing:

```text
V2D
```

---

## Disclaimer

This project is for education, visualisation, and creative research-interface prototyping. All generated structures, scores, confidence values, mutation suggestions, energies, contacts, and PDB exports are approximate and should be treated as simulated outputs only.

For real scientific work, compare against validated tools, experimental structures, peer-reviewed methods, and domain-expert review.

---

## License

MIT License recommended.

You may use, modify, and extend this project for learning, research prototyping, portfolio work, or open-source development.

---

## Credits

Built as a browser-first computational biology interface experiment.

Concepts inspired by modern protein-folding, protein-language-model, uncertainty-estimation, and protein-design workflows.
