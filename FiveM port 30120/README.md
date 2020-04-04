# FiveM (Grand Theft Auto 5 FXServer)

## Port: 30120

## Proto: UDP

## Amplification factor: ~7-10x

## Reflector count: Coming soon...

---

- A flavour of Grand Theft Auto V with "modifications" and multiplayer based on CitizenFX server Source Engine flavour, allowing the use of dedicated servers to host your own GTAV experience.
- They claim it supports LUA and Node on both server and client (erg).
- Vulnerable to CWE-406 as per usual with Source Engine servers.

### Example Request / Response

- Request: 16 bytes

  - `> ~# echo -ne '\xff\xff\xff\xff\x67\x65\x74\x69\x6e\x66\x6f\x20\x78\x78\x78\x00'|nc -u 94.23.28.219 30120 -w2`

- Response: Avg 250 bytes (differs greatly on custom server name)

  - ASCII (Only ASCII character space): `����infoResponse
\sv_maxclients\32\clients\1\challenge\xxx\gamename\CitizenFX\protocol\4\hostname\^4 [^0FR^1]  🌄^8Auria^8RP   ^9| 🌍 ^2Free-Acces - ^1100K Start 👊 ^9| 📺 ^5 100 FPS+^9 | ^6📁 Scripts & Mappings ^9|^3💎Staff-Actif |^7😈Gang/job^7 🔊^8discord.gg/es3ccJQ^9|\gametype\Freeroam\mapname\Auria_Map_\iv\1081559699`
  - Raw Bytes: `ffffffff696e666f526573706f6e73650a5c73765f6d6178636c69656e74735c33325c636c69656e74735c315c6368616c6c656e67655c787878005c67616d656e616d655c436974697a656e46585c70726f746f636f6c5c345c686f73746e616d655c5e34205b5e3046525e315d2020f09f8c845e3841757269615e3852502020205e397c20f09f8c8d205e32467265652d4163636573202d205e313130304b20537461727420f09f918a205e397c20f09f93ba205e3520313030204650532b5e39207c205e36f09f938120536372697074732026204d617070696e6773205e397c5e33f09f928e53746166662d4163746966207c5e37f09f988847616e672f6a6f625e3720f09f948a5e38646973636f72642e67672f65733363634a515e397c5c67616d65747970655c46726565726f616d5c6d61706e616d655c41757269615f4d61705f5c69765c31303831353539363939`

### Documentation

- FiveM Main Site <https://fivem.net/>
- CitizenFX's Github <https://github.com/citizenfx>
- Running FXServer <https://docs.fivem.net/docs/server-manual/setting-up-a-server/>
- List of Public Servers <https://servers.fivem.net/servers>

### Mitigations

- Vendor issue, CitizenFX will need to address it otherwise will just be left exposed and free to use as an amplification source.
