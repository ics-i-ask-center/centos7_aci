# centos7_aci
Centos 7 base image for ACI Singualarity recipe  
This recipe may include unnecessary packages for certain software installation.  
Size of CPU-only container: ~1 GB  
Size of GPU container: ~2.6 GB

More packages will be added in the future

2019/2/17
**Centos 7** with **GCC 8**  
To enable GCC 8,  
```
> source /opt/rh/devtoolset-8/enable
```

2019/3/1  
OpenMPI is added to `$PATH`

2019/3/11  
OpenMPI is updated to version 2.1.6  

2019/4/12  
Boost 1.70.0 in added

2019/7/19  
~~Python 2 and 3 are updated to version 2.7.16 and version 3.7.4~~  
OpenMPI is updated to version 4.0.1

2019/7/21  
~~Few Python packages are added~~

2019/7/22  
~~Few corrections are made including Python~~

2019/7/23  
Pythons are replaced with packages  
To enable Python 2.7.16,  
```
> source /opt/rh/python27/enable
```  
System version of python is 3.6.8

2019/7/30  
devtoolset-7 GCC is added (some software can't be built with GCC 8)

2019/11/9  
CMake 3.15.5 is added

2019/11/22  
OpenMPI is downgraded to 1.10.1 to match version on ACI

2020/2/12  
Boost is upgraded to 1.72.0 and CMake is upgraded to 3.16.4

2020/3/2  
GPU version is added

2020/9/21  
Minor updates are made (regarding libxkb)

2020/9/28  
Recipe for CUDA 9.1 is added (for FSL with CUDA)

2020/10/11  
Boost is upgraded to 1.74.0 and CMake is upgraded to 3.18.4  
R 4.0.3 is added (Curl 7.72.0 and XZ 5.2.5 are added for R)  
VirtualGL is downgraded to 2.5.2 to match system version
