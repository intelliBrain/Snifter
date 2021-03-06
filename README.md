Snifter
=======

Snifter is a raw socket IP packet capturing tool for Windows, with a tiny CPU and memory footprint.

Output is written in [PCAPNG](https://github.com/pcapng/pcapng) format, and you can filter captured packets based on protocol, source/destination address and source/destination port

Why?
----

You can't capture on the local loopback address 127.0.0.1 with a Windows packet capture driver like [WinPcap](https://wiki.wireshark.org/WinPcap) - but you can by using a raw socket sniffer like Snifter.

Limitations
-----------

You must run Snifter with elevated privileges - this is a Windows requirement to create raw sockets.

For now at least, Snifter only supports IPv4. It should be straightforward to add support for IPv6, but I don't use IPv6 yet, so haven't added it.

Usage
-----

````
snifter.exe -i x -f filename

  -i, --interface=VALUE      ID of the interface to listen on
  -f, --filename=VALUE       Filename to output sniffed packets to. Defaults to snifter.pcapng
  -o, --operator=VALUE       Whether filters should be AND or OR. Defaults to OR
  -p, --protocol=VALUE       Filter packets by IANA registered protocol number
  -s, --source-address=VALUE Filter packets by source IP address
  -d, --dest-address=VALUE   Filter packets by destination IP address
  -x, --source-port=VALUE    Filter packets by source port number
  -y, --dest-port=VALUE      Filter packets by destination port number
  -h, -?, --help             Show command line options
````

Run `snifter.exe -h` to see a list of available network interfaces.

Note that each filter option can only be specified once.
