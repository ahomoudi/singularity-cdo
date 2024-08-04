# singularity-cdo

Singularity image for [cdo](https://code.mpimet.mpg.de/projects/cdo) 

## Build 

```
sudo singularity build singularity-cdo.sif singularity-cdo.def
```

> [!NOTE]  
> make is performed in parallel (4 processes). Please  adjust `make -j4` in `singularity-cdo.def` accordingly. 


## Run 

```
foo@bar:~$ singularity shell singularity-cdo.sif 
Singularity> cdo -V
Climate Data Operators version 2.1.1 (https://mpimet.mpg.de/cdo)
System: x86_64-pc-linux-gnu
CXX Compiler: g++ -std=gnu++17 -g -O2 -fopenmp -pthread
CXX version : g++ (Ubuntu 9.4.0-1ubuntu1~20.04.2) 9.4.0
C Compiler: gcc -g -O2 -fopenmp -pthread -pthread
C version : gcc (Ubuntu 9.4.0-1ubuntu1~20.04.2) 9.4.0
F77 Compiler: f77 -g -O2
F77 version : GNU Fortran (Ubuntu 9.4.0-1ubuntu1~20.04.2) 9.4.0
Features: 31GB 12threads c++17 OpenMP45 Fortran pthreads HDF5 NC4/HDF5 OPeNDAP sz proj fftw3 sse2
Libraries: yac/2.6.1 HDF5/1.12.0 proj/6.3.1
CDI data types: SizeType=size_t
CDI file types: srv ext ieg grb1 grb2 nc1 nc2 nc4 nc4c nc5 nczarr 
     CDI library version : 2.1.1
 cgribex library version : 2.0.2
 ecCodes library version : 2.35.0
  NetCDF library version : 4.9.0 of Aug  4 2024 12:42:52 $
    HDF5 library version : 1.12.0
    exse library version : 1.4.2
    FILE library version : 1.9.1
```

## Examples

```
foo@bar:~$ singularity exec Sing_CDO.sif cdo sinfo era5_quv.nc 
   File format : NetCDF2
    -1 : Institut Source   T Steptype Levels Num    Points Num Dtype : Parameter ID
     1 : unknown  unknown  v instant      37   1     24321   1  I16  : -1            
     2 : unknown  unknown  v instant      37   1     24321   1  I16  : -2            
     3 : unknown  unknown  v instant      37   1     24321   1  I16  : -3            
   Grid coordinates :
     1 : lonlat                   : points=24321 (201x121)
                        longitude : 20 to 70 by 0.25 degrees_east
                         latitude : 40 to 10 by -0.25 degrees_north
   Vertical coordinates :
     1 : pressure                 : levels=37
                            level : 1 to 1000 millibars
   Time coordinate :
                             time : 1 step
     RefTime =  1900-01-01 00:00:00  Units = hours  Calendar = gregorian
  YYYY-MM-DD hh:mm:ss  YYYY-MM-DD hh:mm:ss  YYYY-MM-DD hh:mm:ss  YYYY-MM-DD hh:mm:ss
  2014-01-01 00:00:00
cdo    sinfo: Processed 3 variables over 1 timestep [0.05s 25MB]
```


```
# another example
foo@bar:~$ singularity exec Sing_CDO.sif cdo selname,q era5_quv.nc era5_q.nc
cdo    selname: Processed 899877 values from 3 variables over 1 timestep [0.10s 26MB]
```

## Contributing
Bug reports and pull requests are welcome on GitHub at  https://github.com/ahomoudi/singularity-cdo/issues

## License
Licensed under [MIT License](http://opensource.org/licenses/MIT) as open source.