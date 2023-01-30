# MpoxUK

The `MpoxUK` module provides a simulation and inference framework for Mpox transmission in the United Kingdom among gay and bisexual men who have sex with men (GBMSM) and the wider community. Full details are available in _The role of vaccination and public awareness in forecasts of Mpox incidence in the United Kingdom_ (under revision).

### Preprint versions

This modelling framework has evolved during 2022 and early 2023. Earlier versions can be found [here](https://github.com/SamuelBrand1/MonkeypoxUK), and are described in two preprints:

* A first preprint describing the underlying reasoning and methodology is now available [_The role of vaccination and public awareness in medium-term forecasts of monkeypox incidence in the United Kingdom_](https://www.medrxiv.org/content/10.1101/2022.08.15.22278788v1).

* A second preprint using data directly from the UKHSA, rather than open source data from Global.Health, and with an updated set of counter-factual scenarios is now available [_The role of vaccination and public awareness in forecasts of monkeypox incidence in the United Kingdom_](https://www.researchsquare.com/article/rs-2162921/v1).

### Quick start for inference

1. Download [Julia](https://julialang.org/downloads/).
2. Clone this repository.
3. Start the Julia REPL.
4. Change working directory to where this repo is cloned.
5. Enter `Pkg` mode by pressing `]`
6. Activate the environment for `MpoxUK` and download the underlying dependencies.
    > pkg> activate . \
    > pkg> instantiate
7. The script `mpx_inference.jl` covers running the inference methodology. The script loads the underlying case data into a two column matrix `mpxv_wkly` where rows are weeks and first column is reported MSM cases and second column is reported non-MSM cases. The Monday date for each week is given as a `Vector{Date}` array `wks`.

### Other scripts

* `mpx_model_checking.jl`. A post-processing script for creating PIT histograms of model outputs compared to actual data for model checking.
* `mpx_projections.jl`. This script generates projections and creates the main plots from the manuscript.
* `posterior_plots.jl`. This scripts creates standard plots of the posterior (ABC accepted) MCMC chains.
* `sequential_predictions.jl`. This script creates forecasts using parameter and model state fits based on a sequence of redacted data and scores these retrospective forecasts against actual data. Requires inference runs to have already been performed.
* `setup_model.jl`. Sets up the demography, contact rates and other epidemiological distributions. Is included in most other scripts. This script also outputs plots of relevant epidemiological distributions that are shown in the main maunscript.