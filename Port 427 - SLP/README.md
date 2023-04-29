# SLP (Service Location Protocol)

## Port: **427**

## Proto: **UDP/TCP**

## Amplification factor: **1.6x and 12x (2,200x when paired with CVE-2023-29552)**

## Reflector count: ~35,000 (April, 2023)

---

### Payload
<pre>\x02\t\x00\x00\x1d\x00\x00\x00\x00\x00s_\x00\x02en\x00\x00\xff\xff\x00\x07default</pre>

### Response
<pre></pre>

Other links:
- https://www.bleepingcomputer.com/news/security/new-slp-bug-can-lead-to-massive-2-200x-ddos-amplification-attacks/
- https://www.netscout.com/blog/asert/slp-reflectionamplification-ddos-attack-vector
- https://curesec.com/blog/article/CVE-2023-29552-Service-Location-Protocol-Denial-of-Service-Amplification-Attack-212.html
- https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-29552/
- https://github.com/curesec/slpload