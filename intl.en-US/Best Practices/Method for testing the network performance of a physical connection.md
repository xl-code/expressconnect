# Method for testing the network performance of a physical connection {#concept_fnm_bkb_ydb .concept}

After a physical connection is completed, you need to test the performance of the physical connection to ensure that it can meet your service needs.

## Prerequisites {#section_h3q_fkb_ydb .section}

Before the test, make sure that you have made the following preparations:

-   Configurations regarding the physical connection and routes are completed. The on-premises data center is connected to the VPC through a leased line.

-   A network access device for the on-premises data center is prepared. The network access device is subjected to a stress test to measure the packets per second \(pps\) of the on-premises data center. It serves as the client or server in the Netperf or iPerf3 test.

    In this topic, the IP address of the network device for the on-premises data center is 192.168.100.1.

-   Eight VPC-type ECS instances are created. The ECS instances serve as clients or servers in the Netperf or iPerf3 test. They are connected to the network access device of the on-premises data center to transmit test configurations and test results.

    For the eight ECS instances, the specification is ecs.se1.2xlarge, the image is centos\_7\_2\_64\_40G\_base\_20170222.vhd, and the IP address range is from 172.16.0.2 to 172.16.0.9.


## Build the test environment {#section_uv3_3kb_ydb .section}

Install Netperf

Netperf is a tool for testing network performance and is targeted for TCP or UDP transmission.

Follow these steps to install Netperf on the network access device of the on-premises data center and the eight ECS instances.

1.  Run the following command to download Netperf:

    ``` {#codeblock_8bb_ltr_bfe}
    wget -c "https://codeload.github.com/HewlettPackard/netperf/tar.gz/netperf-2.5.0" -O netperf-2.5.0.tar.gz
    ```

2.  Run the following command to install Netperf:

    ``` {#codeblock_zwq_znx_wb6}
    tar -zxvf netperf-2.5.0.tar.gz
    cd netperf-netperf-2.5.0
    ./configure 
    make 
    make install
    ```

3.  Run the `netperf -h` and `netserver -h` commands to verify if the installation is successful.

Install iPerf3

iPerf3 is a tool for testing network performance and can test the maximum TCP or UDP bandwidth.

Follow these steps to install iPerf3 on the network access device of the on-premises data center and the eight ECS instances.

1.  Run the following command to download iPerf3:

    ``` {#codeblock_s4v_qho_ao6}
    yum install git -y  
    git clone https://github.com/esnet/iperf
    ```

2.  Run the following command to install iPerf3:

    ``` {#codeblock_fug_shs_84r}
    cd iperf
    ./configure && make && make install && cd ..
    cd src
    ADD_PATH="$(pwd)" 
    PATH="${ADD_PATH}:${PATH}"
    export PATH
    ```

3.  Run the `iperf3 -h` command to verify if the installation is successful.

Enable the multiple queue feature

Run the following command on the network access device of the on-premises data center to enable the multiple queue feature. \(Assume the interface connected to the leased line is eth0.\)

``` {#codeblock_l1o_xv7_qw2}
ethtool -L eth0 combined 4
echo "ff" > /sys/class/net/eth0/queues/rx-0/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-1/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-2/rps_cpus
echo "ff" > /sys/class/net/eth0/queues/rx-3/rps_cpus
```

## Use Netperf to test the packet forwarding performance of the physical connection {#section_l4r_jlb_ydb .section}

After being installed, Netperf creates two command line tools: netserver \(server side\) and netperf \(client side\). Main parameters of the two tools are described in the following table.

|Tool name|Main parameter|Description|
|:--------|:-------------|:----------|
|netserver \(server side: receiving side tool\)|-p|The port of the server.|
|netperf \(client side: sending side tool\)|-H|The IP address of the network access device of the on-premises data center or the VPC server.|
|-p|The port of the network access device of the on-premises data center or the VPC server.|
|-l|The running duration.|
|-t|The protocol used for sending packets: TCP\_STREAM or UDP\_STREAM. We recommend UDP\_STREAM.

 |
|-m|The data packet size. -   We recommend that you set the value to 1 when testing pps.
-   We recommend that you set the value to 1400 when testing bps \(bit per second\).

 |

Test the inbound direction

1.  Start the netserver process on the network access device of the on-premises data center and specify different ports:

    ``` {#codeblock_c1p_jio_gty}
     netserver -p 11256
     netserver -p 11257 
     netserver -p 11258 
     netserver -p 11259 
     netserver -p 11260 
     netserver -p 11261 
     netserver -p 11262 
     netserver -p 11263
    ```

2.  Start the netperf process on the eight ECS instances in the VPC and specify different ports connecting to the network access device of the on-premises data center.

    ``` {#codeblock_jj0_22s_jgg}
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the first ECS instance
    netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1 #the second ECS instance
    netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1 #the third ECS instance
    netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1 #the fourth ECS instance
    netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1 #the fifth ECS instance
    netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1 #the sixth ECS instance
    netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1 #the seventh ECS instance
    netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1 #the eighth ECS instance
    ```

3.  If you want to test bps, change the preceding commands to:

    ``` {#codeblock_3zb_ufk_bqp}
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1400 #the first ECS instance
    netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1400 #the second ECS instance
    netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1400 #the third ECS instance
    netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1400 #the fourth ECS instance
    netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1400 #the fifth ECS instance
    netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1400 #the sixth ECS instance
    netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1400 #the seventh ECS instance
    netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1400 #the eighth ECS instance
    ```


Test the outbound direction

1.  Start the netserver process on the eight ECS instances in the VPC and specify the port as follows:

    ``` {#codeblock_c7v_765_212}
    netserver -p 11256
    ```

2.  Start eight netperf processes on the network access device of the on-premises data center and specify different IP addresses:

    ``` {#codeblock_2m2_iyt_o7y}
     netperf -H 172.16.0.2 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the first ECS instance
     netperf -H 172.16.0.3 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the second ECS instance
     netperf -H 172.16.0.4 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the third ECS instance
     netperf -H 172.16.0.5 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the fourth ECS instance
     netperf -H 172.16.0.6 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the fifth ECS instance
     netperf -H 172.16.0.7 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the sixth ECS instance
     netperf -H 172.16.0.8 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the seventh ECS instance
     netperf -H 172.16.0.9 -p 11256 -t UDP_STREAM -l 300 -- -m 1 #the eighth ECS instance
    ```

3.  If you want to test bps, change the preceding commands to:

    ``` {#codeblock_7h0_53e_vb3}
     netperf -H 192.168.100.1 -p 11256 -t UDP_STREAM -l 300 -- -m 1400 #the first ECS instance
     netperf -H 192.168.100.1 -p 11257 -t UDP_STREAM -l 300 -- -m 1400 #the second ECS instance
     netperf -H 192.168.100.1 -p 11258 -t UDP_STREAM -l 300 -- -m 1400 #the third ECS instance
     netperf -H 192.168.100.1 -p 11259 -t UDP_STREAM -l 300 -- -m 1400 #the fourth ECS instance
     netperf -H 192.168.100.1 -p 11260 -t UDP_STREAM -l 300 -- -m 1400 #the fifth ECS instance
     netperf -H 192.168.100.1 -p 11261 -t UDP_STREAM -l 300 -- -m 1400 #the sixth ECS instance
     netperf -H 192.168.100.1 -p 11262 -t UDP_STREAM -l 300 -- -m 1400 #the seventh ECS instance
     netperf -H 192.168.100.1 -p 11263 -t UDP_STREAM -l 300 -- -m 1400 #the eighth ECS instance
    ```


Analyze test results

The following results are displayed when netperf processes on the client side are completed.

``` {#codeblock_a6y_usz_7vh}
   Socket  Message  Elapsed      Messages
   Size    Size     Time         Okay Errors   Throughput
   bytes   bytes    secs            #      #   10^6bits/sec
   124928       1   10.00     4532554      0       3.63
   212992           10.00     1099999              0.88
```

The fields in the test results are described in the following table:

|Field|Description|
|:----|:----------|
|Socket Size|The buffer size.|
|Message Size|The packet size. Unit: Byte|
|Elapsed Time|The duration of the test. Unit: seconds|
|Message Okay|The number of packets successfully sent out.|
|Message Errors|The number of packets that fail to be sent out.|
|Throughput|Network throughput. Unit: Mbit/s|

You can obtain the pps of the tested link if you divide the number of packets successfully sent out by the duration of the test. That is, pps = the number of packets successfully sent out/the duration of the test.

## Use iPerf3 to test the bandwidth of the physical connection {#section_ip2_l4b_ydb .section}

Main parameters of iPerf3 are described in the following table:

|Tool name|Main parameter|Description|
|:--------|:-------------|:----------|
|iPerf3|-s|Indicates receiving packets as the server.|
|-i|The interval between every two reports. Unit: seconds|
|-p|The listening port of the server.|
|-u|Indicates using the UDP protocol to send packets. If this parameter is not specified, the TCP protocol is used.|
|-l|Indicates the length of the read/write buffer. We recommend that you set the value to 16 when you test the packet forwarding performance and to 1400 when you test the bandwidth.|
|-b|The bandwidth used in the UDP mode. Unit: bit/s|
|-t|Set the duration of transmission. In the specified time period, iPerf repeatedly sends packets of specified length. The default value is 10 seconds.|
|-A|CPU affinity. You can associate an iperf3 process with the logic CPU of the corresponding number to avoid cross-CPU scheduling of the iPerf3 process.|

Test the inbound direction

1.  Start the iPerf3 process in the server mode on the network access device of the on-premises data center and specify different ports as follows:

    ``` {#codeblock_10u_59i_c7j}
     iperf3 -s -i 1 -p 16001
     iperf3 -s -i 1 -p 16002
     iperf3 -s -i 1 -p 16003
     iperf3 -s -i 1 -p 16004
     iperf3 -s -i 1 -p 16005
     iperf3 -s -i 1 -p 16006
     iperf3 -s -i 1 -p 16007
     iperf3 -s -i 1 -p 16008
    ```

2.  Start the iPerf3 process in the client mode on the eight ECS instances in the VPC and specify different ports connecting to the network access device of the on-premises data center:

    ``` {#codeblock_u0w_50t_16u}
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16001 -A 1
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16002 -A 2
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16003 -A 3
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16004 -A 4
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16005 -A 5
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16006 -A 6
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16007 -A 7
     iperf3 -u -l 16 -b 100m -t 120 -c 192.168.100.1 -i 1 -p 16008 -A 8
    ```


Test the outbound direction

1.  Start the iPerf3 process in the server mode on each ECS instance in the VPC and specify the port:

    ``` {#codeblock_q9f_m1i_o8h}
     iperf3 -s -i 1 -p 16001
    ```

2.  Start eight iPerf3 processes in the client mode on the network access device of the on-premises data center and the value of `-c` is the IP address of each ECS instance.

    ``` {#codeblock_kdb_f6u_d2w}
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.2 -i 1 -p 16001 -A 1
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.3 -i 1 -p 16001 -A 2
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.4 -i 1 -p 16001 -A 3
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.5 -i 1 -p 16001 -A 4
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.6 -i 1 -p 16001 -A 5
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.7 -i 1 -p 16001 -A 6
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.8 -i 1 -p 16001 -A 7
     iperf3 -u -l 16 -b 100m -t 120 -c 172.16.0.9 -i 1 -p 16001 -A 8
    ```


Analyze test results

The following results are displayed when iPerf3 processes on the client side are completed.

``` {#codeblock_sbi_5mr_1ja}
[ ID]  Interval        Transfer    Bandwidth      Jitter    Lost/Total Datagrams
[  4]  0.00-10.00 sec  237 MBytes  199 Mbits/sec  0.027 ms  500/30352 (1.6%)
[  4]  Sent 30352  datagrams
```

The fields in the rest results are described in the following table:

|Field|Description|
|:----|:----------|
|Transfer|The total amount of data transmitted|
|Bandwidth|The bandwidth|
|Jitter|Jitter|
|Lost/Total Datagrams|The number of dropped packets/The total number of packets \(packet loss\)|

PPS = The number of packets received by the peer end/Duration

**Note:** We recommend that you run the `sar` command on the server side to count the packets actually received and use the obtained value as the actual result, for example, `sar -n DEV 1 320`.

## Alibaba Cloud-side speed limit {#section_v14_5pb_ydb .section}

In addition to limits on the physical connection, the following are limits on the communication between the VPC and the on-premises data center:

-   The maximum read/write speed of OSS is 5 Gbit/s.
-   To improve the reliability, the speed of a single hash stream from the VPC to the VBR is limited to one twelfth of the Express Connect bandwidth. For example, if the bandwidth from the VBR to the VPC is large1, namely 1 Gbit/s, the maximum bandwidth of a single hash stream is 85 Mbit/s.

    Hash stream: the data stream that is defined by the combination of the source IP address, source port, transport layer protocol, destination IP address, and destination port. For example, 192.168.1.1 10000 TCP 121.14.88.76 80 forms a hash stream. A terminal whose IP address is 192.168.1.1 is connected to port 80 of a terminal whose IP address is 121.14.88.76 through port 10000 by using the TCP protocol.


