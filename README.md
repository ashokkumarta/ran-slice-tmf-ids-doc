# tmf-ids-doc

# IDS Documentation
Documentation for IDS TMF catalyst program

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
Source code of a sample dataapp used in the configurations 
```

https://github.com/ashokkumarta/tmf-ids-test/tree/main/dataapps

```
Contains multiple configurations of the sample dataapp. Includes configurations for
 1. csp-recommendations-feedback-app
 2. csp-sharing-agent-app
 3. mno1-recommendations-feedback-app
 4. mno1-sharing-agent-app
 5. mno2-recommendations-feedback-app
 6. mno2-sharing-agent-app
 7. recommendations-incentive-processor-app
 8. recommendations-processor-app
 9. regulator-recommendations-app
10. regulator-recommendations-feedback-processor-app
11. regulator-recommendations-incentive-app
12. regulator-usage-data-processor-app

```

https://github.com/ashokkumarta/tmf-ids-test/tree/main/connectors/RAN-SHARE-UC-SLOW

```
IDS connector sample configurations for deployment
For deployment - this repo is sufficient. No need to work on other repos
Currently has the following configurations

1. regulator - Configuration for running RAN Regulator Instance.

  To run this, execute the command 
    docker-compose -f ran-regulator.yaml up

2. csp - Configuration for running CSP Instance.

  To run this, execute the command 
    docker-compose -f csp.yaml up
    
3. mno-1 - Configuration for running MNO-1 Instance.

  To run this, execute the command 
    docker-compose -f mno-1.yaml up
    
4. mno-2 - Configuration for running MNO-2 Instance.

  To run this, execute the command 
    docker-compose -f mno-2.yaml up
    
```

https://github.com/ashokkumarta/tmf-ids-logs
```
Configuration and files to initialise the logs.io instance

```

https://github.com/ashokkumarta/tmf-ids-bin

```
scripts to start the instances. Following scripts are included in this repo
regu - starts the regulator instance
csp - starts the csp instance 
mno1 - starts the mno-1 instance
mno2 - starts the mno-2 instance
all - starts all the instances in sequence
slow - folder containing all the above scripts, to start instances with slow communication speed configuration

logs - starts the logs.io instance

```
