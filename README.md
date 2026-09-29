Perovskite Solar Cell Interactive Simulation

Overview

index.html is a self-contained, offline HTML/JavaScript simulation of a planar n–i–p halide-perovskite solar cell. It uses Canvas 2D for the device animation and an energy-level diagram, with no external assets, libraries, or network calls.

The animation is intended as a physically informed teaching and presentation tool, not as a TCAD-grade quantitative device simulator.

Device architecture

The simulated structure is:

Glass/FTO | TiO₂ | NDI | Perovskite | Spiro-OMeTAD | Ag

Front illumination enters through the FTO side.

Default thicknesses:

TiO₂: 200 nm

NDI: 5 nm

Perovskite: 500 nm

Spiro-OMeTAD: 150 nm

What the animation shows

The 30-second master loop is divided into three time-dilated phases:

0–10 s — Absorption and pair generation
Photons enter the absorber. Their absorption positions are sampled from a compact Beer–Lambert model using wavelength-dependent absorption coefficients. Absorption generates a short-lived exciton representation followed by free electron–hole pairs.

10–20 s — Dissociation and boundary transport
Electrons migrate toward the ETL/perovskite boundary, while holes migrate toward the perovskite/HTL boundary.

20–30 s — Extraction and collection
Electrons move through the electron-transport stack toward the FTO cathode. Holes move through Spiro-OMeTAD toward the Ag anode.

The visualisation uses approximately 12 representative photogenerated pairs per loop so that the individual generation, migration, and extraction events remain easy to see.

Energy-level diagram

The lower Canvas region contains two deliberately separated energy channels:

Electron channel: CBM/LUMO, shown in blue.

Hole channel: VBM/HOMO, shown in red.

The levels are drawn as straight horizontal segments with sharp vertical interface steps. The electron and hole channels occupy separate vertical drawing regions, preventing the two level lines from visually intersecting.

The supplied vacuum-referenced values are retained:

Material

Electron level

Hole level

FTO

−4.25 eV effective contact level

−7.10 eV modelling level

TiO₂

CBM ≈ −4.20 eV

modelling level ≈ −7.20 eV

NDI

LUMO ≈ −3.70 eV

HOMO ≈ −6.90 eV

Perovskite

CBM = −3.60 eV

VBM = −5.45 eV

Spiro-OMeTAD

modelling conduction level

HOMO = −5.20 eV

Ag

contact level ≈ −5.10 eV

contact level ≈ −5.10 eV

For a specific experimental device, measured UPS/Kelvin-probe/contact values should replace modelling assumptions.

Optical model

The photon simulation uses a compact offline approximation:

Wavelength grid: approximately 420–800 nm.

Compact AM1.5G photon-weight table.

Compact perovskite absorption-coefficient table.

Beer–Lambert absorption depth:

x = -ln(U) / α(λ)

Shorter-wavelength photons are therefore preferentially absorbed closer to the illuminated surface, while longer-wavelength photons penetrate more deeply.

The optical tables are deliberately compressed for an offline interactive demonstration and are not substitutes for ASTM G173 or measured absorption data.

Carrier and recombination assumptions

Temperature: 300 K.

kT ≈ 25.85 meV.

Perovskite electron mobility: 2 cm² V⁻¹ s⁻¹.

Perovskite hole mobility: 2 cm² V⁻¹ s⁻¹.

NDI electron mobility: 10⁻³ cm² V⁻¹ s⁻¹.

TiO₂ electron mobility: 0.5 cm² V⁻¹ s⁻¹ (modelling assumption).

Spiro-OMeTAD hole mobility: 2×10⁻⁴ cm² V⁻¹ s⁻¹ (modelling assumption).

Einstein relation: D = μkT/q.

Exciton binding energy: 15 meV.

Bulk SRH lifetime: 100 ns clean / 5 ns defective.

Radiative coefficient: 10⁻¹⁰ cm³ s⁻¹.

The animation represents trapping and recombination visually; it is not a full self-consistent transient SRH/radiative TCAD calculation.

NDI behaviour

The NDI layer is treated as an interfacial electron-selective layer. Its supplied LUMO of approximately −3.70 eV is shown as a ~0.10 eV downward step relative to the perovskite CBM at −3.60 eV.

The WKB diagnostic is:

T = exp[-2 d sqrt(2 m_eff phi) / hbar]

Current modelling assumptions:

Tunnel barrier phi = 0.10 eV.

Effective tunnelling mass m_eff = 0.01 m_e.

NDI relative permittivity εr = 3.5.

The WKB term is used as an interface-coupling diagnostic rather than as the sole quantitative current-limiting mechanism.

Live controls

The interface provides:

Play/pause.

30-second timeline scrubber.

Bulk defect-trap toggle.

NDI interlayer toggle.

NDI thickness: 1–20 nm in 0.5 nm steps.

Trap density slider.

Perovskite thickness: 350–700 nm.

Illumination: 0.1–1 sun.

The right-hand parameter-response panel displays the live values and changes in:

Jsc, Voc, FF, and PCE

relative to the default reference state.

Device-output model

The displayed photovoltaic metrics are calculated from an analytical compact model. In particular:

PCE(%) = Voc(V) × Jsc(mA cm⁻²) × FF

for an assumed incident power density of 100 mW cm⁻².

The model includes phenomenological penalties for defects, interface recombination, NDI transport, and thickness-dependent throughput. The parameters are calibration/modelling assumptions and should not be interpreted as measurements of a particular fabricated cell.

Important simplifications

This is a 1-D planar teaching model. It does not explicitly solve all physics of a real perovskite device. In particular, it does not include:

3-D microstructure or grain morphology.

Explicit grain-boundary electrostatics.

Ion migration.

Hysteresis.

Thermal drift or self-heating.

Full optical interference/transfer-matrix optics.

Detailed contact injection/tunnelling at every electrode.

A self-consistent Poisson solution at every rendered video frame.

A full transient drift–diffusion/Poisson solution for every visible particle.

Visible carriers are representative particles linked to the intended transport sequence, not a one-to-one representation of the enormous physical carrier population in a real solar cell.

Running the file

The simulation is designed to run locally:

Keep index.html and this README in the same folder.

Open index.html in a modern browser such as Chrome, Edge, Firefox, or Safari.

No internet connection is required.

For presentation use, maximise the browser window or use browser full-screen mode.

Source and assumption provenance

The physical inputs in the original HTML are separated into:

Values supplied directly in the design specification.

Explicit modelling assumptions/judgement calls.

Compact offline approximation tables.

These assumptions are also documented in the top README comment embedded inside index.html.

Intended use

Suitable for:

PhD or MSc presentations.

Teaching charge generation and selective transport.

Visualising ETL/HTL energy alignment.

Explaining the role of a thin NDI interlayer.

Demonstrating parameter sensitivity qualitatively.

Not suitable for:

Extracting experimentally validated device parameters.

Replacing SCAPS-1D, drift–diffusion TCAD, or measured J–V data.

Claiming quantitative agreement with a particular fabricated device without recalibration and experimental validation.
