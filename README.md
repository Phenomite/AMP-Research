# AMP-Research

## Research on exotic UDP/TCP amplification vectors, payloads and mitigations

The subfolder's in this repo will house the following:
 - Overview README.md
   - Potential official protocol documentation.
   - Potential Mitigation strategies.
 - Scanning payload (e.g. for use in zmap) OR potential scanning script (C).
 - Raw socket flood script (C) for analysis to build flowspec or ACL mitigations.


## What is amplification in respect to network protocols?

Amplification is where well-formed or malformed socket or application data requests elicit a response larger than the input data. This can then be abused to "amplify" a request, usually by means of Distributed Reflected Denial of Service (DDoS/DRDoS) attacks.

Best way to show what this means is an example.

Example UDP response size from 1 byte on MSSQL protocol:
- >~# echo -ne '\x02' | nc -u -q 2 190.xx.xx.xx 1434|xxd -p|wc -c
	<pre>629 bytes</pre>
	>That's an amplification factor of over 23x.

Example hex response from a discovery probe to Apple Remote Desktop protocol:
 - >~# echo -ne '\x00\x14\x00\x01\x03' |nc -u 89.xx.xx.xx 3283|hexdump
    <pre>
	0000000 0100 ea03 3100 0000 0000 0000 0000 0000
	0000010 0000 0000 0000 0000 0000 0000 0000 0000
	0000020 0000 0000 0000 0000 0100 0000 0000 0000
	0000030 0000 0000 0000 0000 0000 0000 0000 0000
	_
	0000050 0000 1200 0000 0000 0000 0000 0000 0000
	0000060 0000 0000 0000 0000 0000 0000 0000 0000
	0000070 0000 0000 0000 0000 0000 0000 0000 640a
	0000080 7461 6861 6565 6472 0034 0000 0000 0000
	0000090 0000 0000 0000 0000 0000 0000 0000 0000
	_
	00000c0 0000 0001 0000 0000 0000 0000 0000 0000
	00000d0 0000 0000 0000 9803 0000 0100 18f0 ed98
	00000e0 9288 0000 0000 0a00 6400 6100 7400 6100
	00000f0 6800 6500 6500 7200 6400 3400 0000 0000
	0000100 0000 0000 0000 0000 0000 0000 0000 0000
	</pre>

## Compiling the C code in this repo?

Remember that checksum ones-compliment relies on 32bit compilation.
This really only matters with TCP scripts.


## Vulnerable reflectors?

No. This is here to help everyone mitigate amplification vectors. 