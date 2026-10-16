# ECE441 Lab 3

EEG analysis of two OpenBCI recordings collected during intermittent photic stimulation. The Jupyter notebook covers data loading, filtering, bad-channel marking, power spectra, and independent component analysis (ICA).

## Files

- `lab3.ipynb`: analysis code, notes, and saved plots.
- `requirements.txt`: Python dependencies. MNE 1.13 or later is required for the `rng` parameter.
- `electrode_positions_8channel.sfp`: electrode coordinates used for the montage.
- `.vscode/`: Python interpreter settings and recommended extensions.

## Run the notebook

The notebook was developed with Python 3.11 and MNE 1.13.2.

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Obtain `RecA.txt` and `RecB.txt` from the course-provided lab files and place them beside the notebook. The raw recordings are not included in this repository.

Open the folder in VS Code, install the recommended Python and Jupyter extensions, and select `.venv` as the notebook kernel. Restart the kernel and run the cells in order.

## Analysis

The recordings contain eight EEG channels sampled at 250 Hz. The workflow applies a 0.1–100 Hz bandpass and a 60 Hz notch, marks C3 and C4 as bad, and computes channel spectra from 1–30 Hz. Separate copies receive a 1 Hz high-pass before fitting six-component ICA models.

The original bandpass filter is longer than the approximately 25-second recordings, and MNE reports possible distortion. Frequency estimates in the notebook are exploratory; convergence of ICA does not by itself validate a physiological interpretation.

The notebook code is unchanged from the working copy. Saved outputs have been cleaned of local filesystem paths. The LaTeX report, report figures outside the notebook, virtual environment, and report archive are excluded.
