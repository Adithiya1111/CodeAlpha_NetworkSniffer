🎯 Objective/Purpose

1)To capture and inspect live network traffic.

2)To analyze how protocols like IP, TCP, UDP, and ICMP behave.

3)To learn how to extract useful data like source/destination IPs, protocol types, and payloads.

4)To use Python libraries to implement a basic version of tools like Wireshark.

⚙️ Tools & Libraries Used
Python: Programming language.

Tkinter: For creating the GUI.

Scapy: For capturing and parsing network packets.

threading: To run the sniffer without freezing the GUI.

🧱 How It Works
User Interface (Tkinter)

Two buttons: Start Sniffing and Stop Sniffing.

A scrollable text box to display captured packet data in real-time.

Packet Sniffing (Scapy)

Uses scapy.sniff() to listen for IP packets on the network.

Extracts key details:

Source IP

Destination IP

Protocol (ICMP, TCP, UDP, or others)

First 20 bytes of the packet payload

Multithreading

Sniffing runs in a background thread to prevent the GUI from freezing.

A global sniffing flag controls when to start/stop sniffing.

This project is a Python-based network sniffer application with a graphical user interface, designed to capture and analyze 
real-time network traffic. It utilizes the Scapy library for low-level packet inspection and Tkinter for the GUI. The tool displays
essential packet details such as source and destination IP addresses, protocol types (TCP, UDP, ICMP), and a snippet of the payload.
It features start and stop controls for user-managed packet capture, offering a simple yet powerful introduction to network monitoring 
and protocol analysis.

🛰️ Where Do the Source and Destination IPs Come From?
The source (src) and destination (dst) IP addresses are captured directly from the IP headers of packets traveling across the network interface of your computer.

🔍 Here's how it works in detail:
Scapy listens to network traffic using your system's network interface (e.g., Wi-Fi or Ethernet).

Every packet on the network contains a network layer header — typically an IPv4 header in this case.

When a packet is captured, Scapy checks if it contains an IP layer:


if IP in packet:
If so, it extracts the source and destination IPs from the IP header:


ip_layer = packet[IP]
src = ip_layer.src  # Source IP
dst = ip_layer.dst  # Destination IP
📡 What Kind of Traffic Does It Capture?
It captures any IP-based traffic visible to your machine's network interface, which includes:

Packets sent by your computer (e.g., browsing the web).

Packets received by your computer (e.g., incoming data from servers).

Possibly, local network traffic between other devices (if your network supports promiscuous mode).

🧪 Example
Suppose your machine sends a request to Google DNS (8.8.8.8). The sniffer might capture:

Src: 192.168.1.5 | Dst: 8.8.8.8 | Proto: UDP | Payload: ...

And the response:

Src: 8.8.8.8 | Dst: 192.168.1.5 | Proto: UDP | Payload: ...

🧠 Key Skills and Knowledge You'll Gain
1. How Network Communication Works
Understand the structure of network packets (Ethernet, IP, TCP/UDP).

Learn how data moves from one computer to another via the internet or local network.

2. Using Python for Network Programming
Work with libraries like scapy and socket to capture and inspect real-time traffic.

Learn to write scripts that interact with low-level network protocols.

3. Packet Analysis
Identify key packet fields: source/destination IPs, ports, payloads, and protocol types.

Learn the difference between protocols like TCP, UDP, ICMP, etc.

4. Network Security Fundamentals
See how unencrypted data can be inspected on a network.

Gain insight into how intrusion detection systems (IDS) and packet sniffers work.

Understand how hackers might capture sensitive data and how to defend against it.

5. Debugging and Monitoring Network Issues
Use packet data to troubleshoot connection problems.

Spot irregular or suspicious traffic patterns.

🧰 Practical Experience
By doing this task, you’ll:

Build your own mini-Wireshark in Python.

See live packet data as it travels across your network.

Strengthen your understanding of network layers from theory to code.


Need to Install: pip install scapy

Run Command: python network_sniffer.py
