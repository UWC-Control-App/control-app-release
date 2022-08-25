# PID-controller application for UWC platform (binary only)
To deploy PID-Controller application,
1.  Clone all UWC repositories using repo as described in step #2 in the [UWC-installation-guide](https://open-edge-insights.github.io/uwc-docs/Pages/page_04.html#how-to-install-universal-wellpad-controller-with-open-edge-insights-for-industrial-installer).
2.  Clone PID-Controller application source code into the <parent directory>/IEdgeInsights/uwc folder.
```
cd <parent directory>/IEdgeInsights/uwc
git clone https://github.com/UWC-Control-App/control-app pid
```

3.  Apply patch for build scripts and modbus container.
```
git apply pid/deploy/controlApp.patch
```

4. Copy UWC recepie file for PID-controller app.
```
 cp <parent directory>/IEdgeInsights/uwc/pid/deploy/uwc-pipeline-with-sparkplug-bridge-and-pid-controller-app.yml <parent directory>/IEdgeInsights/uwc/uwc_recipes/
```
  
5.  Copy sample configuration file for PID-controller application to the directory containing rest of the UWC configuration files.
```
cp <parent directory>/IEdgeInsights/uwc/pid/deploy/PID-controller-config.yml <parent directory>/IEdgeInsights/uwc/Others/Config/UWC/Device_Config/
```

6.  Perform steps #3-8 as described in [UWC-installation-guide](https://open-edge-insights.github.io/uwc-docs/Pages/page_04.html#how-to-install-universal-wellpad-controller-with-open-edge-insights-for-industrial-installer). Selecting Dev Mode in step #8 is ideal when SSL/TLS certificates are not to be used. 

7.  Proceed with step #9, you shall see an option 11 in the prompt as below. Type 11 and continue.
```
11) All modules with PID-Controller Application, SPARKPLUG-BRIDGE, Sample SamplePublisher and Sample SampleSubscriber
```
8.  For step #10, select “Yes”, i.e., pull images from docker container registry. 

9.  Perform step #11 with appropriate inputs depending on your use case. 

10. Once the build is complete, verify modify the `/opt/intel/eii/uwc_data/PID-controller-config.yml` to configure desired number of loops and their respective poll and write datapoints. Alternatively, Use the Configuration-utility application and make sure to list newly created device group file name in `Devices_group_list.yml` file.  
