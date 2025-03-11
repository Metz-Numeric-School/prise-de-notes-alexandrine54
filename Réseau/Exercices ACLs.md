

#### Exercices :


# Part 1: Verify Local Connectivity and Test Access Control List
Step 1: Ping devices on the local network to verify connectivity.
a.     From the command prompt of PC1, ping PC2.
oui ça ping 

b.     From the command prompt of PC1, ping PC3.
oui ça ping

Question:
Why were the pings successful?
Dans le routeur : show run
access-list 11 deny 192.168.10.0 0.0.0.255
access-list 11 permit any


Step 2: Ping devices on remote networks to test ACL functionality.
a.     From the command prompt of PC1, ping PC4.
non ça ping pas

b.     From the command prompt of PC1, ping the DNS Server.
non ping pas non plus

Question:
Why did the pings fail? (Hint: Use simulation mode or view the router configurations to investigate.)

l'information reste dans le réseau 1, cela ne passe pas après le routeur
router ospf 1 log-adjacency-changes
(network 10.10.1.0 0.0.0.3 area 0
network 10.10.1.4 0.0.0.3 area 0
network 192.168.10.0 0.0.0.255 area 10
network 192.168.11.0 0.0.0.255 area 11)

network 10.10.1.0 0.0.0.3 area 0)
en gros y a pas la meme confi
du coup ca marche pas


### Part 2: Remove the ACL and Repeat the Test
Step 1: Use show commands to investigate the ACL configuration.
a.     Navigate to R1 CLI. Use the show run and show access-lists commands to view the currently configured ACLs. To quickly view the current ACLs, use show access-lists. Enter the show access-lists command, followed by a space and a question mark (?) to view the available options:

R1#show access-lists ?

<1-199> ACL number

WORD ACL name

| Output Modifiers

cr

If you know the ACL number or name, you can filter the show output further. However, R1 only has one ACL; therefore, the show access-lists command will suffice.

R1#show access-lists

Standard IP access list 11

10 deny 192.168.10.0 0.0.0.255

20 permit any


Step 2: Remove access list 11 from the configuration.
You can remove ACLs from the configuration by issuing the no access list [number of the ACL] command. The no access-list command when used without arguments deletes all ACLs configured on the router. The no access-list [number of the ACL] command removes only a specific ACL. Removing an ACL from a router does not remove the ACL from the interface. The command that applies the ACL to the interface must be removed separately.

a.     Under the Serial0/0/0 interface, remove access-list 11, which was previously applied to the interface as an outgoing filter:

R1(config)# interface s0/0/0

R1(config-if)# no ip access-group 11 out

b.     In global configuration mode, remove the ACL by entering the following command:

R1(config)# no access-list 11

c.     Verify that PC1 can now ping the DNS Server and PC4.
c'est bon ça marche 


![[Pasted image 20250305110245.png]]

## Part 1: Plan an ACL Implementation
Step 1: Investigate the current network configuration.
Before applying any ACLs to a network, it is important to confirm that you have full connectivity. Verify that the network has full connectivity by choosing a PC and pinging other devices on the network. You should be able to successfully ping every device.

PC1 ping avec PC2 et 3 et aussi avec le Webserver

Step 2: Evaluate two network policies and plan ACL implementations.
a.     The following network policies are implemented on R2:

·         The 192.168.11.0/24 network is not allowed access to the WebServer on the 192.168.20.0/24 network.

·         All other access is permitted.

To restrict access from the 192.168.11.0/24 network to the WebServer at 192.168.20.254 without interfering with other traffic, an ACL must be created on R2. The access list must be placed on the outbound interface to the WebServer. A second rule must be created on R2 to permit all other traffic.

### Part 2: Configure, Apply, and Verify a Standard ACL
Step 1: Configure and apply a numbered standard ACL on R2.
a.     Create an ACL using the number 1 on R2 with a statement that denies access to the 192.168.20.0/24 network from the 192.168.11.0/24 network.

Open configuration window

R2(config)# access-list 1 deny 192.168.11.0 0.0.0.255

b.     By default, an access list denies all traffic that does not match any rules. To permit all other traffic, configure the following statement:

R2(config)# access-list 1 permit any

c.     Before applying an access list to an interface to filter traffic, it is a best practice to review the contents of the access list, in order to verify that it will filter traffic as expected.

R2# show access-lists

Standard IP access list 1

10 deny 192.168.11.0 0.0.0.255

20 permit any

d.     For the ACL to actually filter traffic, it must be applied to some router operation. Apply the ACL by placing it for outbound traffic on the GigabitEthernet 0/0 interface. Note: In an actual operational network, it is not a good practice to apply an untested access list to an active interface.

R2(config)# interface GigabitEthernet0/0

R2(config-if)# ip access-group 1 out

Après avoir fait toutes commandes nous avons bien une ACL qui interdit la communication entre   192.168.11.0/24 network is not allowed access to the WebServer on the 192.168.20.0/24 network.
Mais tout les autres accès sont permis. 


### Step 2: Configure and apply a numbered standard ACL on R3.
a.     Create an ACL using the number 1 on R3 with a statement that denies access to the 192.168.30.0/24 network from the PC1 (192.168.10.0/24) network.

R3(config)# access-list 1 deny 192.168.10.0 0.0.0.255

b.     By default, an ACL denies all traffic that does not match any rules. To permit all other traffic, create a second rule for ACL 1.

R3(config)# access-list 1 permit any

c.     Verify that the access list is configured correctly.

R3# show access-lists

Standard IP access list 1

10 deny 192.168.10.0 0.0.0.255

20 permit any

d.     Apply the ACL by placing it for outbound traffic on the GigabitEthernet 0/0 interface.

R3(config)# interface GigabitEthernet0/0

R3(config-if)# ip access-group 1 out

Step 3: Verify ACL configuration and functionality.Step 3: Verify ACL configuration and functionality.
a.     Enter the show run or show ip interface gigabitethernet 0/0 command to verify the ACL placements.

b.     With the two ACLs in place, network traffic is restricted according to the policies detailed in Part 1. Use the following tests to verify the ACL implementations:

·         A ping from 192.168.10.10 to 192.168.11.10 succeeds.

·         A ping from 192.168.10.10 to 192.168.20.254 succeeds.

·         A ping from 192.168.11.10 to 192.168.20.254 fails.

·         A ping from 192.168.10.10 to 192.168.30.10 fails.

·         A ping from 192.168.11.10 to 192.168.30.10 succeeds.

·         A ping from 192.168.30.10 to 192.168.20.254 succeeds.

J'ai réussi tous ces test avec succès

![[Pasted image 20250305110325.png]]

### Part 1: Configure and Apply a Named Standard ACL
Step 1: Verify connectivity before the ACL is configured and applied.
All three workstations should be able to ping both the Web Server and File Server.

Step 2: Configure a named standard ACL.
Open configuration window

a.     Configure the following named ACL on R1.

R1(config)# ip access-list standard File_Server_Restrictions

R1(config-std-nacl)# permit host 192.168.20.4

R1(config-std-nacl)# permit host 192.168.100.100

R1(config-std-nacl)# deny any

Note: For scoring purposes, the ACL name is case-sensitive, and the statements must be in the same order as shown.

b.     Use the show access-lists command to verify the contents of the access list before applying it to an interface. Make sure you have not mistyped any IP addresses and that the statements are in the correct order.

R1# show access-lists

Standard IP access list File_Server_Restrictions

10 permit host 192.168.20.4

20 permit host 192.168.100.100

30 deny any

Step 3: Apply the named ACL.
a.     Apply the ACL outbound on the Fast Ethernet 0/1 interface.

Note: In an actual operational network, applying an access list to an active interface is not a good practice and should be avoided if possible.

R1(config-if)# ip access-group File_Server_Restrictions out

b.     Save the configuration.

Close configuration window

### Part 2: Verify the ACL Implementation
Step 1: Verify the ACL configuration and application to the interface.
Open configuration window

Use the show access-lists command to verify the ACL configuration. Use the show run or show ip interface fastethernet 0/1 command to verify that the ACL is applied correctly to the interface.

Step 2: Verify that the ACL is working properly.
All three workstations should be able to ping the Web Server, but only PC1 and the Web Server should be able to ping the File Server. Repeat the show access-lists command to see the number of packets that matched each statement.


![[Pasted image 20250305111045.png]]




### Part 1: Verify Connectivity
#### In Part 1, you verify connectivity between devices.

Note: It is very important to test whether connectivity is working before you configure and apply access lists. You want to be sure that your network is properly functioning before you start to filter traffic.

Questions:
From PC-A, ping PC-C and PC-D. Were your pings successful?
ça ping 
From R1, ping PC-C and PC-D. Were your pings successful?
ça ping
From PC-C, ping PC-A and PC-B. Were your pings successful?
ça ping
From R3, ping PC-A and PC-B. Were your pings successful?
ça ping 
Can all of the PCs ping the server at 209.165.200.254?
oui tout marche

#### Part 2: Configure and Verify Standard Numbered and Named ACLs
Step 1: Configure a numbered standard ACL.
Standard ACLs filter traffic based on the source IP address only. A typical best practice for standard ACLs is to configure and apply the ACL as close to the destination as possible. For the first access list in this activity, create a standard numbered ACL that allows traffic from all hosts on the 192.168.10.0/24 network and all hosts on the 192.168.20.0/24 network to access all hosts on the 192.168.30.0/24 network. The security policy also states that an explicit deny any access control entry (ACE), also referred to as an ACL statement, should be present at the end of all ACLs.

Questions:
What wildcard mask would you use to allow all hosts on the 192.168.10.0/24 network to access the 192.168.30.0/24 network?

0.0.0.255

Following Cisco’s recommended best practices, on which router would you place this ACL?

On which interface would you place this ACL? In what direction would you apply it?

a.     Configure the ACL on R3. Use 1 for the access list number.

Open configuration window

R3(config)# access-list 1 remark Allow R1 LANs Access

R3(config)# access-list 1 permit 192.168.10.0 0.0.0.255

R3(config)# access-list 1 permit 192.168.20.0 0.0.0.255

R3(config)# access-list 1 deny any

b.     Apply the ACL to the appropriate interface in the proper direction.

R3(config)# interface g0/0/0

R3(config-if)# ip access-group 1 out

c.     Verify a numbered ACL.

The use of various show commands can help you to verify both the syntax and placement of your ACLs in your router.

Questions:
To see access list 1 in its entirety with all ACEs, which command would you use?

What command would you use to see where the access list was applied and in what direction?

1)    On R3, issue the show access-lists 1 command.

R3# show access-list 1

Standard IP access list 1

permit 192.168.10.0, wildcard bits 0.0.0.255

permit 192.168.20.0, wildcard bits 0.0.0.255

deny any

1)    On R3, issue the show ip interface g0/0/0 command.

R3# show ip interface g0/0/0

GigabitEthernet0/0/0 is up, line protocol is up (connected)

Internet address is 192.168.30.1/24

Broadcast address is 255.255.255.255

Address determined by setup command

MTU is 1500 bytes

Helper address is not set

Directed broadcast forwarding is disabled

Outgoing access list is 1

Inbound access list is not set

'Output omitted' Questions:

3)    Test the ACL to see if it allows traffic from the 192.168.10.0/24 network to access the 192.168.30.0/24 network.
	oui tout marche 
From the PC-A command prompt, ping the PC-C IP address. Were the pings successful?
ça ping 
4)    Test the ACL to see if it allows traffic from the 192.168.20.0/24 network access to the 192.168.30.0/24 network.
	oui ça ping 
From the PC-B command prompt, ping the PC-C IP address. Were the pings successful?

5)    Should pings from PC-D to PC-C be successful? Ping from PC-D to PC-C to verify your answer.
	ça marche pas

d.     From the R1 prompt, ping PC-C’s IP address again.
ça ping pas

R1# ping 192.168.30.3

Question:
Was the ping successful? Explain.

e.     Issue the show access-lists 1 command again. Note that the command output displays information for the number of times each ACE was matched by traffic that reached interface Gigabit Ethernet 0/0/0.

R3# show access-lists 1

Standard IP access list 1

permit 192.168.10.0 0.0.0.255 (4 match(es))

permit 192.168.20.0 0.0.0.255 (4 match(es))

deny any (4 match(es))

Step 2: Configure a named standard ACL.
Create a named standard ACL that conforms to the following policy: allow traffic from all hosts on the 192.168.40.0/24 network access to all hosts on the 192.168.10.0/24 network. Also, only allow host PC-C access to the 192.168.10.0/24 network. The name of this access list should be called BRANCH-OFFICE-POLICY.

Questions:
Following Cisco’s recommended best practices, on which router would you place this ACL?

On which interface would you place this ACL? In what direction would you apply it?

a.     Create the standard named ACL BRANCH-OFFICE-POLICY on R1.

R1(config)# ip access-list standard BRANCH-OFFICE-POLICY

R1(config-std-nacl)# permit host 192.168.30.3

R1(config-std-nacl)# permit 192.168.40.0 0.0.0.255

R1(config-std-nacl)# end

R1#

*Feb 15 15:56:55.707: %SYS-5-CONFIG_I: Configured from console by console

Question:
Look at the first ACE in the access list. What is another way to write this?

b.     Apply the ACL to the appropriate interface in the proper direction.

R1# config t

R1(config)# interface g0/0/0

R1(config-if)# ip access-group BRANCH-OFFICE-POLICY out

c.     Verify a named ACL.

1)    On R1, issue the show access-lists command.

R1# show access-lists

Standard IP access list BRANCH-OFFICE-POLICY

10 permit host 192.168.30.3

20 permit 192.168.40.0 0.0.0.255

Question:
Is there any difference between this ACL on R1 and the ACL on R3? If so, what is it?

![[Pasted image 20250305114716.png]]

1)    On R1, issue the show ip interface g0/0/0 command to verify that the ACL is configured on the interface.

R1# show ip interface g0/0/0

GigabitEthernet0/0/0 is up, line protocol is up (connected)

Internet address is 192.168.10.1/24

Broadcast address is 255.255.255.255

Address determined by setup command

MTU is 1500 bytes

Helper address is not set

Directed broadcast forwarding is disabled

Outgoing access list is BRANCH-OFFICE-POLICY

Inbound access list is not set

'Output omitted' Question:

Test the ACL. From the command prompt on PC-C, ping the IP address of PC-A. Were the pings successful?
oui 

1)    Test the ACL to ensure that only the PC-C host is allowed access to the 192.168.10.0/24 network. You must do an extended ping and use the G0/0/0 address on R3 as your source. Ping PC-A’s IP address.

R3# ping

Protocol [ip]:

Target IP address: 192.168.10.3

Repeat count [5]:

Datagram size [100]:

Timeout in seconds [2]:

Extended commands [n]: y

Source address or interface: 192.168.30.1

Type of service [0]:

Set DF bit in IP header? [no]:

Validate reply data? [no]:

Data pattern [0xABCD]:

Loose, Strict, Record, Timestamp, Verbose[none]:

Sweep range of sizes [n]:

Type escape sequence to abort.

Sending 5, 100-byte ICMP Echos to 192.168.10.3, timeout is 2 seconds:

Packet sent with a source address of 192.168.30.1

U.U.U
non 
Question:
Were the pings successful?

1)    Test the ACL to see if it allows traffic from the 192.168.40.0/24 network access to the 192.168.10.0/24 network. From the PC-D command prompt, ping the PC-A IP address.

Question:
Were the pings successful?
oui

Step 1: Modify a named standard ACL.
a.     From R1, issue the show access-lists command.

Open configuration window

R1# show access-lists

Standard IP access list BRANCH-OFFICE-POLICY

10 permit 192.168.30.3 (8 matches)

20 permit 192.168.40.0 0.0.0.255 (5 matches)

b.     Add two additional lines at the end of the ACL. From global config mode, modify the ACL, BRANCH-OFFICE-POLICY.

R1#(config)# ip access-list standard BRANCH-OFFICE-POLICY

R1(config-std-nacl)# 30 permit 209.165.200.224 0.0.0.31

R1(config-std-nacl)# 40 deny any

R1(config-std-nacl)# end

c.     Verify the ACL.

1)    On R1, issue the show access-lists command.

R1# show access-lists

Standard IP access list BRANCH-OFFICE-POLICY

10 permit 192.168.30.3 (8 matches)

20 permit 192.168.40.0, wildcard bits 0.0.0.255 (5 matches)

30 permit 209.165.200.224, wildcard bits 0.0.0.31

40 deny any

Question:
Do you have to apply the BRANCH-OFFICE-POLICY to the G0/1 interface on R1?


1)    Test the ACL to see if it allows traffic from the 209.165.200.224/27 network access to return to the 192.168.10.0/24 network. From PC-A, ping the server at 209.165.200.254.

Question:
Were the pings successful?
yes

![[Pasted image 20250305115902.png]]


### Part 1: Configure, Apply and Verify an Extended Numbered ACL
#### Step 1: Configure an ACL to permit FTP and ICMP from PC1 LAN.
a.     From global configuration mode on R1, enter the following command to determine the first valid number for an extended access list.

Open configuration window

R1(config)# access-list ?

<1-99> IP standard access list

<100-199> IP extended access list

b.     Add 100 to the command, followed by a question mark.

R1(config)# access-list 100 ?

deny Specify packets to reject

permit Specify packets to forward

remark Access list entry comment

c.     To permit FTP traffic, enter permit, followed by a question mark.

R1(config)# access-list 100 permit ?

ahp Authentication Header Protocol

eigrp Cisco's EIGRP routing protocol

esp Encapsulation Security Payload

gre Cisco's GRE tunneling

icmp Internet Control Message Protocol

ip Any Internet Protocol

ospf OSPF routing protocol

tcp Transmission Control Protocol

udp User Datagram Protocol

d.     When configured and applied, this ACL should permit FTP and ICMP. ICMP is listed above, but FTP is not. This is because FTP is an application layer protocol that uses TCP at the transport layer. Enter TCP to further refine the ACL help.

R1(config)# access-list 100 permit tcp ?

A.B.C.D Source address

any Any source host

host A single source host

e.     The source address can represent a single device, such as PC1, by using the host keyword and then the IP address of PC1. Using the keyword any permits any host on any network. Filtering can also be done by a network address. In this case, it is any host that has an address belonging to the 172.22.34.64/27 network. Enter this network address, followed by a question mark.

R1(config)# access-list 100 permit tcp 172.22.34.64 ?

A.B.C.D Source wildcard bits

f.      Calculate the wildcard mask by determining the binary opposite of the /27 subnet mask.

11111111.11111111.11111111.11100000 = 255.255.255.224

00000000.00000000.00000000.00011111 = 0.0.0.31

g.     Enter the wildcard mask, followed by a question mark.

R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 ?

A.B.C.D Destination address

any Any destination host

eq Match only packets on a given port number

gt Match only packets with a greater port number

host A single destination host

lt Match only packets with a lower port number

neq Match only packets not on a given port number

range Match only packets in the range of port numbers

h.     Configure the destination address. In this scenario, we are filtering traffic for a single destination, which is the server. Enter the host keyword followed by the server’s IP address.

R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 ?

dscp Match packets with given dscp value

eq Match only packets on a given port number

established established

gt Match only packets with a greater port number

lt Match only packets with a lower port number

neq Match only packets not on a given port number

precedence Match packets with given precedence value

range Match only packets in the range of port numbers

cr

i.      Notice that one of the options is 'cr' (carriage return). In other words, you can press Enter and the statement would permit all TCP traffic. However, we are only permitting FTP traffic; therefore, enter the eq keyword, followed by a question mark to display the available options. Then, enter ftp and press Enter.

R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ?

0-65535 Port number

ftp File Transfer Protocol (21)

pop3 Post Office Protocol v3 (110)

smtp Simple Mail Transport Protocol (25)

telnet Telnet (23)

www World Wide Web (HTTP, 80)

R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp

j.      Create a second access list statement to permit ICMP (ping, etc.) traffic from PC1 to Server. Note that the access list number remains the same and a specific type of ICMP traffic does not need to be specified.

R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62

k.     All other traffic is denied, by default.

l.      Execute the show access-list command and verify that access list 100 contains the correct statements. Notice that the statement deny any any does not appear at the end of the access list. The default execution of an access list is that if a packet does not match a statement in the access list, it is not permitted through the interface.

R1#show access-lists

Extended IP access list 100

10 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp

20 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62


Step 2: Apply the ACL on the correct interface to filter traffic.
From R1’s perspective, the traffic that access list HTTP_ONLY applies to is inbound from the network connected to the Gigabit Ethernet 0/1 interface. Enter interface configuration mode and apply the ACL.

Note: On an actual operational network, it is not a good practice to apply an untested access list to an active interface. It should be avoided if possible.

R1(config)# interface gigabitEthernet 0/1

R1(config-if)# ip access-group HTTP_ONLY in

Step 3: Verify the ACL implementation.
a.     Ping from PC2 to Server. If the ping is unsuccessful, verify the IP addresses before continuing.

b.     From PC2 open a web browser and enter the IP address of the Server. The web page of the Server should be displayed.

c.     FTP from PC2 to Server. The connection should fail. If not, troubleshoot the access list statements and the access-group configurations on the interfaces.


![[Pasted image 20250305143304.png]]


### Part 1: Configure a Named Extended ACL
Configure one named ACL to implement the following policy:

·         Block HTTP and HTTPS access from PC1 to Server1 and Server2. The servers are inside the cloud and you only know their IP addresses.

·         Block FTP access from PC2 to Server1 and Server2.

·         Block ICMP access from PC3 to Server1 and Server2.

Note: For scoring purposes, you must configure the statements in the order specified in the following steps.

#### Step 1: Deny PC1 access to HTTP and HTTPS services on Server1 and Server2.
a.     Create a named extended IP access list on router RT1 which will deny PC1 access to the HTTP and HTTPS services of Server1 and Server2. Four access control statements are required. Use LimitedAccess as the name of the named access list in this activity.

Question:
What is the command to begin the configuration of an extended access list with the name LimitedAccess?

Type your answers here.

Open configuration window

b.     Begin the ACL configuration with a statement that denies access from PC1 to Server1, only for HTTP (port 80). Refer to the addressing table for the IP address of PC1 and Server1.

RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.101.255.254 eq 80

c.     Next, enter the statement that denies access from PC1 to Server1, only for HTTPS (port 443).

RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.101.255.254 eq 443

d.     Enter the statement that denies access from PC1 to Server2, only for HTTP. Refer to the addressing table for the IP address of Server 2.

RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.103.255.254 eq 80

e.     Enter the statement that denies access from PC1 to Server2, only for HTTPS.

RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.103.255.254 eq 443



### Part 1: Verify Connectivity in the New Company Network
First, test connectivity on the network as it is before configuring the ACLs. All hosts should be able to ping all other hosts.

### Part 2: Configure Standard and Extended ACLs per Requirements.
Configure ACLs to meet the following requirements:

Important guidelines:

o    Do not use explicit deny any statements at the end of your ACLs.

o    Use shorthand (host and any) whenever possible.

o    Write your ACL statements to address the requirements in the order that they are specified here.

o    Place your ACLs in the most efficient location and direction.

ACL 1 Requirements

o    Create ACL 101.

o    Explicitly block FTP access to the Enterprise Web Server from the internet.

o    No ICMP traffic from the internet should be allowed to any hosts on HQ LAN 1

o    Allow all other traffic.

ACL 2 Requirements

o    Use ACL number 111

o    No hosts on HQ LAN 1 should be able to access the Branch Server.

o    All other traffic should be permitted.

ACL 3: Requirements

o    Create a named standard ACL. Use the name vty_block. The name of your ACL must match this name exactly.

o    Only addresses from the HQ LAN 2 network should be able to access the VTY lines of the HQ router.

ACL 4: Requirements

o    Create a named extended ACL called branch_to_hq. The name of your ACL must match this name exactly.

o    No hosts on either of the Branch LANs should be allowed to access HQ LAN 1. Use one access list statement for each of the Branch LANs.

o    All other traffic should be allowed.