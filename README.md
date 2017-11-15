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

## II. Adding the meta-baylibre-agl-eas layer to your AGL build

1. Download meta-baylibre-agl-eas at `$AGL_TOP`
2. Add `eas` to the feature of your AGL build<br>
```shell
source meta-agl/scripts/aglsetup.sh -m $MACHINE -b <your-other-features> eas
```

With this `meta-baylibre-agl-eas` will be added to your `conf/bblayers.conf`.

## III. Background information:

Several techniques for saving energy through various scheduler
modifications have been proposed in the past, however most of the
techniques have not been universally beneficial for all use-cases and
platforms. For example, consolidating tasks on fewer cpus is an
effective way to save energy on some platforms, while it might make
things worse on others.

This proposal, which is inspired by the Ksummit workshop discussions in
2013 [1], takes a different approach by using a (relatively) simple
platform energy cost model to guide scheduling decisions. By providing
the model with platform specific costing data the model can provide a
estimate of the energy implications of scheduling decisions. So instead
of blindly applying scheduling techniques that may or may not work for
the current use-case, the scheduler can make informed energy-aware
decisions. We believe this approach provides a methodology that can be
adapted to any platform, including heterogeneous systems such as ARM
big.LITTLE. The model considers cpus only, i.e. no peripherals, GPU or
memory. Model data includes power consumption at each P-state and
C-state.

## IV. Further reading:

https://developer.arm.com/open-source/energy-aware-scheduling
