vis_template
============
My templates and scripts for diag/diaggui measurements at KAGRA

This repository contains

* Generic diaggui templates for KAGRA VIS measurements including

  * Transfer functions

    * Using Gaussing excition for now, fixed bandwidth, fixed frequency range, but with configurable excitation amplitude.
    * Inverted Pendulum (``TEST_[LTY]_EXC`` to ``IP_BLEND_LVDT[LTY]_IN1``)
    * GAS Filters (``TEST_[GAS]_EXC`` to ``F[0-3]_DAMP_GAS_IN1``, ``SF_DAMP_GAS_IN1``, and ``BF_DAMP_GAS_IN1``)
    * Bottom Filter (``TEST_[LTVRPY]_EXC`` to ``BF_DAMP_[LTVRPY]_IN1``)
    * Marionette (``TEST_[LTVRPY]_EXC`` to ``MN_DAMP_[LTVRPY]_IN1`` and ``MN_OLDAMP_[LTVRPY]_IN1``)
    * IM (``TEST_[LTVRPY]_EXC`` to I``M_DAMP_[LTVRPY]_IN1`` and ``IP_OLDAMP_[LPY]_IN1``)
    * TM (``TEST_[LPY]_EXC`` to ``TM_OLDAMP_[LPY]_IN1``)

* Scripts that convert the diaggui templates for specific optics.

  * ``make_typeb``: convert templates for Type-B suspensions

    * usage:

    .. code-block:: bash

       ./make_typeb --outdir SR3 --optics SR3 --config ./typeb_config

    Equivalently

    .. code-block:: bash

       ./make_typeb -o SR3 -O SR3 -c ./typeb_config

* Configuration files for converting the templates

  * ``typeb_config``

    * Excitation amplitude for different stages and degree of freedoms.

After generating the measurement files, it's strongly recommended to use
`vishack <https://github.com/gw-vis/vishack>`_ for automating measurements.
