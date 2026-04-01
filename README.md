Niki Gruber's classic box model for BATS and BERM from 1996--2002.

REQUIREMENTS: Linux/Mac OS with `gfortran` compiler and an installation of `NCL` for graphics output (I used `Conda` for this in a new environment, and it works well).

USAGE: head over to `bin_ia` directory, and run `./recompile_model` to get started. Assuming no errors, run `./diag_boxmodel_ia.x` and follow the onscreen instructions:

```
--------------------------------------------------

              DIAGNOSTIC BOX MODEL
       OF THE CARBON CYCLE IN THE SARGASSO SEA

            INTERANNUAL VARIABILITY VERSION 

         this program is based on a study 
                 done at station S 

                Version 1.0   15.8.96 
                Version 3.3   10.6.97 
                Version 4.0   15.10.99 
                        4.1   06.06.00 
                        4.2   29.08.01 

               written by Nicolas Gruber 
       IGPP & Dept. of Atmospheric Sciences 
           UCLA, Los Angeles, CA 90095 
              e-mail: ngruber@igpp.ucla.edu 

--------------------------------------------------


 --INIT_PARAMS: initializing parameters...

 Please give name of experiment 
    (is used also for naming the output files) (max length = 10) : jmltest

 Please add notes to this experiment (max length = 30) : test

 Please specify simulation mode : 
      <st> : standard simulation (DEFAULT) 
      <mc> : Monte Carlo simulations 
      <op> : parameter optimization 
      <sn> : evaluation of parameter sensitivities
 please type character*2 : st

 Please specify solution scheme : 
      <std> : original standard, solve for dC/dt 
      <adv> : solve for u velocity 
      <phy> : solve for Kz +  u 
      <kz>  : solve for Kz 
 please type character*2 : std

 Please specify the choice of parameters : 
    <d> : default parameters (DEFAULT) 
    <i> : interactive choice of parameters 
 please type character*1 : d


 Parameters for plotting

 do you like plot output (type <y> or <n>) : y
```

To visualize the results, look for the `gmeta` file, and run `ctrans -d x11 gmeta` for an on-screen preview, or `ctrans -d ps.color gmeta > plots.ps` for a file.

Let me know if you have questions!

TIPS:

For my Intel Mac, I got a working install of `ncl` using conda (thanks to the install hints at [https://github.com/suvarchal/IPyNCL](https://github.com/suvarchal/IPyNCL/tree/ecdd7778dc00aff307f28e73c87a7e8b3bc7ddfd)):
```
>>conda create -n ncl -c conda-forge -c ncar ncl=6.6.2 gsl python=3.6 jupyter
```
and then edited `/usr/local/anaconda3/envs/ncl/bin/ncargf90` to point to my installation of `gfortran`:
```
>> conda activate ncl
>> grep -i gfortran /usr/local/anaconda3/envs/ncl/bin/ncargf90                                                                      (ncl) 
set fortran  = ""/Users/runner/miniforge3/conda-bld/ncl_1672316636637/_build_env/bin/x86_64-apple-darwin13.4.0-gfortran""
        echo "Smooth "/Users/runner/miniforge3/conda-bld/ncl_1672316636637/_build_env/bin/x86_64-apple-darwin13.4.0-gfortran" of NCAR Graphics"
        echo "Super "/Users/runner/miniforge3/conda-bld/ncl_1672316636637/_build_env/bin/x86_64-apple-darwin13.4.0-gfortran" of NCAR Graphics"
        echo "Quick "/Users/runner/miniforge3/conda-bld/ncl_1672316636637/_build_env/bin/x86_64-apple-darwin13.4.0-gfortran" of NCAR Graphics"
```
to
```
>> conda activate ncl
>> grep -i gfortran /usr/local/anaconda3/envs/ncl/bin/ncargf90                                                  (ncl) 
set fortran  = ""/usr/local/bin/gfortran""
        echo "Smooth "/usr/local/bin/gfortran" of NCAR Graphics"
        echo "Super "/usr/local/bin/gfortran" of NCAR Graphics"
        echo "Quick "/usr/local/bin/gfortran" of NCAR Graphics"
```
The model compiles and works :)
