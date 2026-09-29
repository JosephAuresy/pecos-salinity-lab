# Pecos Basin Salinity Transport — Stakeholder Lab

Interactive teaching / stakeholder-engagement tool built for a Midland conference on treated produced-water return and beneficial use in the Pecos Basin near Red Bluff Reservoir, Texas.

**Live demo:** https://josephauresy.github.io/pecos-salinity-lab/
*(enable GitHub Pages: Settings → Pages → Deploy from branch `main` / root)*

## What it does

Salinity (TDS) is simulated as a conservative tracer moving with groundwater, using an explicit-Euler / upwind finite-difference scheme conceptually aligned with SWAT+ and MODFLOW 6 gwflow physics. Users can:

- Adjust source strength, treatment level (raw / desalinated / polished produced water), river flow, dilution, aquifer conductivity, specific yield, recharge, and streambed conductivity
- Switch the 2-D plan-view grid resolution live (Δx = 500 m / 100 m / 50 m) and watch the salt front sharpen or smear with numerical dispersion
- Add or remove pumping wells, or load a **pump-and-treat** scenario that deploys a hydraulic-containment well barrier across the salt plume, upstream of the river
- Explore two cross-sections side by side (⊥ layout): a longitudinal field→river vadose/saturated profile, and a transversal river-channel cut showing bank infiltration
- Compare preset scenarios (pristine baseline, high TDS loading, drought year, pump-and-treat) against EPA/agricultural/livestock TDS thresholds
- Read a contextual help panel that explains, in plain language, what every slider and button controls and why it matters hydrogeologically

The lab intentionally frames results around **treated produced-water return, beneficial use, and where it is demonstrably safe** — not fracking language.

## Scope note

This version simulates **TDS/salinity only**. An earlier combined PFAS+salinity version exists separately; PFAS content in this file is retained only as educational/comparison text (Chemicals and Theory tabs) explaining what a fully coupled PFAS transport model would require — it is not part of the interactive simulation.

**This is an idealized teaching tool, not the calibrated basin model.** Parameters here are illustrative, chosen for a clear teaching narrative — not fit to observed data.

## Related tools (Pecos modeling suite)

- **[Pecos Reservoir Management & Reuse Lab](https://josephauresy.github.io/pecos-reservoirs/)** — real observed flow/storage/release data (2000–2020, Red Bluff extended to 1937–2026) for the 5 major Pecos dams, plus the **[Red Bluff Reservoir Modeling Hub](https://josephauresy.github.io/pecos-reservoirs/red-bluff-reservoir-hub.html)** (data-readiness for a Delft3D-FM model of Red Bluff specifically).
- **[Pecos Model Ledger](https://josephauresy.github.io/pre_calibration_pecos/)** — the actual SWAT+/gwflow model's calibration status: flow bias diagnostics, bug tracker, and (in its Salinity section) the real 26-year salt-transport run this teaching lab is conceptually modeled after, with its own observed-vs-simulated comparison and honestly-stated uncertainties.

## Running locally

No build step. Serve the folder with any static file server, e.g.:

```
python -m http.server 8732
```

then open `http://localhost:8732/`.

## Structure

- `index.html` — the entire application (HTML/CSS/JS, single file, no external dependencies except Leaflet for the real-map tab)
