# Networking Basics in Linux

Networking is one of those things that looks complicated at first, but once you understand the basics, it starts making sense pretty quickly. In Linux, networking is not only about connecting to the internet. It is also about understanding how devices talk to each other, how data moves, and how to check what is happening on your system.

This note is just a simple, human way of understanding networking basics in Linux. Nothing too technical, just the important stuff that helps build a good foundation.

---

## 1. What Networking Actually Means

Networking is basically how computers communicate with each other.

When you open a website, send a file, connect to a server, or even ping another machine, your computer is using networking.

A few basic things are always involved:

- an IP address
- a MAC address
- a port number
- a protocol like TCP or UDP

If you understand these four things, a lot of networking becomes easier.

---

## 2. IP Address

An IP address is like the address of a device on a network.

It helps other devices know where to send data.

There are two common types:

- **IPv4** — looks like `192.168.1.10`
- **IPv6** — looks longer, something like `2001:db8::1`

### Why it matters
If two devices want to communicate, they usually need an IP address so the data goes to the right place.

### Example
A router, laptop, phone, and server can all have their own IP addresses.

---

## 3. MAC Address

A MAC address is the physical address of a network device.

It is assigned to the network interface card, so it is more tied to the hardware than the IP address.

### Example
A MAC address usually looks like this:

    08:00:27:12:ab:4f

### Why it matters
- IP addresses can change
- MAC addresses usually stay the same for the device

So MAC is often used for identifying devices inside a local network.

---

## 4. Public IP vs Private IP

### Public IP
This is the IP visible on the internet.

Your internet service provider usually gives it to your network.

### Private IP
This is used inside a local network like your home Wi-Fi or office network.

Common private IP ranges are:

- `192.168.x.x`
- `10.x.x.x`
- `172.16.x.x` to `172.31.x.x`

### Why it matters
Private IPs are used inside the network, while public IPs are used to communicate outside the network.

---

## 5. Ports

A port is like a door on a computer.

The IP address tells you which machine to reach, and the port tells you which service on that machine you want.

### Example
- Port `22` is usually for SSH
- Port `80` is usually for HTTP
- Port `443` is usually for HTTPS

### Simple way to think about it
- IP address = house address
- Port = room number inside the house

So a device can run many services at the same time, and each service listens on a different port.

---

## 6. TCP and UDP

These are two common ways data is sent over a network.

### TCP
TCP is more reliable.

It checks if data arrives properly and in the correct order.

Use TCP when accuracy matters.

Examples:
- web browsing
- file transfers
- SSH

### UDP
UDP is faster but less reliable.

It sends data without waiting for confirmation every time.

Use UDP when speed matters more than perfect delivery.

Examples:
- video streaming
- online games
- live voice calls

### Easy comparison
- TCP = careful and reliable
- UDP = fast and lightweight

---

## 7. Common Ports You Should Know

These come up a lot in networking and security:

- `20` / `21` — FTP
- `22` — SSH
- `23` — Telnet
- `25` — SMTP
- `53` — DNS
- `67` / `68` — DHCP
- `80` — HTTP
- `110` — POP3
- `143` — IMAP
- `443` — HTTPS
- `445` — SMB
- `3306` — MySQL
- `3389` — RDP

### Why this matters
If you see a service running on a port, you can often guess what it is just by the number.

---

## 8. `ping`

`ping` is one of the first commands people use when checking network connectivity.

It sends small packets to a target and waits for a reply.

### What it tells you
- whether a host is reachable
- how fast the response is
- whether packet loss is happening

### Example

    ping google.com

### What I usually look for
If ping works, it usually means the network path is alive.

If it does not work, there may be a network issue, firewall rule, or the target may not respond to ping.

---

## 9. `ip`

`ip` is one of the most useful Linux networking commands.

It shows information about your network interfaces, addresses, and routes.

### Common uses

    ip a

Shows IP addresses and interfaces.

    ip addr

Same idea as `ip a`.

    ip route

Shows routing information.

### Why it matters
This is one of the first commands to check when you want to know:
- what IP your machine has
- which interface is active
- where your traffic is going

---

## 10. `ifconfig`

`ifconfig` is an older command for checking network information.

It is still seen on some systems, but `ip` is the modern command.

### Example

    ifconfig

### Why it matters
It still appears in older tutorials and systems, so it is good to recognize it.

---

## 11. `netstat`

`netstat` shows network connections, listening ports, and related details.

### Example

    netstat -tuln

### What it means
- `-t` = TCP
- `-u` = UDP
- `-l` = listening services
- `-n` = show numeric addresses and ports

### Why it matters
This is useful when you want to see what ports are open on a system.

---

## 12. `ss`

`ss` is like a modern replacement for `netstat`.

It is faster and often preferred on newer Linux systems.

### Example

    ss -tuln

### What it shows
- TCP listening ports
- UDP listening ports
- active sockets

### Why it matters
If you are checking open services, `ss` is one of the best commands to know.

---

## 13. `hostname`

`hostname` shows the name of the machine.

### Example

    hostname

### Why it matters
It helps identify which system you are on, especially when working with multiple machines.

You can also use:

    hostname -I

This shows the IP address assigned to the machine.

---

## 14. `curl`

`curl` is used to fetch data from URLs.

It is very useful for testing websites, APIs, and simple connectivity.

### Examples

    curl https://example.com

    curl -O https://example.com/file.txt

### What it does
- First example: downloads and prints the content of a page
- Second example: downloads a file and saves it

### Why it matters
It is very useful when you want to test if a server is responding properly.

---

## 15. `wget`

`wget` is another tool for downloading files from the internet.

### Example

    wget https://example.com/file.txt

### Why it matters
It is simple and useful when you just want to download something quickly.

---

## 16. `dig`

`dig` is used to check DNS information.

DNS is what turns names like `google.com` into IP addresses.

### Example

    dig google.com

### Why it matters
If a website name is not working, DNS might be the problem. `dig` helps you check that.

---

## 17. `nslookup`

`nslookup` is another DNS lookup command.

### Example

    nslookup google.com

### Why it matters
It is useful for checking what IP address a domain name points to.

---

## 18. `traceroute`

`traceroute` shows the path packets take to reach a destination.

### Example

    traceroute google.com

### Why it matters
If a network connection is slow or failing, `traceroute` can help you see where the problem might be.

It shows each hop along the way, so you can understand how traffic moves.

---

## 19. `whois`

`whois` gives information about a domain or IP registration.

### Example

    whois example.com

### Why it matters
It can show details like:
- domain owner info
- registrar details
- registration dates

This is often used in investigation and security work.

---

## 20. `arp`

`arp` is related to the mapping between IP addresses and MAC addresses on a local network.

### Example

    arp -a

### Why it matters
It helps you see which MAC address is connected to which IP on your local network.

---

## 21. `route`

`route` shows routing tables on a system.

### Example

    route -n

### Why it matters
Routing tells the system where to send traffic.

It is useful when a machine is not reaching the network the way it should.

---

## 22. `nmcli`

`nmcli` is a command-line tool for NetworkManager.

### Example

    nmcli device status
    nmcli connection show

### Why it matters
It helps manage network connections directly from the terminal.

This is useful when working on Linux servers or systems without a graphical interface.

---

## 23. Network Interfaces

A network interface is the part of your system that connects to the network.

Examples:
- Ethernet
- Wi-Fi
- virtual interfaces
- loopback interface

### Loopback Interface
The loopback interface is usually `127.0.0.1`.

It is used when a system talks to itself.

### Example
If you open a local service on your machine and connect to `127.0.0.1`, you are not going outside the computer.

---

## 24. The Loopback Address

`127.0.0.1` is the most common loopback address.

It is also called `localhost`.

### Why it matters
It is used for testing services locally.

For example, if a web server is running on your own machine, you might open:

    http://127.0.0.1

or

    http://localhost

---

## 25. Basic Network Troubleshooting

When the internet is not working, I usually check things in this order:

1. Is the cable or Wi-Fi connected?
2. Does the machine have an IP address?
3. Can I ping the router?
4. Can I ping a public IP?
5. Can I open a domain name?
6. Is DNS working?
7. Is a firewall blocking anything?

### Useful commands for checking

    ip a
    ping 8.8.8.8
    ping google.com
    ss -tuln
    netstat -tuln
    dig google.com

### Simple idea
- If `ping 8.8.8.8` works but `ping google.com` does not, DNS may be the problem.
- If nothing works, the issue may be network access, routing, or firewall settings.

---

## 26. Common Service Ports in Security

These are worth remembering because they show up a lot:

- `22` — SSH remote login
- `80` — web traffic
- `443` — secure web traffic
- `53` — DNS
- `445` — file sharing
- `3389` — remote desktop

### Why security people care
Open ports can tell you what services are running on a machine.

That is why port checking is such a big part of security and system administration.

---

## 27. A Few Useful Commands Together

These are simple but very practical:

    ip a
    ip route
    ping google.com
    ss -tuln
    netstat -tuln
    hostname -I
    curl https://example.com
    dig google.com
    traceroute google.com

---

## Final Thoughts

Networking in Linux is not something you understand perfectly in one day. It takes a bit of time, but once the basics are clear, it becomes much easier to deal with servers, tools, and security tasks.

For now, just remember the main idea:

- IP address tells you which machine
- port tells you which service
- TCP and UDP tell you how data is sent
- commands like `ping`, `ip`, `ss`, `curl`, and `dig` help you check what is happening

That is enough to build a strong base.