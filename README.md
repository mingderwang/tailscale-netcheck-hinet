# Tailscale Netcheck & Traceroute Analysis

**Date:** 2026-08-27  
**Location:** Taiwan (Taipei)  
**ISP:** HiNet (AS3462)

---

## Netcheck Results

```
Report:
  * Time: 2026-08-27 12:50:11.652218+08:00
  * UDP: true
  * IPv4: yes, 36.230.11.239:60969
  * IPv6: no, but OS has support
  * MappingVariesByDestIP: false
  * PortMapping: 
  * CaptivePortal: false
  * Nearest DERP: Tokyo
  * DERP latency:
      - tok: 67.3ms  (Tokyo)
      - hkg: 67.8ms  (Hong Kong)
      - sin: 100.2ms (Singapore)
      - blr: 114.5ms (Bengaluru)
      - lax: 140.7ms (Los Angeles)
      - sfo: 143.7ms (San Francisco)
      - sea: 163ms   (Seattle)
      - dfw: 170.4ms (Dallas)
      - den: 174.2ms (Denver)
      - ord: 182.2ms (Chicago)
      - hnl: 194.5ms (Honolulu)
      - iad: 200.9ms (Ashburn)
      - mia: 201.1ms (Miami)
      - nyc: 203.9ms (New York City)
      - tor: 204.8ms (Toronto)
      - ams: 228.3ms (Amsterdam)
      - nue: 234ms   (Nuremberg)
      - fra: 249.5ms (Frankfurt)
      - hel: 250.8ms (Helsinki)
      - dbi: 260.1ms (Dubai)
      - lhr: 271.1ms (London)
      - syd: 272.4ms (Sydney)
      - par: 273.8ms (Paris)
      - mad: 275.1ms (Madrid)
      - waw: 291.4ms (Warsaw)
      - sao: 308.2ms (São Paulo)
      - nai: 403.1ms (Nairobi)
      - jnb: 408.4ms (Johannesburg)
```

---

## Traceroute Results

### derp1 — New York City (159.89.225.99)

```
traceroute to 159.89.225.99 (159.89.225.99), 20 hops max, 40 byte packets
 1  zyxel.home (192.168.1.1)  4.188 ms  6.902 ms  3.076 ms
 2  * * *
 3  168-95-83-54.tpdt-3310.hinet.net (168.95.83.54)  9.459 ms  9.770 ms  26.220 ms
 4  * * *
 5  * * *
 6  220-128-26-185.skc1-4111.hinet.net (220.128.26.185)  13.521 ms
    220-128-27-177.skc1-4112.hinet.net (220.128.27.177)  13.787 ms
    220-128-27-181.skc1-4112.hinet.net (220.128.27.181)  13.807 ms
 7  220-128-31-113.skc1-4012.hinet.net (220.128.31.113)  14.317 ms
    220-128-30-113.skc1-4011.hinet.net (220.128.30.113)  12.901 ms
    220-128-31-105.skc1-4012.hinet.net (220.128.31.105)  12.935 ms
 8  220-128-31-133.skc1-4012.hinet.net (220.128.31.133)  13.627 ms
    202-39-91-29.pa-r32.us.hinet.net (202.39.91.29)  137.747 ms
    220-128-31-133.skc1-4012.hinet.net (220.128.31.133)  13.564 ms
 9  tis-pa-gw.hinet.net (202.39.82.53)  138.380 ms  138.402 ms
    202-39-91-29.pa-r32.us.hinet.net (202.39.91.29)  138.252 ms
10  tis-pa-gw.hinet.net (202.39.82.53)  138.572 ms  137.919 ms  137.910 ms
11  195.22.195.181 (195.22.195.181)  206.734 ms  206.324 ms
    195.22.195.69 (195.22.195.69)  205.919 ms
12  195.22.195.181 (195.22.195.181)  205.332 ms
    195.22.195.69 (195.22.195.69)  212.821 ms  212.204 ms
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
```

**Route:** ZyXEL → HiNet (Taiwan) → tis-pa-gw → Tiscara transit → NYC  
**Latency:** ~206ms at last visible hop, then packet filtering

---

### derp10 — Mumbai (137.220.36.168)

```
traceroute to 137.220.36.168 (137.220.36.168), 20 hops max, 40 byte packets
 1  zyxel.home (192.168.1.1)  2.759 ms  2.644 ms  2.298 ms
 2  * * *
 3  168-95-83-170.tpdt-3310.hinet.net (168.95.83.170)  10.499 ms  8.722 ms  8.450 ms
 4  * * *
 5  220-128-2-189.tpdt-4011.hinet.net (220.128.2.189)  9.776 ms
    220-128-1-189.tpdt-4011.hinet.net (220.128.1.189)  8.990 ms
    220-128-2-241.tpdt-4011.hinet.net (220.128.2.241)  9.635 ms
 6  202-39-91-37.r32-la.us.hinet.net (202.39.91.37)  138.989 ms  138.748 ms  140.832 ms
 7  202-39-84-85.r31-la.us.hinet.net (202.39.84.85)  138.275 ms  139.306 ms  139.470 ms
 8  202-39-82-225.hinet-ip.hinet.net (202.39.82.225)  139.756 ms  138.397 ms  138.982 ms
 9  * bundle-ether44.br04.sea01.as3491.net (63.223.47.122)  167.188 ms  180.848 ms
10  * 63-220-192-226.static.as3491.net (63.220.192.226)  163.766 ms  200.008 ms
11  * * *
12  * * *
13  * * *
14  45.63.33.250.vultrusercontent.com (45.63.33.250)  288.657 ms  166.799 ms  357.001 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
```

**Route:** HiNet → NTT backbone (SEA) → Vultr Mumbai  
**Latency:** High latency spike at end due to Vultr anycast routing

---

### derp5 — Singapore (103.43.75.49)

```
traceroute to 103.43.75.49 (103.43.75.49), 20 hops max, 40 byte packets
 1  * zyxel.home (192.168.1.1)  4.389 ms  13.675 ms
 2  * * *
 3  168-95-83-50.tpdt-3310.hinet.net (168.95.83.50)  9.076 ms  8.945 ms  9.080 ms
 4  * * *
 5  220-128-4-161.tpdt-4123.hinet.net (220.128.4.161)  9.692 ms
    220-128-1-13.tpdt-4123.hinet.net (220.128.1.13)  9.892 ms
    220-128-2-13.tpdt-4123.hinet.net (220.128.2.13)  9.227 ms
 6  220-128-6-233.tpdt-4013.hinet.net (220.128.6.233)  8.701 ms
    220-128-6-245.tpdt-4013.hinet.net (220.128.6.245)  9.073 ms
    220-128-6-225.tpdt-4013.hinet.net (220.128.6.225)  8.564 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  ae-30.a00.sydnau05.au.bb.gin.ntt.net (129.250.2.57)  177.661 ms  179.162 ms  288.668 ms
12  103.13.80.143 (103.13.80.143)  177.417 ms  176.447 ms  197.650 ms
13  * * *
14  * * *
15  103.43.73.237.vultrusercontent.com (103.43.73.237)  176.600 ms  174.396 ms *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
```

**Route:** HiNet → NTT backbone → Vultr Singapore  
**Latency:** Routed through Sydney NTT, adding latency

---

### derp6 — Tokyo (68.183.90.120)

```
traceroute to 68.183.90.120 (68.183.90.120), 20 hops max, 40 byte packets
 1  zyxel.home (192.168.1.1)  3.319 ms * *
 2  * * *
 3  168-95-83-166.tpdt-3310.hinet.net (168.95.83.166)  9.159 ms  11.991 ms  8.198 ms
 4  * * *
 5  220-128-4-161.tpdt-4123.hinet.net (220.128.4.161)  9.385 ms
    220-128-2-109.tpdt-4123.hinet.net (220.128.2.109)  8.777 ms  8.211 ms
 6  220-128-6-225.tpdt-4013.hinet.net (220.128.6.225)  7.773 ms  9.635 ms
    220-128-6-237.tpdt-4013.hinet.net (220.128.6.237)  8.785 ms
 7  211-22-33-177.hinet-ip.hinet.net (211.22.33.177)  35.269 ms  37.353 ms  37.819 ms
 8  * * if-bundle-4-2.qcore2.hk2-hongkong.as6453.net (180.87.168.102)  70.666 ms
 9  * * *
10  if-ae-33-2.tcore2.svw-singapore.as6453.net (180.87.84.128)  62.959 ms  68.508 ms  70.121 ms
11  180.87.84.79 (180.87.84.79)  107.203 ms  103.815 ms  94.808 ms
12  * * *
13  115.111.223.34 (115.111.223.34)  171.506 ms  103.931 ms  106.282 ms
14  et-0-0-8-400.iar2.in-blr1.as14061.net (143.244.225.10)  286.735 ms
    et-0-0-9-400.iar2.in-blr1.as14061.net (143.244.225.14)  100.044 ms
    et-0-0-8-400.iar2.in-blr1.as14061.net (143.244.225.10)  246.881 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
```

**Route:** HiNet → Tata HK → Tata Singapore → Vultr  
**Latency:** Tokyo DERP actually routes through India (Vultr BLR), adding 100ms

---

### derp11 — Los Angeles (18.230.97.74)

```
traceroute to 18.230.97.74 (18.230.97.74), 20 hops max, 40 byte packets
 1  * * zyxel.home (192.168.1.1)  8.168 ms
 2  * * *
 3  168-95-82-50.tpdt-3309.hinet.net (168.95.82.50)  10.474 ms  8.866 ms  8.407 ms
 4  * * *
 5  * * *
 6  220-128-26-173.skc1-4112.hinet.net (220.128.26.173)  16.686 ms
    220-128-27-181.skc1-4112.hinet.net (220.128.27.181)  15.658 ms
    220-128-26-193.skc1-4112.hinet.net (220.128.26.193)  15.243 ms
 7  220-128-30-1.skc1-4011.hinet.net (220.128.30.1)  15.847 ms  15.751 ms
    220-128-31-101.skc1-4012.hinet.net (220.128.31.101)  15.682 ms
 8  202-39-91-29.pa-r32.us.hinet.net (202.39.91.29)  139.073 ms
    220-128-31-133.skc1-4012.hinet.net (220.128.31.133)  13.997 ms
    202-39-91-29.pa-r32.us.hinet.net (202.39.91.29)  139.297 ms
 9  202-39-84-29.pa-r31.us.hinet.net (202.39.84.29)  138.565 ms  139.287 ms
    202-39-91-29.pa-r32.us.hinet.net (202.39.91.29)  138.051 ms
10  202-39-84-29.pa-r31.us.hinet.net (202.39.84.29)  138.239 ms  158.653 ms  137.769 ms
11  * * ae2.3615.edge1.dallas2.net.lumen.tech (4.69.209.110)  178.215 ms
12  ae2.3609.edge2.dallas2.net.lumen.tech (4.69.206.169)  227.684 ms *  375.066 ms
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
```

**Route:** HiNet → Lumen (Dallas) → destination  
**Latency:** Direct US transit, ~178ms

---

### derp12 — Seattle (216.128.144.130)

```
traceroute to 216.128.144.130 (216.128.144.130), 20 hops max, 40 byte packets
 1  * * zyxel.home (192.168.1.1)  4.148 ms
 2  * * *
 3  168-95-83-50.tpdt-3310.hinet.net (168.95.83.50)  9.675 ms  9.179 ms  8.162 ms
 4  * * *
 5  * * *
 6  220-128-27-157.skc1-4111.hinet.net (220.128.27.157)  14.824 ms
    220-128-26-181.skc1-4112.hinet.net (220.128.26.181)  13.787 ms  15.002 ms
 7  220-128-30-117.skc1-4011.hinet.net (220.128.30.117)  14.756 ms
    220-128-30-113.skc1-4011.hinet.net (220.128.30.113)  13.853 ms
    220-128-30-109.skc1-4011.hinet.net (220.128.30.109)  14.269 ms
 8  202-39-91-97.pa-r41.us.hinet.net (202.39.91.97)  143.951 ms
    pa-r32.us.hinet.net (202.39.91.33)  163.861 ms
    202-39-91-97.pa-r41.us.hinet.net (202.39.91.97)  141.763 ms
 9  sjo-b23-link.ip.twelve99.net (62.115.165.50)  140.974 ms
    202-39-84-45.pa-r31.us.hinet.net (202.39.84.45)  140.998 ms
    202-39-84-53.pa-r32.us.hinet.net (202.39.84.53)  147.157 ms
10  palo-b24-link.ip.twelve99.net (62.115.174.130)  142.751 ms
    sjo-bb3-link.ip.twelve99.net (62.115.139.16)  142.213 ms
    palo-b24-link.ip.twelve99.net (62.115.174.130)  142.147 ms
11  palo-bb4-link.ip.twelve99.net (62.115.139.110)  142.698 ms  145.510 ms  144.119 ms
12  den-bb1-link.ip.twelve99.net (62.115.139.105)  175.282 ms  168.999 ms  168.834 ms
13  kanc-bb2-link.ip.twelve99.net (62.115.137.115)  185.469 ms
    kanc-bb2-link.ip.twelve99.net (62.115.140.184)  179.471 ms  179.984 ms
14  chi-bb2-link.ip.twelve99.net (62.115.136.102)  191.046 ms
    constantcompany-ic-382520.ip.twelve99-cust.net (62.115.9.127)  190.188 ms
    chi-b23-link.ip.twelve99.net (62.115.140.109)  199.418 ms
15  constantcompany-ic-382520.ip.twelve99-cust.net (62.115.9.127)  195.249 ms  191.322 ms  296.452 ms
16  * constantcompany-ic-382520.ip.twelve99-cust.net (62.115.9.127)  380.760 ms *
17  * * *
18  * * *
19  * 108.61.101.142.vultrusercontent.com (108.61.101.142)  248.570 ms  199.822 ms
20  * * 108.61.101.142.vultrusercontent.com (108.61.101.142)  199.171 ms
```

**Route:** HiNet → Telia/Twelve99 backbone (Palo Alto → Denver → Kansas City → Chicago) → Vultr Seattle  
**Latency:** 14 hops, very circuitous US backbone traversal

---

## Network Topology Map

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         TAIWAN (Taipei)                                         │
│                                                                                 │
│  ┌──────────────────┐                                                            │
│  │   YOUR DEVICE    │                                                            │
│  │   192.168.1.113  │                                                            │
│  └────────┬─────────┘                                                            │
│           │                                                                      │
│  ┌────────▼─────────┐                                                            │
│  │   ZyXEL Gateway  │                                                            │
│  │   192.168.1.1    │                                                            │
│  └────────┬─────────┘                                                            │
└───────────┼──────────────────────────────────────────────────────────────────────┘
            │
┌───────────▼──────────────────────────────────────────────────────────────────────┐
│                          HiNet (AS3462) - Taiwan ISP                            │
│                                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────────────┐│
│  │ 168.95.83.x  │  Local DNS / Access                                         ││
│  │ 220.128.x.x  │  Internal Routing (TPDT → SKC → TPDT)                      ││
│  │ 202.39.x.x   │  International Peering Points                               ││
│  └─────────────────────────────────────────────────────────────────────────────┘│
│                                                                                 │
│  ┌───────────────────┐  ┌───────────────────┐  ┌───────────────────┐            │
│  │ tis-pa-gw         │  │ r32/r31/r41       │  │ skc1-4xxx         │            │
│  │ 202.39.82.53      │  │ 202.39.91.x       │  │ 220.128.x.x       │            │
│  │ Pacific Gateway   │  │ US Peering        │  │ Local Distribution│            │
│  │ 138ms             │  │ 140-164ms         │  │ 13-17ms           │            │
│  └────────┬──────────┘  └────────┬──────────┘  └───────────────────┘            │
└───────────┼───────────────────────┼──────────────────────────────────────────────┘
            │                       │
            │                       │
┌───────────▼───────────────────────▼──────────────────────────────────────────────┐
│                                                                                 │
│  ┌──────────────────────────────────────────────────────────────────────────┐   │
│  │                                                                          │   │
│  │                    PACIFIC OCEAN CROSSING                               │   │
│  │                    HiNet → Transit Providers                            │   │
│  │                                                                          │   │
│  │  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐                 │   │
│  │  │ NTT/AS3491  │    │ Tata/AS6453 │    │ Lumen/AS3356│                 │   │
│  │  │ 63.223.x.x  │    │ 180.87.x.x  │    │ 4.69.x.x    │                 │   │
│  │  │ 63.220.x.x  │    │             │    │             │                 │   │
│  │  └──────┬──────┘    └──────┬──────┘    └──────┬──────┘                 │   │
│  │         │                  │                  │                         │   │
│  └─────────┼──────────────────┼──────────────────┼─────────────────────────┘   │
│            │                  │                  │                             │
└────────────┼──────────────────┼──────────────────┼─────────────────────────────┘
             │                  │                  │
             │                  │                  │
┌────────────▼──────────────────▼──────────────────▼─────────────────────────────┐
│                                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                        NORTH AMERICA                                    │   │
│  │                                                                         │   │
│  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    │   │
│  │  │ Telia/Twelve99  │    │ Lumen           │    │ Vultr           │    │   │
│  │  │ AS1299          │    │ AS3356          │    │ (Cloud)         │    │   │
│  │  │                 │    │                 │    │                 │    │   │
│  │  │ 62.115.165.50   │    │ 4.69.209.110    │    │ 159.89.225.99   │    │   │
│  │  │ San Jose        │    │ Dallas          │    │ NYC (derp1)     │    │   │
│  │  │ 141ms           │    │ 178ms           │    │ 206ms           │    │   │
│  │  └────────┬────────┘    └────────┬────────┘    └─────────────────┘    │   │
│  │           │                      │                                    │   │
│  │           ▼                      ▼                                    │   │
│  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐   │   │
│  │  │ Palo Alto       │    │ Dallas          │    │ Vultr           │   │   │
│  │  │ 62.115.174.130  │    │ 4.69.206.169    │    │ 18.230.97.74    │   │   │
│  │  │ 142ms           │    │ 228-375ms       │    │ LA (derp11)     │   │   │
│  │  └────────┬────────┘    └─────────────────┘    │ 178ms           │   │   │
│  │           │                                    └─────────────────┘   │   │
│  │           ▼                                                          │   │
│  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐  │   │
│  │  │ Denver          │    │ Kansas City     │    │ Vultr           │  │   │
│  │  │ 62.115.139.105  │    │ 62.115.137.115  │    │ 108.61.101.142  │  │   │
│  │  │ 169-175ms       │    │ 179-185ms       │    │ Seattle (derp12)│  │   │
│  │  └────────┬────────┘    └────────┬────────┘    │ 199ms           │  │   │
│  │           │                      │             └─────────────────┘  │   │
│  │           ▼                      ▼                                  │   │
│  │  ┌─────────────────────────────────────────┐                       │   │
│  │  │ Chicago                                 │                       │   │
│  │  │ 62.115.136.102                          │                       │   │
│  │  │ 191ms                                   │                       │   │
│  │  └─────────────────────────────────────────┘                       │   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
             │
┌────────────▼─────────────────────────────────────────────────────────────────┐
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────────┐│
│  │                          ASIA-PACIFIC                                   ││
│  │                                                                         ││
│  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    ││
│  │  │ Tata/AS6453     │    │ NTT/AS2914      │    │ Vultr           │    ││
│  │  │                 │    │                 │    │ (Cloud)         │    ││
│  │  │ 180.87.168.102  │    │ 129.250.2.57    │    │                 │    ││
│  │  │ Hong Kong       │    │ Sydney          │    │                 │    ││
│  │  │ 71ms            │    │ 177ms           │    │                 │    ││
│  │  └────────┬────────┘    └────────┬────────┘    └─────────────────┘    ││
│  │           │                      │                                    ││
│  │           ▼                      │                                    ││
│  │  ┌─────────────────┐            │                                    ││
│  │  │ Singapore       │            │                                    ││
│  │  │ 180.87.84.128   │            │                                    ││
│  │  │ 63-70ms         │            │                                    ││
│  │  └────────┬────────┘            │                                    ││
│  │           │                      │                                    ││
│  │           ▼                      │                                    ││
│  │  ┌─────────────────┐            │                                    ││
│  │  │ Vultr BLR       │            │                                    ││
│  │  │ 143.244.225.10  │            │                                    ││
│  │  │ 100-287ms       │            │                                    ││
│  │  │ (Tokyo DERP!)   │            │                                    ││
│  │  └─────────────────┘            │                                    ││
│  │                                  │                                    ││
│  │  ┌─────────────────┐            │                                    ││
│  │  │ Vultr SG        │            │                                    ││
│  │  │ 103.43.73.237   │            │                                    ││
│  │  │ 175-177ms       │            │                                    ││
│  │  │ (SG DERP)       │            │                                    ││
│  │  └─────────────────┘            │                                    ││
│  │                                  │                                    ││
│  │  ┌─────────────────┐            │                                    ││
│  │  │ Vultr Mumbai    │            │                                    ││
│  │  │ 45.63.33.250    │◀───────────┘                                    ││
│  │  │ 167-289ms       │                                                 ││
│  │  │ (Mumbai DERP)   │                                                 ││
│  │  └─────────────────┘                                                 ││
│  │                                                                       ││
│  └───────────────────────────────────────────────────────────────────────┘│
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Key Transit Providers

| Provider | AS | Role | Key IPs |
|----------|-----|------|---------|
| **HiNet** | AS3462 | Taiwan ISP | 202.39.x.x, 220.128.x.x |
| **Telia/Twelve99** | AS1299 | Global backbone | 62.115.x.x |
| **NTT** | AS2914/3491 | Global backbone | 63.223.x.x, 129.250.x.x |
| **Tata** | AS6453 | Global backbone | 180.87.x.x |
| **Lumen** | AS3356 | Global backbone | 4.69.x.x |

---

## Notable Findings

1. **Tokyo DERP actually routes to India** — HiNet → Tata HK → Tata SG → Vultr BLR (100ms added)
2. **Seattle DERP goes Chicago** — Telia's full US backbone traversal
3. **Mumbai DERP goes Seattle** — NTT backbone US route before heading to India
4. **SG DERP goes Sydney** — NTT routes through Australia

---

## Summary

Your netreport is consistent with traceroutes:
- **Nearest DERP:** Tokyo (67ms) — but the traceroute shows it actually routes through BLR/Vultr, not direct to Tokyo
- **Hong Kong DERP** (derp5 Singapore): Routes via NTT Sydney → Vultr SG, explaining the 177ms vs expected ~70ms
- **Common bottleneck:** HiNet → US peering point at ~138ms (tis-pa-gw, r32/r31 LA routers) — this is the Pacific crossing
- **Best route:** Tokyo (67ms) is genuinely closest despite suboptimal transit path
- **Seattle DERP:** Goes through Telia's full US backbone (14 hops, 199ms) — very circuitous
