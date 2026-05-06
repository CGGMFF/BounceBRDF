# BounceBRDF: High-Gloss SVBRDF Capture Using Bounce Light

[![Eurographics 2026](https://img.shields.io/badge/Eurographics-2026-c5a76c)](https://eg2026.eu/)
[![Computer Graphics Forum](https://img.shields.io/badge/CGF-Vol%2045%2C%20No%202-1f6feb)](https://onlinelibrary.wiley.com/journal/14678659)
[![Project Page](https://img.shields.io/badge/Project-Page-2ea44f)](https://reality.tf.fau.de/publications/2026/iser2026highgloss/iser2026highgloss.html)
[![Code](https://img.shields.io/badge/code-coming%20by%20end%20of%20May%202026-orange)](#-code-release-status)

**[Tomáš Iser](https://tomasiser.com)<sup>1,2</sup> &nbsp;·&nbsp; [Andrei-Timotei Ardelean](https://reality.tf.fau.de/staff/t.ardelean.html)<sup>1</sup> &nbsp;·&nbsp; [Tim Weyrich](https://reality.tf.fau.de/weyrich.html)<sup>1</sup>**

<sup>1</sup>Friedrich-Alexander-Universität Erlangen-Nürnberg (FAU) &nbsp;·&nbsp; <sup>2</sup>Charles University, Faculty of Mathematics and Physics

*Computer Graphics Forum (Proc. Eurographics)*, Vol. 45, No. 2, 2026.

📄 **[Project page & paper](https://reality.tf.fau.de/publications/2026/iser2026highgloss/iser2026highgloss.html)** &nbsp;·&nbsp; 📚 **[BibTeX](https://reality.tf.fau.de/publications/2026/iser2026highgloss/iser2026highgloss.bib)**

---

<img src="https://reality.tf.fau.de/publications/2026/iser2026highgloss/iser2026highgloss-400x300@2x.jpg" width="400px">

## 🚧 Code Release Status

> **The source code is not in this repository yet.** We are releasing it by **the end of May 2026**, shortly after the Eurographics presentation. 🎉
>
> If you'd like to be notified the moment the code lands, please **click "Watch" → "Custom" → "Releases"** at the top of this repository. Stars are also very appreciated and help us gauge interest! ⭐

In the meantime, the paper and supplementary material are available from the [project page](https://reality.tf.fau.de/publications/2026/iser2026highgloss/iser2026highgloss.html). For questions, please open a GitHub issue or contact the authors directly.

## Method at a Glance

We acquire a spatially-varying Disney Principled BRDF (base color, roughness, metallicness, and normal map) from a small set of photographs lit by handheld **indirect bounce light**. A mirror sphere placed next to the sample lets us recover each photo's environment map. A lightweight per-pixel MLP is then trained **on the fly** &mdash; without any pre-collected material dataset &mdash; to invert the rendering equation against those measured environments, with Mitsuba 3 generating the synthetic supervision.

Key properties:

- **No material dataset required.** The MLP is trained on synthetic data and the captured environments.
- **Robust to glossy materials.** Indirect illumination keeps the dynamic range manageable and gives contiguous hemispherical coverage, avoiding the highlight clipping and angular under-sampling that hurt point-light methods.
- **Scales to high resolutions.** Inference is per-pixel, so cost is linear in pixel count: a 2048×2048 SVBRDF is produced in under a second on consumer hardware after a few minutes of training.
- **Casual capture.** A camera, a handheld light, and a mirror ball; typically 9 photographs suffice.

## Citation

If our work is useful to your research, please cite:

```bibtex
@article{iser2026highgloss,
  author    = {Iser, Tom\'{a}\v{s} and Ardelean, Andrei-Timotei and Weyrich, Tim},
  title     = {High-Gloss {SVBRDF} Capture Using Bounce Light},
  journal   = {Computer Graphics Forum (Proc. Eurographics)},
  volume    = {45},
  number    = {2},
  year      = {2026},
  month     = may,
  publisher = {Eurographics Association},
  authorurl = {https://reality.tf.fau.de/pub/iser2026highgloss.html},
}
```

## Acknowledgments

This project has received funding from the European Union's Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 956585. This work was further supported by the Charles University grant SVV-260822.

## License

The source code will be released under an open-source license &mdash; details to be confirmed at the time of code release.
