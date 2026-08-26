# Networking Fundamentals — Condensed Notes

## IP addresses and ports

- An **IP address** identifies a *machine* (or interface) on a network.
  IPv4 = four octets (`192.168.1.10`), IPv6 = the longer hex format.
- A **port** identifies a *specific service/process* on that machine.
  Combined, `IP:port` (a "socket") uniquely identifies one conversation
  endpoint — e.g. `192.168.1.10:443`.
- Ports 0–1023 are "well-known" (80=HTTP, 443=HTTPS, 22=SSH, 53=DNS,
  3389=RDP). 1024–49151 are registered. 49152–65535 are ephemeral —
  your OS hands these out temporarily for outbound connections.

## DNS

- Translates human-readable names into IPs. Flow: your resolver (often
  your ISP or `1.1.1.1` / `8.8.8.8`) checks its cache → asks a root server
  → asks the TLD server (`.com`) → asks the authoritative nameserver for
  the domain → gets the answer → caches it for the TTL.
- **A record**: hostname → IPv4 address.
- **AAAA record**: hostname → IPv6 address.
- **CNAME**: hostname → *another hostname* (alias; requires a follow-up
  lookup).
- **MX**: mail server for the domain. **TXT**: arbitrary text (SPF/DKIM,
  domain verification, etc.) — worth knowing since these show up
  constantly in phishing/spoofing investigations.

## HTTP / HTTPS

- HTTP is a request/response protocol. A request has:
  a **method** (GET, POST, PUT, DELETE, ...), a **path**, **headers**
  (Host, User-Agent, Cookie, Authorization, Content-Type...), and
  optionally a **body**.
- A response has a **status code**:
  - 2xx = success (200 OK)
  - 3xx = redirect (301 permanent, 302 temporary)
  - 4xx = client error (401 unauthorized, 403 forbidden, 404 not found)
  - 5xx = server error (500 internal server error)
- **HTTPS = HTTP + TLS.** TLS handles the crypto handshake (certificate
  exchange, key negotiation) *before* any HTTP data flows, giving you
  encryption in transit, integrity, and server identity verification.
  It does **not** by itself guarantee the server or content is trustworthy
  — just that you're talking to who the cert says you're talking to, and
  no one in the middle can read/tamper with it.

## How web applications work (high level)

Client (browser) → DNS lookup → TCP/TLS handshake → HTTP request to a
server → server may talk to an application layer (app server) → which
may talk to a database → response flows back up the same chain. Most web
app vulnerabilities live in that "server processes the request" step
(injection, auth flaws, business logic issues) — this is what Week 4
builds on.

## LAN vs. public internet, NAT, routing

- **LAN** (Local Area Network): machines on the same local network,
  typically using **private IP ranges** (`10.0.0.0/8`, `172.16.0.0/12`,
  `192.168.0.0/16`) that aren't routable on the public internet.
- **NAT** (Network Address Translation): your router rewrites private
  source IPs to its one public IP for outbound traffic, and tracks the
  mapping so return traffic gets routed back to the right internal
  machine. This is why multiple devices at home can share one public IP.
- **Routing**: at a basic level, each hop (router) looks at the
  destination IP, checks its routing table, and forwards the packet to
  the next hop closer to the destination — repeat until it arrives.

## Do these, don't just read them

- Run `curl -v https://example.com` and actually read the TLS handshake
  + request/response headers it prints.
- Run `nslookup` or `dig` against a few domains and look at A vs CNAME
  answers for yourself (e.g. `dig www.github.com`).
- TryHackMe: HTTP in Detail, Web Application Basics, DNS in Detail,
  Intro to LAN (see README for links).
