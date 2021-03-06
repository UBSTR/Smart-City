
### CMake Options:

Use the following definitions to customize the building process:   
- **PLATFORM**: Specify the target platform: ```Xeon``` or [```VCAC-A```](vcac-a.md).   
- **FRAMEWORK**: Specify the target framework: ```gst``` or ```ffmpeg``` , Now ```gst``` is enabled.   
- **SCENARIO**: Specify the sample scenario(s): ```traffic```, ```stadium```, or their combination ```traffic,stadium```. As each scenario runs its own set of services and databases, it is recommended that you run multiple scenarios only on a multiple-node deployment setting.     
- **NOFFICES**: Specify the number of offices in the deployment. Support 1-3 offices in the traffic scenario and 1 office in the stadium scenario.       
- **NCAMERAS**: Specify the number of cameras served in each office. Currently support 1-8 cameras. In **traffic scenario**, you just need to specify camera numbers as ```<#camera>```, e.g. ```5``` for traffic survelliance. In **stadium scenario**, you can specify camera numbers as```<#people_counting>,[#crowd_counting],[#queue_counting]```,  e.g. ```5,1,3```, which specifies that there are 5 cameras for people-counting, 1 camera for crowd-counting and 3 cameras for queue-counting. Missing parameters are auto-filled with previous ones. e.g. ```5``` will set 5 cameras for people-counting and auto fill 5 cameras for crowd-counting and queue-counting separately. 
- **NANALYTICS**: Specify the number of analytics instances running in each office. In **traffic scenario**, you just need to specify analytics instances as ```<#instance>```, e.g. ```3``` for traffic survelliance. Similarly, in **stadium scenario**, you can specify different analytics instances with an additional number as ```<#people_counting>,[#crowd_counting],[#queue_counting]```,  e.g. ```5,1,3``` to specify 5 analytics instances for people-counting, 1 analytics instances for crowd-counting and 3 analytics instances for queue-counting. Missing parameters are auto-filled with previous one. e.g. ```5``` will set 5 analytics instances for people-counting and auto fill 5 analytics instances for crowd-counting and queue-counting separately.

### Examples:   

```
cd build
cmake -DPLATFORM=Xeon ..
```

```
cd build
cmake -DNOFFICES=3 -DPLATFORM=Xeon ..
```

```
cd build
cmake -DPLATFORM=Xeon -DSCENARIO=traffic -DNOFFICES=3 -DNCAMERAS=5 -DNANALYTICS=3 FRAMEWORK=gst ..
```

```
cd build
cmake -DPLATFORM=Xeon -DSCENARIO=stadium -DNOFFICES=1 -DNCAMERAS=5,1,3 -DNANALYTICS=5,1,3 FRAMEWORK=gst ..
```

### Make Commands:

- **build**: Build the sample (docker) images.  
- **update**: Distribute the sample images to worker nodes.  
- **dist**: Create the sample distribution package.   
- **start/stop_docker_compose**: Start/stop the sample orchestrated by docker-compose.  
- **start/stop_docker_swarm**: Start/stop the sample orchestrated by docker swarm.   
- **start/stop_kubernetes**: Start/stop the sample orchestrated by Kubernetes.   
- **discover**: Scan the network specified by `PORT_SCAN` for IP cameras, and print out the IP camera profiles.    

### See Also:

- [Sample Distribution](dist.md)   
