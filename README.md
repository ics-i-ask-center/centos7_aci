# centos7_aci
Centos 7 base image for ACI Singualarity recipe  
This recipe may include unnecessary packages for certain software installation. Size of the container is ~2.5 GB

More packages will be added in the future

2019/2/17
**Centos 7** with **GCC  8.2.1**  
To enable GCC 8.2.1,  
```
> source /opt/rh/devtoolset-8/enable
```

2019/3/1  
OpenMPI is added to `$PATH`

2019/3/11  
OpenMPI is updated to version 2.1.6  

2019/4/12  
Boost 1.70.0 in added
