# CCNA 200-301 v1.1 Study Plan

**Exam:** Thu 8 Oct 2026, 2:00 PM AEST
**Exam version:** v1.1. v1.1 runs until 2 Feb 2027 and v2.0 starts 3 Feb 2027. The v2 syllabus file in the repo does NOT apply to this exam.
**Last updated:** Wed 23 Sep 2026

---

## Status (updated each check-in)

| Metric | Value |
| :--- | :--- |
| Days left (incl. today, excl. exam day) | 15 |
| Work remaining (course + practice exams) | ~43h |
| Required pace | ~2.9h/day |
| Actual pace so far (16–23 Sep) | ~1.3h/day |
| Gap | Need ~2.2x current pace |

**"How behind am I"** = (hours of work remaining) ÷ (days left), compared with the hours you're actually logging per day.

---

## Daily plan

Times are estimates. Pre-assessments are skipped throughout.

### Wed 23 Sep: Finish Module 2 (~2h40m)
- [ ] M2: Starting a Switch
- [ ] M2: Explaining Wireless Fundamentals
- [ ] M2: Post-Assessment
- [ ] Carry-over, M1: Introducing the Host-to-Host Communications Model

### Thu 24 Sep: Module 3, part 1 (~2h30m)
- [ ] M3: Introducing the TCP/IP Internet Layer, IPv4 Addressing, and Subnets
- [ ] Subnetting drills, 45m (HIGH PRIORITY, heavily tested)

### Fri 25 Sep: Module 3, part 2 (~2h50m)
- [ ] M3: Explaining the TCP/IP Transport Layer and Application Layer (skim; focus on TCP vs UDP and port numbers)
- [ ] M3: Configuring a Cisco Router
- [ ] M3: Introducing Basic IPv6 (focus on address types and EUI-64)
- [ ] M3: Post-Assessment
- [ ] Subnetting drills, 15m

### Sat 26 Sep: Module 4, part 1 (~2h)
- [ ] M4: Implementing VLANs and Trunks
- [ ] M4: Routing between VLANs
- [ ] Subnetting/IPv6 drills, 30m

### Sun 27 Sep: Module 4, part 2 (~2h05m)
- [ ] M4: Building Redundant Switched Topology (STP, HIGH PRIORITY)
- [ ] M4: Improving Redundant Switched Topologies with EtherChannel
- [ ] M4: Post-Assessment
- [ ] ExSim: Network Access domain questions, 30m

### Mon 28 Sep: Module 5 (~2h50m)
- [ ] M5: Exploring the Functions of Routing
- [ ] M5: Exploring the Packet Delivery Process
- [ ] M5: Troubleshooting a Simple Network
- [ ] M5: Post-Assessment
- [ ] Routing-table drill: longest prefix match, AD, metric (20m)

### Tue 29 Sep: Module 6, part 1 (~2h30m)
- [ ] M6: Configuring Static Routing (incl. floating static, default, host routes)
- [ ] M6: Introducing OSPF (first half)
- [ ] ExSim: IP Connectivity domain questions, 30m

### Wed 30 Sep: Module 6, part 2 (~2h40m)
- [ ] M6: Introducing OSPF (finish; DR/BDR, router ID, neighbor adjacencies)
- [ ] M6: Exploring Layer 3 Redundancy (skim, describe-level only)
- [ ] M6: Post-Assessment
- [ ] OSPF config/verify lab, 45m
- [ ] ExSim: Network Fundamentals domain questions, 30m

### Thu 1 Oct: Module 7 (~3h15m)
- [ ] M7: Explaining Basics of ACLs (full, HIGH PRIORITY) plus ACL lab, 30m
- [ ] M7: Examining the Security Threat Landscape (skim)
- [ ] M7: Implementing Threat Defense Technologies (skim)
- [ ] M7: Post-Assessment

### Fri 2 Oct: Module 8 + NAT (~3h15m)
- [ ] M8: Securing Administrative Access
- [ ] M8: Implementing Device Hardening (full: port security, DHCP snooping, DAI)
- [ ] M8: Post-Assessment
- [ ] M9: Enabling Internet Connectivity (NAT/PAT and DHCP, HIGH PRIORITY)

### Sat 3 Oct: Module 10 (~3h30m)
- [ ] M10: Introducing System Monitoring (syslog levels, SNMP, NTP)
- [ ] M10: Managing Cisco Devices
- [ ] M10: Introducing Network Programmability (REST, JSON, Ansible/Terraform)
- [ ] M10: Post-Assessment

### Sun 4 Oct: Module 11 + Module 9 skims (~3h35m)
- [ ] M11: Introducing Architectures and Virtualization (skim; VMs, containers, VRFs, cloud)
- [ ] M11: Explaining Software-Defined Networking (control/data plane, APIs)
- [ ] M11: Introducing AI and ML in Network Operations (skim)
- [ ] M11: Post-Assessment
- [ ] M9: Introducing WAN Technologies (skim)
- [ ] M9: Introducing QoS (skim, PHB terms only)
- [ ] M9: Post-Assessment

### Mon 5 Oct: Practice Exam 1 (~3h30m)
- [ ] ExSim Practice Exam 1 (timed, 120 min)
- [ ] Review every wrong answer; log weak topics in revisionareas.md

### Tue 6 Oct: Practice Exam 2 (~3h30m)
- [ ] ExSim Practice Exam 2 (timed)
- [ ] Review wrong answers and update revisionareas.md

### Wed 7 Oct: Weak areas + buffer (~2h30m)
- [ ] 31 Days: revise only the weak topics from revisionareas.md (see hard topics below)
- [ ] Retake M1 Post-Assessment (last score 9/18)
- [ ] Early night

### Thu 8 Oct: EXAM DAY
- [ ] Morning warm-up, max 1h: 10 subnetting questions, AD values, port numbers, syslog levels
- [ ] Exam at 2:00 PM AEST

---

## 31 Days textbook: high-value / high-fail topics only

Use these for revision on 7 Oct or whenever a practice score is weak:
- Subnetting and VLSM
- IPv6 addressing (types, EUI-64, prefix)
- Routing table interpretation (longest prefix, AD, metric) and static/floating static routes
- OSPFv2 (neighbors, DR/BDR, router ID, point-to-point vs broadcast)
- STP / Rapid PVST+ (root election, port roles/states, PortFast, BPDU guard)
- EtherChannel (LACP)
- ACLs (standard vs extended, placement, wildcard masks)
- NAT/PAT
- Layer 2 security (port security, DHCP snooping, DAI)

---

## Skipped / skimmed content (come back if time allows)

About 5h25m saved. These are low-weight or describe-level topics on v1.1.

| Item | Treatment | Time saved |
| :--- | :--- | :--- |
| All module Pre-Assessments | Skipped | ~1h30m |
| M3 Transport/Application Layer | Skimmed | ~10m |
| M6 Exploring Layer 3 Redundancy (FHRP) | Skimmed | ~25m |
| M7 Security Threat Landscape | Skimmed | ~45m |
| M7 Threat Defense Technologies | Skimmed | ~30m |
| M9 Introducing WAN Technologies | Skimmed | ~35m |
| M9 Introducing QoS | Skimmed | ~30m |
| M11 Architectures and Virtualization | Skimmed | ~30m |
| M11 AI and ML in Network Operations | Skimmed | ~30m |

---

## Catch-up rules

- **Missed a day:** spread its items across the next 3 days. 7 Oct is the buffer.
- **Ahead of plan:** pull the next day's items forward. Use freed time on 3rd or more ExSim exam papers and mock CCNA exams. Only go through skimed content as last resort and briefly touch on them.
- **Never cut:** subnetting, OSPF, STP, ACLs, NAT, the 2 practice exams.
- **If desperate:** cut the M11 and M9 skims first, then the M7 skims.
