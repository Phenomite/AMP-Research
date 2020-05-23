# SRCDS (Source game Dedicated Server)

## Common Ports: 2302 (Arma3), 27015-27020 (HL2, Gmod, TF2, ARK: Survival Evolved), 28015, 21025 (Starbound)

## Proto: UDP

## Amplification factor: ~5x

## Reflector count: ~25,000

---

Amplification factor varies depending on player stats, server slot fullness and player names (random data).

The TSource Engine query (A2S_INFO) has trivially been used as a direct UDP attack against game servers for many years, however by using it to reflect off other game servers, the data returned can typically be an amplification itself.

- `ffffffff54536f7572636520456e67696e6520517565727900`

### Documentation

- <https://developer.valvesoftware.com/wiki/Source_Dedicated_Server> (Other ports in use)
- <https://developer.valvesoftware.com/wiki/Server_queries#A2S_INFO>
- <https://github.com/BerntA/SRCDSMonitor>

### Mitigations

- <https://github.com/blastehh/SourceQueryCacheMono> (For SRCDS themselves)
- <https://stackoverflow.com/questions/825481/iptable-rule-to-drop-packet-with-a-specific-substring-in-payload> (With ^0xffffffff)
- <http://www.dedicated-server.ru/vbb/archive/index.php?t-27617.html>
