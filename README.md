<h1 align="center">app-bet-t1w</h1>

<p align="center">
  Skull-strips a T1-weighted image with FSL 6.0.4 BET and outputs the brain-extracted T1w volume.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.995"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.995-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-see_LICENSE-lightgrey.svg" alt="License"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Skull-strips a T1-weighted image with FSL 6.0.4 BET and outputs the brain-extracted T1w volume.**

Runs FSL bet on a T1w image with a configurable fractional intensity threshold (-f) and optional robust brain centre estimation (-R) or bias field and neck cleanup (-B), inside the brainlife/fsl:6.0.4 container. Use it for brain extraction before registration or segmentation. Lower frac values give larger brain estimates; enable bias_neck_cleanup for images with a lot of neck.

| | |
|---|---|
| **Inputs** | `neuro/anat/t1w` |
| **Outputs** | `neuro/anat/t1w` |
| **Container** | `brainlife/fsl:6.0.4` |
| **Resources** | 4 GB memory · 1 h walltime |
| **Run it** | [doi.org/10.25663/brainlife.app.995](https://doi.org/10.25663/brainlife.app.995) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `t1` | `neuro/anat/t1w` | yes | T1-weighted NIfTI image to skull-strip. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `t1_brain` | `neuro/anat/t1w` | Skull-stripped T1w brain volume produced by FSL BET |

<details>
<summary><b>Parameters</b> (3)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `frac` | number | `0.5` | BET fractional intensity threshold (0-1) |
| `robust` | boolean | `false` | Use robust brain centre estimation (-R) |
| `bias_neck_cleanup` | boolean | `false` | Bias field + neck cleanup (-B) |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.995](https://doi.org/10.25663/brainlife.app.995), choose `neuro/anat/t1w` from your project, set the parameters and press **Execute**. The results are saved to your project as `neuro/anat/t1w`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/fsl:6.0.4`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "t1": "/path/to/t1/t1",
       "frac": 0.5,
       "robust": false,
       "bias_neck_cleanup": false
   }
   ```

3. Run `./main`.

## Troubleshooting

- **no output produced**: Check the log for the bet error.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- app-bet-t1w. brainlife.io App. [doi:10.25663/brainlife.app.995](https://doi.org/10.25663/brainlife.app.995)
- Jenkinson et al. FSL. *NeuroImage* 62:782-790 (2012). [doi:10.1016/j.neuroimage.2011.09.015](https://doi.org/10.1016/j.neuroimage.2011.09.015)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

- Gabriele Amorosino

#### MIT Copyright (c) 2026 Gabriele Amorosino

## License

See [LICENSE](LICENSE).
