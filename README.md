This repository belongs to the paper

Glerum et al. (in review) Why does Victoria rotate? Continental microplate dynamics in numerical models of the East African Rift System.

and contains the input files (.prm) to the ASPECT code used to compute the model results in the paper.

The input files correspond to the ASPECT branch paper-Victoria-microplate-rotation that can be found at

`https://github.com/anne-glerum/aspect/tree/paper-Victoria-microplate-rotation` 

This branch stems from 2.0.0-pre commit `31a88da` and includes changes to a.o. the files:

```
include/aspect/particle/particle_handler.h
include/aspect/postprocess/point_values.h
include/aspect/simulator_access.h
source/particle/particle_handler.cc
source/particle/world.cc
source/postprocess/point_values.cc
source/simulator/core.cc
source/simulator/simulator_access.cc
```

It also includes custom plugins needed for model setup and postprocessing:

```
include/aspect/geometry_model/initial_topography_model/lithosphere_rift.h
include/aspect/initial_composition/lithosphere_rift.h
include/aspect/initial_temperature/lithosphere_rift.h
include/aspect/material_model/visco_plastic_strain.h
include/aspect/mesh_refinement/lithosphere_rift.h
include/aspect/postprocess/visualization/stress_regime.h
source/geometry_model/initial_topography_model/lithosphere_rift.cc
source/initial_composition/lithosphere_rift.cc
source/initial_temperature/lithosphere_rift.cc
source/material_model/visco_plastic_strain.cc
source/mesh_refinement/lithosphere_rift.cc
source/postprocess/visualization/stress_regime.cc
```

The file `prms/README_prms_to_paper_model_names` contains a table linking
prm file names to the model names in the paper. 

# Documentation

## System requirements and installation

ASPECT was built using the underlying library deal.II 8.5.0 
on the German HLRN cluster Konrad with the following specifications:
```
###
#
#  ASPECT configuration:
#        ASPECT_VERSION:            2.1.0-pre
#        GIT REVISION:              98098ca13 (EARS_generic)
#        DEAL_II_DIR:               /gfs1/work/bbpanneg/software/deal.II.8.5/installed/lib/cmake/deal.II
#        DEAL_II VERSION:           8.5.0
#        ASPECT_USE_PETSC:          OFF
#        ASPECT_USE_FP_EXCEPTIONS:  OFF
#        ASPECT_RUN_ALL_TESTS:      OFF
#        ASPECT_USE_SHARED_LIBS:    ON
#        ASPECT_HAVE_LINK_H:        ON
#        CMAKE_BUILD_TYPE:          Release
#        ASPECT_PRECOMPILE_HEADERS: OFF
#        CMAKE_INSTALL_PREFIX:      /usr/local
#        CMAKE_SOURCE_DIR:          /gfs1/work/bbpanneg/software/aspect/aspect 
#        CMAKE_BINARY_DIR:          /gfs1/work/bbpanneg/software/aspect/build_release
#        CMAKE_CXX_COMPILER:        GNU 6.2.0 on platform Linux x86_64
#                                   /opt/cray/craype/2.5.9/bin/CC
#        PARAMETER_GUI_EXECUTABLE:  PARAMETER_GUI_EXECUTABLE-NOTFOUND
#        CMAKE_C_COMPILER:          /opt/cray/craype/2.5.9/bin/cc
#
#        LINKAGE:                   DYNAMIC
#
#        COMPILE_FLAGS:             -pedantic -fPIC -Wall -Wextra -Wpointer-arith -Wwrite-strings -Wsynth -Wsign-compare -Wswitch -Woverloaded-virtual -Wno-long-long -Wno-placement-new  -Wno-literal-suffix -fopenmp-simd -std=c++14 -Wno-parentheses -Wno-unused-local-typedefs -O2 -funroll-loops -funroll-all-loops -fstrict-aliasing -Wno-unused-local-typedefs
#
###
```

deal.II 8.5.0 was built with the following specifications using candi (https://github.com/dealii/candi):
```
###
#
#  deal.II configuration:
#        CMAKE_BUILD_TYPE:       DebugRelease
#        BUILD_SHARED_LIBS:      ON
#        CMAKE_INSTALL_PREFIX:   /gfs1/work/bbpanneg/software/deal.II.8.5/installed
#        CMAKE_SOURCE_DIR:       /gfs1/work/bbpanneg/software/deal.II.8.5/dealii-8.5.0
#                                (version 8.5.0)
#        CMAKE_BINARY_DIR:       /gfs1/work/bbpanneg/software/deal.II.8.5/build
#        CMAKE_CXX_COMPILER:     GNU 6.2.0 on platform Linux x86_64
#                                /opt/cray/craype/2.5.9/bin/CC
#        CMAKE_C_COMPILER:       /opt/cray/craype/2.5.9/bin/cc
#        CMAKE_Fortran_COMPILER: /opt/cray/craype/2.5.9/bin/ftn
#        CMAKE_GENERATOR:        Unix Makefiles
#
#  Base configuration (prior to feature configuration):
#        DEAL_II_CXX_FLAGS:            -pedantic -fPIC -Wall -Wextra -Wpointer-arith -Wwrite-strings -Wsynth -Wsign-compare -Wswitch -Woverloaded-virtual -Wno-long-long -Wno-placement-new -Wno-deprecated-declarations -Wno-literal-suffix -fopenmp-simd -std=c++14
#        DEAL_II_CXX_FLAGS_RELEASE:    -O2 -funroll-loops -funroll-all-loops -fstrict-aliasing -Wno-unused-local-typedefs
#        DEAL_II_CXX_FLAGS_DEBUG:      -Og -ggdb -Wa,--compress-debug-sections
#        DEAL_II_LINKER_FLAGS:         -Wl,--as-needed -rdynamic -fuse-ld=gold
#        DEAL_II_LINKER_FLAGS_RELEASE: 
#        DEAL_II_LINKER_FLAGS_DEBUG:   -ggdb
#        DEAL_II_DEFINITIONS:          
#        DEAL_II_DEFINITIONS_RELEASE:  
#        DEAL_II_DEFINITIONS_DEBUG:    DEBUG
#        DEAL_II_USER_DEFINITIONS:     
#        DEAL_II_USER_DEFINITIONS_REL: 
#        DEAL_II_USER_DEFINITIONS_DEB: DEBUG
#        DEAL_II_INCLUDE_DIRS          
#        DEAL_II_USER_INCLUDE_DIRS:    
#        DEAL_II_BUNDLED_INCLUDE_DIRS: 
#        DEAL_II_LIBRARIES:            m
#        DEAL_II_LIBRARIES_RELEASE:    
#        DEAL_II_LIBRARIES_DEBUG:      
#
#  Configured Features (DEAL_II_ALLOW_BUNDLED = ON, DEAL_II_ALLOW_AUTODETECTION = ON):
#      ( DEAL_II_WITH_64BIT_INDICES = OFF )
#      ( DEAL_II_WITH_ARPACK = OFF )
#        DEAL_II_WITH_BOOST set up with bundled packages
#            BOOST_CXX_FLAGS = -Wno-unused-local-typedefs
#            BOOST_BUNDLED_INCLUDE_DIRS = /gfs1/work/bbpanneg/software/deal.II.8.5/dealii-8.5.0/bundled/boost-1.62.0/include
#            BOOST_LIBRARIES = rt
#      ( DEAL_II_WITH_BZIP2 = OFF )
#        DEAL_II_WITH_CXX11 = ON
#        DEAL_II_WITH_CXX14 = ON
#      ( DEAL_II_WITH_GSL = OFF )
#        DEAL_II_WITH_HDF5 set up with external dependencies
#            HDF5_DIR = /opt/cray/hdf5-parallel/1.10.0.1/GNU/51
#            HDF5_INCLUDE_DIRS = /opt/cray/hdf5-parallel/1.10.0.1/GNU/51/include
#            HDF5_USER_INCLUDE_DIRS = /opt/cray/hdf5-parallel/1.10.0.1/GNU/51/include
#            HDF5_LIBRARIES = /opt/cray/hdf5-parallel/1.10.0.1/GNU/51/lib/libhdf5_hl.so;/opt/cray/hdf5-parallel/1.10.0.1/GNU/51/lib/libhdf5.so
#      ( DEAL_II_WITH_LAPACK = OFF )
#      ( DEAL_II_WITH_METIS = OFF )
#        DEAL_II_WITH_MPI set up with external dependencies
#        DEAL_II_WITH_MUPARSER set up with bundled packages
#            MUPARSER_BUNDLED_INCLUDE_DIRS = /gfs1/work/bbpanneg/software/deal.II.8.5/dealii-8.5.0/bundled/muparser_v2_2_4//include
#      ( DEAL_II_WITH_NETCDF = OFF )
#      ( DEAL_II_WITH_OPENCASCADE = OFF )
#        DEAL_II_WITH_P4EST set up with external dependencies
#            P4EST_VERSION = 1.1
#            P4EST_DIR = /gfs1/work/bbpanneg/software/p4est-1.1
#            P4EST_INCLUDE_DIRS = /gfs1/work/bbpanneg/software/p4est-1.1/FAST/include
#            P4EST_USER_INCLUDE_DIRS = /gfs1/work/bbpanneg/software/p4est-1.1/FAST/include
#            P4EST_LIBRARIES = optimized;/gfs1/work/bbpanneg/software/p4est-1.1/FAST/lib/libp4est.so;/gfs1/work/bbpanneg/software/p4est-1.1/FAST/lib/libsc.so;debug;/gfs1/work/bbpanneg/software/p4est-1.1/DEBUG/lib/libp4est.so;/gfs1/work/bbpanneg/software/p4est-1.1/DEBUG/lib/libsc.so;general
#      ( DEAL_II_WITH_PETSC = OFF )
#      ( DEAL_II_WITH_SLEPC = OFF )
#        DEAL_II_WITH_THREADS set up with bundled packages
#            THREADS_CXX_FLAGS = -Wno-parentheses
#            THREADS_DEFINITIONS_DEBUG = TBB_USE_DEBUG;TBB_DO_ASSERT=1
#            THREADS_USER_DEFINITIONS_DEBUG = TBB_USE_DEBUG;TBB_DO_ASSERT=1
#            THREADS_BUNDLED_INCLUDE_DIRS = /gfs1/work/bbpanneg/software/deal.II.8.5/dealii-8.5.0/bundled/tbb41_20130401oss/include
#            THREADS_LIBRARIES = dl
#        DEAL_II_WITH_TRILINOS set up with external dependencies
#            TRILINOS_VERSION = 11.12.1
#            TRILINOS_DIR = /opt/cray/trilinos/11.12.1.5/GNU/5.1/x86_64
#            TRILINOS_INCLUDE_DIRS = /opt/cray/trilinos/11.12.1.5/GNU/5.1/x86_64/include;/opt/cray/hdf5-parallel/1.8.14/GNU/51/include
#            TRILINOS_USER_INCLUDE_DIRS = /opt/cray/trilinos/11.12.1.5/GNU/5.1/x86_64/include;/opt/cray/hdf5-parallel/1.8.14/GNU/51/include
#            TRILINOS_LIBRARIES = 
#      ( DEAL_II_WITH_UMFPACK = OFF )
#        DEAL_II_WITH_ZLIB set up with external dependencies
#            ZLIB_VERSION = 1.2.7
#            ZLIB_INCLUDE_DIRS = /usr/include
#            ZLIB_LIBRARIES = /usr/lib64/libz.so
#
#  Component configuration:
#      ( DEAL_II_COMPONENT_DOCUMENTATION = OFF )
#        DEAL_II_COMPONENT_EXAMPLES
#      ( DEAL_II_COMPONENT_PACKAGE = OFF )
#      ( DEAL_II_COMPONENT_PYTHON_BINDINGS = OFF )
#
###
```
The Konrad cluster (Cray) has been dismantled October 2019. 

ASPECT has been installed and run successfully on local machines and supercomputing clusters alike,
on both Linux and MacOS operating systems.

ASPECT installation guidelines can be found in the manual: http://www.math.clemson.edu/~heister/manual.pdf
Virtual machines and Docker containers can also be downloaded from the ASPECT website: https://aspect.geodynamics.org/download.html


Typical install time including the underlying libraries will be several hours. An ASPECT only install
generally takes 30 minutes to an hour. 

## Demo
The folder demo contains an input file demo.prm that is a 2D simplification of the 3D models
used in the paper. It can be run after installing the branch
https://github.com/anne-glerum/aspect/tree/paper-Victoria-microplate-rotation
The input file will create a 2D rift centered around the centre X coordinate. The continental
lithosphere includes a thicker region towards the right boundary. The model should run for
1 My (model time). At the currently-set low resolution, this will take X minutes for 2 MPI processes.
For postprocessing, the stress is outputted at 5 locations around the rift axis. 

Furthermore, the CIG ASPECT repository contains a benchmarks and a cookbook folder with input files that cover
most functionality of ASPECT. Instructions for these models can be found in the manual and the input files themselves.
These folders are included in the aforementioned branch.

4) Instructions for use
The input files (.prm) in this repository can be run with the ASPECT version
https://github.com/anne-glerum/aspect/tree/paper-Victoria-microplate-rotation
only, as they contain custom functionalities for the model setup and postprocessing.
The custom functionalities are documented in the input files. 
