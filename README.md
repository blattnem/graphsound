I apologize for the oversight. Here's the revised README with LaTeX equations properly wrapped in `$$`.

# Graph Eigenvalue Sound Generator

## Overview

The Graph Eigenvalue Sound Generator is a specialized Streamlit application that combines graph theory with sound synthesis. Users select graph topologies, triggering the computation of adjacency matrices and eigenvalues, which are then used to generate both sound and visualizations. This interdisciplinary project encompasses graph theory, audio synthesis methodologies, and spectral representations to offer a multi-sensory experience.

## Requirements

- Streamlit
- NumPy
- NetworkX
- sounddevice
- Matplotlib
- SciPy

## Installation

To install the required libraries, run:

```bash
pip install streamlit numpy networkx sounddevice matplotlib scipy
```

## Functions

### `generate_sound_and_visuals(G, audio_type, modulation_index, spectrum_type, pitchtime)`

#### Parameters

- `G`: NetworkX graph object.
- `audio_type`: String indicating the audio type ('Sine Wave', 'Square Wave', etc.).
- `modulation_index`: Float for the modulation index.
- `spectrum_type`: String for the type of spectral representation ('Adjacency Matrix', 'Laplacian', 'Modularity').
- `pitchtime`: Duration of each pitch in seconds.

#### Returns

- None; generates sound and plots as side effects.

#### Raises

- `ValueError`: Unsupported `audio_type`.
- `LinAlgError`: Eigenvalue computation fails.

#### Notes

- Uses NetworkX for graph analysis, sounddevice for audio generation, Matplotlib for plotting, and Streamlit for the UI.

## Mathematical Concepts

### Calculating Eigenvalues

Eigenvalues $ \lambda $ for the adjacency matrix $$ A $$ are computed by solving the characteristic equation:

$$ \text{det}(A - \lambda I) = 0 $$

### Eigenvalues in Sound Generation

Eigenvalues are normalized and mapped to frequencies to generate unique audio textures. These are used in methods like FM Synthesis and Waveshaping Synthesis to modulate carrier frequencies.

### Adjacency Matrix Spectrum

The adjacency matrix $$ A $$ is an $$ n \times n $$ square matrix where:

$$ A_{ij} = \begin{cases} 
1 & \text{if there is an edge between nodes \( i \) and \( j \)} \\
0 & \text{otherwise}
\end{cases} $$

### Additional Spectra

- **Laplacian Spectrum**: 

$$ L = D^{-\frac{1}{2}} A D^{-\frac{1}{2}} $$

- **Modularity Spectrum**: 

$$ B = A - \frac{k_i k_j}{2m} $$

### Audio Types

- **Sine Wave**: 

$$ \sin\left((\text{norm\_eigenvalue} + \text{modulating\_frequency} \cdot \sin(2\pi \cdot \text{modulating\_frequency} \cdot t)) \cdot 2\pi \cdot t\right) $$

- **Square Wave**: 

$$ \text{sign}(\sin(2\pi \cdot \text{norm\_eigenvalue} \cdot t)) $$

- **Sawtooth Wave**: 

$$ 0.5 \cdot \left(1 - \frac{\arctan(\sin(2\pi \cdot \text{norm\_eigenvalue} \cdot t))}{\pi}\right) $$

- **FM Synthesis**: 

$$ \sin(2\pi \cdot \text{carrier\_freq} \cdot t + \sin(2\pi \cdot \text{modulating\_freq} \cdot t)) $$

- **Waveshaping Synthesis**: 

$$ \text{sign}(\text{audio}) \cdot (1 - e^{-|\text{audio}|}) $$

## Usage

1. Launch the Streamlit application.
2. Configure graph topology, node count, and other parameters through the sidebar.
3. Click "Generate Sound and Visuals" to produce audio and visuals.

For more detailed information on each section, consult the inline code comments.

---

For contributions or reporting issues, please visit the project's GitHub repository.