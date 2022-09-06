# tmf-ids-doc - Ran Slicing Usecase

# IDS Documentation
Documentation for Ran Slicing - IDS TMF catalyst program

### Code / Configuration Repositories

https://github.com/ashokkumarta/ids-trusted-connector

```
Forked from industrial-data-space/trusted-connector
Minor changes - to get the fresh build from the source docker image creation work properly
Build scripts available only for Linux
Run the script b.sh in the base directory to complete the build, create docker image and push it to dockerhub
```

https://github.com/ashokkumarta/ids-dataapps-ran-slice
```
Source code of the generic dataapp used in the configurations.
To build the docker image from the code
Build code:
mvn clean package

Copy the target jar file to stable folder

Start docker:
systemctl start docker

Build image:
sudo docker container prune
sudo docker image rm ashokkumarta/dataapps-ran-slice:latest
sudo docker build -t ashokkumarta/dataapps-ran-slice:latest .
sudo docker push ashokkumarta/dataapps-ran-slice:latest

```

https://github.com/ashokkumarta/ran-slice-tmf-ids-app-config/tree/main/dataapps

```
Contains multiple configurations of the sample dataapp. Includes configurations for
 1. csp-resource-management
 2. csp-load-optimizer
 3. csp-ran-slice-allocation
 4. subscriber-1-demand-forecast
 5. subscriber-2-demand-forecast
 6. subscriber-allocation-confirmation
 7. subscriber-optimizer-feedback
 
```

Script to build all the apps

```

cd csp-resource-management
sudo docker image rm ashokkumarta/orange-csp-resource-management:latest
sudo docker build -t ashokkumarta/orange-csp-resource-management:latest .
sudo docker push ashokkumarta/orange-csp-resource-management:latest
cd ../csp-load-optimizer
sudo docker image rm ashokkumarta/orange-csp-load-optimizer:latest
sudo docker build -t ashokkumarta/orange-csp-load-optimizer:latest .
sudo docker push ashokkumarta/orange-csp-load-optimizer:latest
cd ../csp-ran-slice-allocation
sudo docker image rm ashokkumarta/orange-csp-ran-slice-allocation:latest
sudo docker build -t ashokkumarta/orange-csp-ran-slice-allocation:latest .
sudo docker push ashokkumarta/orange-csp-ran-slice-allocation:latest
cd ../subscriber-1-demand-forecast
sudo docker image rm ashokkumarta/hospital-sub1-demand-forecast:latest
sudo docker build -t ashokkumarta/hospital-sub1-demand-forecast:latest .
sudo docker push ashokkumarta/hospital-sub1-demand-forecast:latest
cd ../subscriber-optimizer-feedback
sudo docker image rm ashokkumarta/subscriber-optimizer-feedback:latest
sudo docker build -t ashokkumarta/subscriber-optimizer-feedback:latest .
sudo docker push ashokkumarta/subscriber-optimizer-feedback:latest
cd ../subscriber-allocation-confirmation
sudo docker image rm ashokkumarta/subscriber-allocation-confirmation:latest
sudo docker build -t ashokkumarta/subscriber-allocation-confirmation:latest .
sudo docker push ashokkumarta/subscriber-allocation-confirmation:latest
cd ../subscriber-2-demand-forecast
sudo docker image rm ashokkumarta/airport-sub2-demand-forecast:latest
sudo docker build -t ashokkumarta/airport-sub2-demand-forecast:latest .
sudo docker push ashokkumarta/airport-sub2-demand-forecast:latest
cd ..

```

Ports on which the apps are configured

```
csp-resource-management: 9001
csp-load-optimizer: 9002
csp-ran-slice-allocation : 9003

subscriber-1-demand-forecast : 9101
subscriber-2-demand-forecast : 9201

subscriber-optimizer-feedback : 9102
subscriber-allocation-confirmation :9103

```


https://github.com/ashokkumarta/ran-slice-tmf-ids-deploy/tree/main/connectors/TMF-RAN-SILC-UC

```
IDS connector configurations for deployment
For deployment - this repo is sufficient. No need to work on other repos
Currently has the following configurations

1. csp - Configuration for running CSP Instance.

  To run this, execute the command 
    ./csp.sh
    
2. subscriber-1 - Configuration for running Subscriber-1 Instance.

  To run this, execute the command 
    ./sub1.sh
    
3. subscriber-2 - Configuration for running Subscriber-2 Instance.

  To run this, execute the command 
    ./sub2.sh
    
```

Commands to create ssl keys for the connectors

```


copy ..\etc-locked\consumer-keystore.p12 orange-csp.p12
keytool -selfcert -alias 1 -storetype PKCS12 -keypass password -keystore orange-csp.p12 -storepass password -ext "SAN=DNS:orange-csp"
keytool -export -alias 1 -storetype PKCS12 -storepass password -file orange-csp.cer -keystore orange-csp.p12
keytool -import -noprompt -v -trustcacerts -alias orange-csp -storetype PKCS12 -file orange-csp.cer -keystore truststore.p12 -keypass password -storepass password

copy ..\etc-locked\consumer-keystore.p12 hospital-sub1.p12
keytool -selfcert -alias 1 -storetype PKCS12 -keypass password -keystore hospital-sub1.p12 -storepass password -ext "SAN=DNS:hospital-sub1"
keytool -export -alias 1 -storetype PKCS12 -storepass password -file hospital-sub1.cer -keystore hospital-sub1.p12
keytool -import -noprompt -v -trustcacerts -alias hospital-sub1 -storetype PKCS12 -file hospital-sub1.cer -keystore truststore.p12 -keypass password -storepass password

copy ..\etc-locked\consumer-keystore.p12 airport-sub2.p12
keytool -selfcert -alias 1 -storetype PKCS12 -keypass password -keystore airport-sub2.p12 -storepass password -ext "SAN=DNS:airport-sub2"
keytool -export -alias 1 -storetype PKCS12 -storepass password -file airport-sub2.cer -keystore airport-sub2.p12
keytool -import -noprompt -v -trustcacerts -alias airport-sub2 -storetype PKCS12 -file airport-sub2.cer -keystore truststore.p12 -keypass password -storepass password

```

https://github.com/ashokkumarta/ran-slice-tmf-ids-logs

```
Configuration and files to initialise the logs.io instance

```

https://github.com/ashokkumarta/ran-slice-tmf-ids-bin/tree/main/d-slow

```
Shortcut scripts to start the instances. Following scripts are included in this repo
csp - starts the csp instance 
sub1 - starts the subscriber-1 instance
sub2 - starts the subscriber-2 instance
all - starts all the instances in sequence

logs - starts the logs.io instance

```
