vis_template
============
My templates and scripts for diag/diaggui measurements at KAGRA

This repository contains

* Generic diaggui templates for KAGRA VIS measurements including

  * Transfer functions

    * ``IP_DOF_EXC.xml``: Template for measuring ``IP_TEST_[LTY]_EXC`` to ``IP_BLEND_LVDT[LTY]``.
    * ``STAGE_GAS_EXC.xml``: Template for measuing ``[F0-9;SF;BF]_TEST_GAS_EXC`` to ``[F0-9;SF;BF]_DAMP_GAS_IN1``.
    * ``IM_DOF_EXC.xml``: Template for measuring from ``IM_TEST_[LTVRPY]_EXC`` to ``IM_DAMP_[LTVRPY]_IN1`` and ``IM_OLDAMP_[LPY]_IN1``.
    * ``TM_DOF_EXC.xml``: Template for measuring from ``TM_TEST_[LPY]_EXC`` to ``TM_OLDAMP_[LPY]_IN1``.
..
  * Using Gaussing excition for now, fixed bandwidth, fixed frequency range, but with configurable excitation amplitude.
  * Inverted Pendulum (``TEST_[LTY]_EXC`` to ``IP_BLEND_LVDT[LTY]_IN1``)
  * GAS Filters (``TEST_[GAS]_EXC`` to ``F[0-3]_DAMP_GAS_IN1``, ``SF_DAMP_GAS_IN1``, and ``BF_DAMP_GAS_IN1``)
  * Bottom Filter (``TEST_[LTVRPY]_EXC`` to ``BF_DAMP_[LTVRPY]_IN1``)
  * Marionette (``TEST_[LTVRPY]_EXC`` to ``MN_DAMP_[LTVRPY]_IN1`` and ``MN_OLDAMP_[LTVRPY]_IN1``)
  * IM (``TEST_[LTVRPY]_EXC`` to I``M_DAMP_[LTVRPY]_IN1`` and ``IP_OLDAMP_[LPY]_IN1``)
  * TM (``TEST_[LPY]_EXC`` to ``TM_OLDAMP_[LPY]_IN1``)

* Scripts that convert the diaggui templates for specific optics.

  * ``make_typeb``: convert templates for Type-B suspensions

    * example usage: Make transfer functions template

    .. code-block:: bash

       ./make_typeb --outdir SR3 --optics SR3 --transfer-function --config ./typeb_config

    Equivalently

    .. code-block:: bash

       ./make_typeb -o SR3 -O SR3 -tf -c ./typeb_config

* Configuration files for converting the templates

  * ``typeb_config``

    * Excitation amplitude for different stages and degree of freedoms.

After generating the measurement files, it's strongly recommended to use
`vishack <https://github.com/gw-vis/vishack>`_ for automating measurements.

* Help message

  .. code-block:: bash
      $ ./make_typeb -h
      usage make_typeb -o outdir -O optics -c config [-h] [--args ARGS]

      Make diaggui measurement files from template for Type-B suspensions

      arguments
         --out-dir, -o 		 Output directory, e.g. BS 
         --optics, -O 		 The optics, choose from BS, SR2, SR3, SRM.
         --config, -c 		 The configuration file.
         --transfer-function, -tf 		 make transfer function template.
         --diagonalization, -d 		 make diagonalization template.
         --all, -a 		 make all available templates

      optional arguments:
         --template-dir, -t 		 Template directory. Defaults to current directory.
         --help, -h 		 Print this help message.
