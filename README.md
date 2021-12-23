# split-tunneling-linux-namespace-based  

Script to control the Split-Tunneling (per application/process) functionality for Linux.  
The implementation is based on Linux Namespaces  

## Usage:
Note! The script have to be started under privilaged user (sudo ./splittun-ns.sh ...)  
    `./splittun-ns.sh <command> [parameters]`  
Parameters:  
```
    start [-i <interface_name>] [-g <gateway_ip>] [-d <dns>]  
        Initialize split-tunneling functionality  
        - interface_name - (optional) name of network interface to be used for ST environment  
        - gateway_ip     - (optional) gateway IP to be used for ST environment  
        - dns            - (optional) DNS IP to be used for ST environment  
    stop [-i <interface_name>]  
        Uninitialize split-tunneling functionality  
        - interface_name - (optional) name of network interface which was previously used for '-init' command  
    run [-u <username>] <command>  
        Start commands in split-tunneling environment  
        - command        - the command or path to binary to be executed  
        - username       - (optional) the account under which the command have to be executed  
    status  
        Check split-tunneling status  
```        

### Examples:  
    Initialize split-tunneling functionality:  
        ./splittun-ns.sh start  
        ./splittun-ns.sh start -i wlp3s0 -g 192.168.1.1 -d 1.1.1.1  
    Start commands in split-tunneling environment:  
        ./splittun-ns.sh run firefox  
        ./splittun-ns.sh run '/usr/bin/firefox'  
        ./splittun-ns.sh run 'ping 8.8.8.8'  
    Uninitialize split-tunneling functionality:  
        ./splittun-ns.sh stop  
        ./splittun-ns.sh stop -i wlp3s0  
    Check split-tunneling status:  
        ./splittun-ns.sh status  
