# Galactic Natal kick Estimator

Natal kick distribution of black hole X-ray binaries

(Atri et al. 2019)

## Prerequisites

The scripts in this repository require python 3. The following packages are required for the code to work:

- [Numpy](http://www.numpy.org/) ([Oliphant 2006](https://archive.org/details/NumPyBook/page/n0))
- [Galpy](https://galpy.readthedocs.io/) ([Bovy 2015](https://ui.adsabs.harvard.edu/#abs/2015ApJS..216...29B/abstract))
- [Astropy](http://www.astropy.org/) ([Robitaille et al. 2013](https://ui.adsabs.harvard.edu/?#abs/2013A&A...558A..33A))
- [Matplotlib](https://matplotlib.org/) ([Hunter 2007](https://ieeexplore.ieee.org/document/4160265))
- [Joblib](https://joblib.readthedocs.io/)

## Instructions

The `natalkick.py` script requires no installation and should work out of the box as  a standalone script.

For example:

```ascii
$ python natalkick.py test_system 20.0 0 30.0 0 -10.0 0.32 5.0 0.40 4.4 1.0 -5.6 5.0 --niter 100
[Parallel(n_jobs=12)]: Using backend LokyBackend with 12 concurrent workers.
[Parallel(n_jobs=12)]: Done  48 tasks      | elapsed:    2.2s
[Parallel(n_jobs=12)]: Done  98 out of 100 | elapsed:    3.4s remaining:    0.1s
[Parallel(n_jobs=12)]: Done 100 out of 100 | elapsed:    3.4s finished
System natal kick (km/s): 211.08995665734759 (- 44.75847815299406 /+ 52.40289538416792 )
Reported values are Median +/- 1sigma uncertainties.
The final MC results are saved in natalkick_dist_test_system.csv
The distribution is plotted in natalkick_plot_test_system.png
```

You can access the help doc by:

```ascii
$ python natalkick.py -h
usage: natalkick.py [-h] [--niter NITER] [--njobs NJOBS] [--age AGE]
                    [--npoints NPOINTS]
                    name ra ra_er dec dec_er pm_ra pm_ra_er pm_dec pm_dec_er d
                    d_er v_rad v_rad_er

Script to estimate Natal kick for a system based on location, proper motion,
radial velocity and distance with their uncertainties. This code reports
system's potential natal kick based on MC simulations. The probability
distribution of all input parameters are assumed to be gaussian at the moment.
This code also produces a csv file containing all the realizations from the MC
for the natal kick and a png file containing a histogram of this posterior
distribution. For details of calculations, assumptions and application for
black hole X-ray binaries please refer to Atri et al. 2019. This repository is
maintained by P. Atri and A. Bahramian.

positional arguments:
  name               Output files root
  ra                 System RA (in degrees)
  ra_er              Uncertainty in RA (in degrees)
  dec                System Dec (in degrees)
  dec_er             Uncertainty in Dec
  pm_ra              Proper motion in RA (mas/yr)
  pm_ra_er           Uncertainty in proper motion in RA (mas/yr)
  pm_dec             Proper motion in Dec (mas/yr)
  pm_dec_er          Uncertainty in proper motion in Dec (mas/yr)
  d                  Distance to the system (kpc)
  d_er               Uncertainty in distance (kpc)
  v_rad              Systemic radial velocity (km/s)
  v_rad_er           Uncertainty in systemic radial velocity (km/s)

optional arguments:
  -h, --help         show this help message and exit
  --niter NITER      Number of iterations in the MC simulations (default:
                     5000)
  --njobs NJOBS      Number of threads (parallel) for the simulations
                     (default: number of available kernels on the system)
  --age AGE          Total integration time (in Gyr). Note that Galactic
                     potential is not changing over time. Default 10 Gyr.
  --npoints NPOINTS  Number of orbit points to calculate (Default 10000).
```

If you prefer an executable file, you can make the script so by adding something like `#!/usr/local/bin/python` (path to your python) at the top of the script and then in a terminal run `$ chmod +x natalkick.py`.

## Quick scientific summary, caveats and pitfalls

For details please refer to Atri et al. 2019.
_Need to add background, assumptions, what the outputs mean, where it's not appropriate to use this script_

## Citation and acknowledgements:
This repository is based on Atri et al. 2019 and is maintained by P. Atri and A. Bahramian. If you find this repository useful in your work, please cite Atri et al. 2019. If you have questions/suggestions, feel free to contact us.
