---
title: '[Study/Hackthebox] Network Enumeration with Nmap'
date: 2025-05-19
permalink: /projects/2025/05/002/
collection: projects
tags:
  - nmap
---

#### 📝 Description
<p style="font-size: smaller"></p>

`Nmap Architecture`\
├── Host discovery\
├── Port scanning\
├── Service enumeration and detection\
├── OS detection\
├── Scriptable interaction with the  service (Nmap Scripting Engine)

`Syntax`
```bash
nmap <scan types> <options> <target>
```

`Scan Network Range` with `an IP address`
```bash
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```
👉 10.129.2.0/24: target network range

👉 -sn: disabled port scanning. which means, it scans using ping only to figure out which hosts are active

👉 -oA tnet: Stores the results in all formats starting with the name 'tent'. the result will be stored with 3 types, which are nmap, gnamp, and xml.

👉 | grep for:
👉 | cut -d" " -f5:

`Scan Network Range` with `a file`
```bash
sudo nmap -sn -oA tnet -iL <filename.lst> | grep for | cut -d" " -f5
```
👉 -iL: Performs defined scans against targets in provided 'filename.lst' list

`Scan multiple IPs`
```bash
sudo nmap -sn -oA tnet 192.168.64.1-10 | grep for | cut -d" " -f5
```

`Scan single IP`
```bash
sudo nmap 192.168.64.x -sn -oA host
```
👉 -oA host: Stores the results in all formats starting with the name 'host'

`Host discovery` with `ICMP Echo Request (-PE)` and `--packet-trace`
```bash
sudo nmap 192.168.64.1 -sn -oA host -PE --packet-trace
```
👉 -PE: Performs the ping scan by using 'ICMP Echo requests' against the target

👉 --packet-trace: Shows all packets sent and received

`Host discovery` with `--reason`
```bash
sudo nmap 192.168.64.1 -sn -oA host -PE --reason
```
👉 --reason: Displays the reason for specific result

`Host discovery` with `--disable-arp-ping`
```bash
sudo nmap 192.168.64.1 -sn -oA host -PE --packet-trace --disabl-arp-ping
```
👉 --disabl-arp-ping: Disables ARP pings. For ARP reply without ARP request, it's for disabling ARP requests and scan our target with the desired ICMP echo requests

#### Quiz
According to the below result, find out which operating system it belongs to.
<details>
<summary>See the answer</summary>

✅ Answer: `Windows`

Each OS contains their unique TTL values. From these values, we can assume the target's OS.

| OS         | Default TTL value      | Note                         |
|------------------|------------------|------------------------------|
| **Windows**      | `128`            | 거의 모든 Windows 버전 공통        |
| **Linux**        | `64`             | Ubuntu, CentOS, Kali 등 대부분 |
| **macOS**        | `64`             | BSD 기반                     |
| **Android**      | `64`             | 리눅스 커널 기반                  |
| **iOS**          | `64`             | macOS와 동일 커널               |
| **Cisco 장비**   | `255`            | 스위치/라우터 장비                 |
| **Juniper**      | `64` 또는 `128`   | 장비 설정에 따라 다름               |
| **Solaris**      | `255`            | 오래된 Unix 시스템               |
| **FreeBSD**      | `64`             | macOS와 유사                  |
</details>

1. Background

2. Goal

3. What I Did

4. What I Learned

5. Next Step


#### 💻 Script

#### 📷 Result Screenshots

#### 🎥 Result Video