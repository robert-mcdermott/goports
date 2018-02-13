# goports

Simple TCP port scanner written in Golang

## Usage

```
./goports [-t <cpu threads> -c <concurrency> -to <timeout in ms> -v] -ip <IP or CIDR> -p <ports>

Example: ./goports -ip 192.168.73.1/28 -p 22,80,443,8000-8100

  -c int
  	Optional: set number of concurrent port open operations to use; defaults to 32 per 
        logical CPU 
  
  -ip string
    	Required: IP address or CIDR block to scan

  -p string
    	Required: Set of ports to scan; individual ports separated by "," port ranges 
        separated by "-" (22,80,8000-8100)

  -t int
    	Optional: set number of CPU threads to use; defaults to the number of logical 
        CPUs in your system (default 4)

  -to int
    	Optional: Specify the amount of time to wait in milliseconds; defaults to 100 

  -q	Optional: quiet mode; suppress the summary report

  -v	Optional: Turn on verbose output mode; shows both open and closed ports
        and any error messages encountered during connection.

  -h	print usage information
```

## Output

```
./goports -ip 192.168.0.0/16 -p 22-8000 

...
192.168.73.109:80, open
192.168.73.103:80, open
192.168.73.110:80, open
192.168.88.202:80, open
192.168.88.111:80, open
192.168.88.199:80, open
192.168.88.200:80, open
192.168.73.208:80, open
192.168.73.241:80, open
192.168.73.244:80, open
192.168.73.124:80, open
192.168.73.176:80, open

Hosts scanned: 65534
Ports scanned: 65534
Elapsed time: 0.91 seconds
Scan Rates:
    ports/s: 71719.34
    hosts/s: 71719.34
```
