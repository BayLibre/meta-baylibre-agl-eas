# EAS patches for linux-reneas layer

This README file contains information on the contents of the
meta-baylibre-agl-eas layer.

Please see the corresponding sections below for details.

### Dependencies
-------------------------

This layer depends on:

  * URI: https://gerrit.automotivelinux.org/gerrit/AGL/meta-renesas-rcar-gen3<br>
  layers: `meta-rcar-gen3`<br>
  tag: `master`

### Patches
-----------

Please submit any patches against the meta-baylibre-agl-eas layer to the
the maintainers:

* Michael Turquette <mturquette@baylibre.com>
* Frode Isaksen <fisaksen@baylibre.com>
* Jerome Brunet <jbrunet@baylibre.com>

## I. Description and provided packages:

The layer provides Energy Aware Scheduling (EAS) patches for the linux-reneases kernel. 
This package is an experimental utility to improve scheduling efficiency on big/LITTLE architecture.

+ Patched packages :
	- linux-renesas: Add configuration flags and patches required for EAS.

## II. Adding the meta-baylibre-agl-easlayer to your AGL build

1. Download meta-baylibre-agl-eas at `$AGL_TOP`
2. Add `eas` to the feature of your AGL build<br>
```shell
source meta-agl/scripts/aglsetup.sh -m $MACHINE -b <your-other-features> blsched
```

With this `meta-baylibre-agl-eas` will be added to your `conf/bblayers.conf`.
