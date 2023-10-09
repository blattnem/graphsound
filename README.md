# Graph Eigenvalue Sound Generator

## Overview

The code is a Streamlit application that generates sound and visuals based on a selected graph topology. It computes the adjacency matrix and eigenvalues of the graph and then uses these to produce sound and visual outputs. The application offers various options for graph types, audio types, and spectral representations.

## Requirements

- Streamlit
- NumPy
- NetworkX
- sounddevice
- Matplotlib
- SciPy

## Functions

#### `generate_sound_and_visuals(G, audio_type, modulation_index, spectrum_type, pitchtime)`

#### Parameters:

- `G`: A NetworkX graph object.
- `audio_type`: A string indicating the type of audio to be generated ('Sine Wave', 'Square Wave', etc.).
- `modulation_index`: A float specifying the modulation index for the sound.
- `spectrum_type`: A string specifying the type of spectral representation ('Adjacency Matrix', 'Laplacian', 'Modularity').
- `pitchtime`: Duration of each pitch in seconds.

#### Returns:
- None. Side effects include generating sound and displaying plots.

#### Raises:
- `ValueError`: If `audio_type` is not supported.
- `LinAlgError`: If eigenvalue computation fails.

#### Notes:
- Utilizes NetworkX for graph analysis, sounddevice for sound generation, Matplotlib for plotting, and Streamlit for UI layout.

---

## Mathematical Formulas

### Adjacency Matrix Spectrum

The adjacency matrix A is a square matrix where $$A_{ij}$$ is 1 if there is an edge between nodes i and j, and 0 otherwise.

### Laplacian Spectrum

The normalized Laplacian matrix L is calculated as:

$$
L = D^{-\frac{1}{2}} A D^{-\frac{1}{2}}
$$

where D is the diagonal matrix of node degrees and A is the adjacency matrix.

### Modularity Spectrum

The modularity matrix B is calculated as:


$$B = A - \frac{k_i k_j}{2m}$$

where A is the adjacency matrix, k is the degree of nodes, and m is the total number of edges.



### Audio Types

- **Sine Wave**: 
$$\sin\left((\mathrm{norm\_eigenvalue} + \mathrm{modulating\_frequency} \cdot \sin(2\pi \cdot \mathrm{modulating\_frequency} \cdot t)) \cdot 2\pi \cdot t\right)$$

- **Square Wave**:
$$\mathrm{sign}(\sin(2\pi \cdot \mathrm{norm\_eigenvalue} \cdot t))$$

- **Sawtooth Wave**:
$$0.5 \cdot \left(1 - \frac{\arctan(\sin(2\pi \cdot \mathrm{norm\_eigenvalue} \cdot t))}{\pi}\right)$$

- **FM Synthesis**:
$$\sin(2\pi \cdot \mathrm{carrier\_freq} \cdot t + \sin(2\pi \cdot \mathrm{modulating\_freq} \cdot t))$$

- **Waveshaping Synthesis**:
$$\mathrm{sign}(\mathrm{audio}) \cdot (1 - e^{-|\mathrm{audio}|})$$





---

## Usage

1. Run the Streamlit application.
2. Choose the graph topology, number of nodes, and other parameters from the sidebar.
3. Click "Generate Sound and Visuals" to see the plots and hear the sound.

For more details on each section, refer to the comments within the code.

