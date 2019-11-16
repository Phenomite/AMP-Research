# DVR DHCPDiscover (multiple CCTV products) UDP-MIB

## Port: 37810

## Proto: UDP

## Amplification factor: ~9x

## Reflector count: 297,056

---

Multiple DVR/XVR/NVR products implement multiple UDP ports for different SNMP-like protocols.
37810 (this finding) is specifically for IP Search and DHCP Discovery JSON.
37777 is the default port for remote connections, etc.

### Example Request / Response

- Request: 62 bytes

  - > ~# echo -ne '\x20\x00\x00\x00\x44\x48\x49\x50\x00\x00\x00\x00\x00\x00\x00\x00\x3e\x00\x00\x00\x00\x00\x00\x00\x3e\x00\x00\x00\x00\x00\x00\x00\x7b\x22\x6d\x65\x74\x68\x6f\x64\x22\x3a\x22\x44\x48\x44\x69\x73\x63\x6f\x76\x65\x72\x2e\x73\x65\x61\x72\x63\x68\x22\x7d'|nc -u 191.251.40.102 37810

- Response: 759 bytes

  - `DHIP▒▒{"mac":"58:10:8c:4d:3b:fa","method":"client.notifyDevInfo","params":{"deviceInfo":{"AlarmInputChannels":0,"AlarmOutputChannels":0,"DeviceClass":"MHDX","DeviceType":"MHDX 1016","HttpPort":1101,"IPv4Address":{"DefaultGateway":"192.168.15.1","DhcpEnable":false,"IPAddress":"192.168.15.110","SubnetMask":"255.255.255.0"},"IPv6Address":{"DefaultGateway":"fe80::1272:23ff:fe4c:1d5a","DhcpEnable":true,"IPAddress":"2804:7f4:5380:8bc5:5810:8cff:fe4d:3bfa\/64","LinkLocalAddress":"fe80::5a10:8cff:fe4d:3bfa\/64"},"MachineName":"KELVIN","Manufacturer":"Intelbras","Port":1102,"RemoteVideoInputChannels":2,"SerialNo":"O9RF220012635","Vendor":"Intelbras","Version":"3.210.IB01.3","VideoInputChannels":16,"VideoOutputChannels":0}}}`

### Documentation

- <https://ipvm.com/reports/dahua-oem> (OEM Listing and article about US bans)
- <https://community.boschsecurity.com/t5/Security-Video/What-Ports-need-to-be-open-for-LAN-and-WAN-Access-for-Divar-AN/ta-p/536> (Ports)
- <https://www.dahuasecurity.com/?us> (A large number of responders are this manufacturer)
- <https://www.hybrid-analysis.com/sample/0a6d12fc58871c387c2e322b099a545b981a91f6719c5251adf6a79c4bd851b7?environmentId=120> (Potential Dahua windows client analysis)

### Mitigations

- Stop allowing Internet access, restrict to LAN as default configuration (vendor issue)!
- Similar to WSD SOAP Discovery Queries
- <https://www.csoonline.com/article/3089298/iot-botnet-25-513-cctv-cameras-used-in-crushing-ddos-attacks.html>
