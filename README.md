[![Build Status](https://github.com/JuliaGeo/AbstractDatasets.jl/workflows/CI/badge.svg)](https://github.com/JuliaGeo/AbstractDatasets.jl/actions)
[![documentation dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliageo.github.io/AbstractDatasets.jl/dev/)


This package contains abstracts type definition to ensure compatibility of the package [GRIBDatasets](https://github.com/JuliaGeo/GRIBDatasets.jl) and [NCDatasets](https://github.com/Alexander-Barth/NCDatasets.jl) for manipulating GRIB and NetCDF files. This package aims to follow the [Common Data Model](https://docs.unidata.ucar.edu/netcdf-c/current/netcdf_data_model.html) and the [CF (climate and forecast models) Metadata Conventions](https://cfconventions.org/).

This package is at a very early state of developpement.


Here is minimal example for loading GRIB or NetCDF files.

``` julia
import SomeDatasets # where SomeDatasets is either GRIBDatasets or NCDatasets

ds = SomeDatasets.Dataset("file_name")

# ntime is the number of time instances
ntime = ds.dim["time"]

# create an array-like structure v corresponding to variable temperature
v = ds["temperature"]

# load a subset
subdata = v[10:30,30:5:end]

# load all data
data = v[:,:]

# load a global attribute
title = ds.attrib["title"]
close(ds)
```

Most users would typically import `GRIBDatasets` and `NCDatasets` directly and not `AbstractDatasets`. One should import `AbstractDatasets` only to extent the functionality of `GRIBDatasets` and `NCDatasets`.



