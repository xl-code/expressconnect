# Method for testing the network performance of the leased line {#concept_fnm_bkb_ydb .concept}

After completing the leased line access, you need to test the performance of the leased line to ensure that it can meet your service needs.

## Prerequisites {#section_h3q_fkb_ydb .section}

Before the test, ensure you have made the following preparations:

-   Complete configurations regarding leased line access and routes. The local data center must be connected to the VPC through a leased line.

-   Prepare a network access device for the local data center: The network access device is subjected to stress testing to test the packets per second \(pps\) of the local data center. It serves as the client or server in the Netperf or iperf3 test.

    In this tutorial, the IP address of the local data center is 192.168.100.1.

-   Prepare eight VPC ECS instances: The ECS instances serve as clients or servers in the Netperf or iperf3 test. They are connected to the network access device of the local data center to transmit test configurations and test results.

    In this tutorial, eight ECS instances are used, of which the specification is ecs.se1.2xlarge, the image is centos\_7\_2\_64\_40G\_base\_20170222.vhd, and the IP address range is 172.16.0.2 − 172.16.0.9.


## Build the test environment {#section_uv3_3kb_ydb .section}

Install Netperf

Netperf is a tool for testing network performance and is based on TCP or UDP transmission.

Follow these steps to install Netperf on the network access device of the local data center and the eight ECS instances.

1.  Run the following command to download netperf:

    ```
    wget -c "https://codeload.github.com/HewlettPackard/netperf/tar.gz/netperf-2.5.0" -O netperf-2.5.0.tar.gz
    ```

2.  Run the following command to install netperf:

    ```
    tar -zxvf netperf-2.5.0.tar.gz
    cd netperf-netperf-2.5.0
    ./configure 
    make 
    make install
    ```

3.  Run the `netperf -h` and `netserver -h` commands to verify if the installation is successful.

Install iperf3

Iperf3 is a tool for testing network performance and can test the maximum TCP or UDP bandwidth.

Follow these steps to install iperf3 on the network access device of the local data center and the eight ECS instances.

1.  Run the following command to download iperf3:

    ```
    yum install git -y  
    git clone https://github.com/esnet/iperf
    ```

2.  Run the following command to install iperf3:

    ```
    cd iperf
    ./configure && make && make install && cd ..
    cd src
    ADD_PATH="$(pwd)" 
    PATH="${ADD_PATH}:${PATH}"
    export PATH
    ```

3.  Run the `iperf3 -h` command to verify if the installation is successful.

Enable the multiple queues feature

Run the following command on the network access device of the local data center to enable the multiple queue feature \( Assume the interface connected to the leased line is eth0.\)

```
ethtool -L eth0 combined 4
echo "ff" > /sys/class/net/eth0/queues/rx-0/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-1/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-2/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-3/rps_cpus
```

## Use netperf to test the packet forwarding performance of the leased line {#section_l4r_jlb_ydb .section}

After being installed, netperf creates two command line tools: netserver \(server side\) and netperf \(client side\). Main parameters of the two tools are shown in the following table.

|Tool name|Main parameter|Parameter description|
|:--------|:-------------|:--------------------|
|netserver \(server side: receiving side tool\)|-p|The port of the server.|
|netperf \(client side: sending side tool\)|-H|The IP address of the network access device of the local data center or the VPC server.|
|-p|The port of the network access device of the local data center or the VPC server.|
|-l|The running duration.|
|-t|The protocol used for sending packets: TCP\_STREAM or UDP\_STREAM.We recommend using UDP\_STREAM.

|
|-m|The data packet size.-   We recommend that you set the value to 1 when testing pps.
-   We recommend that you set the value to 1400 when testing bps \(bit per second\).

|

Test the inbound direction

1.  Start the netserver process on the network access device of the local data center and specify different ports:

    ```
     netserver -p 11256
     netserver -p 11257 
     netserver -p 11258 
     netserver -p 11259 
     netserver -p 11260 
     netserver -p 11261 
     netserver -p 11262 
     netserver -p 11263
    ```

2.  Start the netperf process on the eight ECS instances in the VPC and specify different ports connecting to the network access device of the local data center.

    ```
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #first ECS instance
    netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1 #second ECS instance
    netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1 #third ECS instance
    netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1 #fourth ECS instance
    netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1 #fifth ECS instance
    netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1 #sixth ECS instance
    netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1 #seventh ECS instance
    netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1 #eighth ECS instance
    ```

3.  If you want to test bps, change the preceding commands to:

    ```
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1400 #first ECS instance
    netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1400 #second ECS instance
    netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1400 #third ECS instance
    netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1400 #fourth ECS instance
    netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1400 #fifth ECS instance
    netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1400 #sixth ECS instance
    netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1400 #seventh ECS instance
    netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1400 #eighth ECS instance
    ```


Test the outbound direction

1.  Start the netserver process on the eight ECS instances in the VPC and specify the port as follows:

    ```
    netserver -p 11256
    ```

2.  Start eight netperf processes on the network access device of the local data center and specify different IP addresses.

    ```
     netperf -H 172.16.0.2 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #first ECS instance
     netperf -H 172.16.0.3 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #second ECS instance
     netperf -H 172.16.0.4 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #third ECS instance
     netperf -H 172.16.0.5 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #fourth ECS instance
     netperf -H 172.16.0.6 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #fifth ECS instance
     netperf -H 172.16.0.7 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #sixth ECS instance
     netperf -H 172.16.0.8 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #seventh ECS instance
     netperf -H 172.16.0.9 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #eighth ECS instance
    ```

3.  If you want to test bps, change the preceding commands to:

    ```
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1400 #first ECS instance
     netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1400 #second ECS instance
     netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1400 #third ECS instance
     netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1400 #fourth ECS instance
     netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1400 #fifth ECS instance
     netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1400 #sixth ECS instance
     netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1400 #seventh ECS instance
     netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1400 #eighth ECS instance
    ```


Test the outbound direction

1.  Start the netserver process on the eight ECS instances in the VPC and specify the port as follows:

    ```
    netserver -p 11256
    ```

2.  Start eight netperf processes on the network access device of the local data center and specify different IP addresses.

    ```
     netperf -H 172.16.0.2 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #first ECS instance
     netperf -H 172.16.0.3 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #second ECS instance
     netperf -H 172.16.0.4 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #third ECS instance
     netperf -H 172.16.0.5 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #fourth ECS instance
     netperf -H 172.16.0.6 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #fifth ECS instance
     netperf -H 172.16.0.7 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #sixth ECS instance
     netperf -H 172.16.0.8 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #seventh ECS instance
     netperf -H 172.16.0.9 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #eighth ECS instance
    ```

3.  If you want to test bps, change the preceding commands to:

    ```
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1400 #first ECS instance
     netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1400 #second ECS instance
     netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1400 #third ECS instance
     netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1400 #fourth ECS instance
     netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1400 #fifth ECS instance
     netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1400 #sixth ECS instance
     netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1400 #seventh ECS instance
     netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1400 #eighth ECS instance
    ```


Analyze test results

The following results are displayed when netperf processes on the client side are completed.

```
   Socket Message Elapsed Messages
   Size Size Time Okay Errors Throughput
   bytes bytes secs # # 10^6bits/sec
   124928 1 10.00 4532554 0 3.63
   212992 10.00 1099999 0.88
```

Descriptions of fields in the test results are shown in the following table:

|Field|Description|
|:----|:----------|
|Socket Size|Buffer size|
|Message Size|Packet size \(Byte\)|
|Elapsed Time|The duration of test \(s\)|
|Message Okay|The number of packets successfully sent out|
|Message Errors|The number of packets fail to be sent out|
|Throughput|Network throughput \(Mbit/s\)|

You can obtain the pps of the tested link if you divide the number of packets successfully sent out by the duration of test. That is, pps = the number of packets successfully sent out / the duration of test.

## Use iperf3 to test the bandwidth of the leased line {#section_ip2_l4b_ydb .section}

Main parameters of iperf3 are shown in the following table.

|Tool name|Main parameter|Description|
|:--------|:-------------|:----------|
|iPerf3|-s|Indicates receiving packets as the server.|
|-i|Interval between every two reports, in seconds.|
|-p|The listening port of the server.|
|-u|Indicates using the UDP protocol to send packets. If this parameter is not specified, the TCP protocol is used.|
|-l|Indicates the length of the read-write buffer. We recommend that you set the value to 16 when testing the packet forwarding performance and to 1400 when testing the bandwidth.|
|-b|The bandwidth used by the UDP mode, in bits/s.|
|-t|Set the duration of transmission. In the specified time period, iperf repeatedly sends packets of specified length. The default value is 10 seconds.|
|-A|CPU affinity. You can bind an iperf3 process to the logic CPU of the corresponding number to avoid cross-CPU scheduling of the iperf3 process.|

Test the inbound direction

1.  Start the iperf3 process in the server mode on the network access device of the local data center and specify different ports as follows:

    ```
     iPerf3 -s -i 1 -p 16001
     iPerf3 -s -i 1 -p 16002
     iPerf3 -s -i 1 -p 16003
     iPerf3 -s -i 1 -p 16004
     iPerf3 -s -i 1 -p 16005
     iPerf3 -s -i 1 -p 16006
     iPerf3 -s -i 1 -p 16007
     iPerf3 -s -i 1 -p 16008
    ```

2.  Start the iperf3 process in the client mode on the eight ECS instances in the VPC and specify different ports connecting to the network access device of the local data center.

    ```
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16001 -A 1
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16002 -A 2
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16003 -A 3
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16004 -A 4
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16005 -A 5
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16006 -A 6
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16007 -A 7
     iPerf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16008 -A 8
    ```


Test the outbound direction

1.  Start the iperf3 process in the server mode on each ECS instance in the VPC and specify the port:

    ```
     iPerf3 -s -i 1 -p 16001
    ```

2.  Start eight iperf3 processes in the client mode on the network access device of the local data center and the value of `-c` is the IP address of each ECS instance.

    ```
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.2 -i 1 -p 16001 -A 1
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.3 -i 1 -p 16001 -A 2
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.4 -i 1 -p 16001 -A 3
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.5 -i 1 -p 16001 -A 4
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.6 -i 1 -p 16001 -A 5
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.7 -i 1 -p 16001 -A 6
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.8 -i 1 -p 16001 -A 7
     iPerf3 -u -l 16 -b 100m -t 120 -c 172.16.0.9 -i 1 -p 16001 -A 8
    ```


Analyze test results

The following results are displayed when iperf3 processes on the client side are completed.

```
[ ID] Interval Transfer Bandwidth Jitter Lost/Total Datagrams
[ 4] 0.00-10.00 sec 237 MBytes 199 Mbits/sec 0.027 ms 500/30352 (1.6%)
[ 4] Sent 30352 datagrams
```

Descriptions of fields in the rest results are shown in the following table:

|Field|Definition|
|:----|:---------|
|Transfer|The total number of data transmitted|
|Bandwidth|Bandwidth|
|Jitter|Jitter|
|Lost/Total Datagrams|The number of dropped packets / The total number of packets \(packet loss\)|

PPS = The number of packets received by the peer end/Duration

**Note:** We recommend that you run the `sar` command on the server side to count the packets actually received and use the obtained value as the actual result, such as `sar -n DEV 1 320`.

## Alibaba Cloud side speed limit {#section_v14_5pb_ydb .section}

In addition to limits on the leased line, the following are limits on the communication between the VPC and the local data center:

-   The maximum read-write speed of OSS is 5 Gbit/s.
-   To improve the reliability, the speed of a single hash stream from the VPC to the VBR is limited to “Express Connect bandwidth / 12”. For example, if the bandwidth from the VBR to the VPC is large1, namely 1 Gbps, the maximum bandwidth of a single hash stream is 83 Mbps.

    Hash stream: The data stream that is defined by the combination of the source IP address, source port, transport layer protocol, destination IP address, and destination port. For example, “192.168.1.1 10000 TCP 121.14.88.76 80” forms a hash stream. A terminal whose IP address is 192.168.1.1 is connected to port 80 of a terminal whose IP address is 121.14.88.76 through port 10000 by using the TCP protocol.


