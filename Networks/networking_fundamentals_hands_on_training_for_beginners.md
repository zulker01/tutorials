# Networking Fundamentals: Hands on Training for Beginners #
## Network Basics ##
### Introduction ###
1. Topics
	1. Network Basics
		1. Definition
		2. Types of Networks
		3. Network Topologies
		4. Summary
	2. Network Models & Protocols
		1. OSI Model
		2. TCP/IP Model
		3. Comparison
		4. Summary
	3. Layer-2 Networks & Switching (broadcast domains, collision domains)
		1. Layer-2 Networks
		2. MAC Addressing
		3. Layer-2 Switches & Functions
		4. VLANs
		5. Summary
	4. Layer-3 Networks & Routing
		1. IP Addressing & Subnetting
		2. Basic Routing
		3. Routing Protocols
		4. Summary
	5. Important Concepts
		1. DHCP
		2. TCP & UDP
		3. ARP
		4. DNS
		5. NAT - Network Address Translation
		6. VPN - Virtual Private Network
		7. Summary
	6. Bonus Section
		1. How to make career in Networks
			1. For certifications
			2. For career
			3. For basics
2. Not advanced topics
	1. Comptia Network+ course
	2. CCNA course

### Network Basics ###
1. Topics:
	1. What are networks
	2. Types of networks
	3. Journey and growth of technologies
	4. Different network topologies
2. What is Network?
	1. Network is a group of two or more computing or digital devices connected together via communication channel or medium
		1. For sharing data or info
	2. Media
		1. Copper
		2. Wireless
		3. Bluetooth
		4. Satellites
3. Evolution (to understand the need)
	1. 1960s
		1. Big large systems
		2. Operating in isolation
		3. Manual data sharing
			1. even to machines within organization
				1. It is called sneaker network
		4. Requirement of business
			1. Data & Resource's sharing
			2. Performance
			3. Efficiency
		5. Solution
			1. LAN
				1. Local Area Network
					1. Interconnection of multiple computer systems which are in close proximity
						1. To share data sources and data
			2. LANs were not sufficient for geographically distributed computers (need of interconnecting beyond boundaries)
				1. Solutions
					1. MAN - Metropolitan Area Network
					2. WAN - Wide Area Network
					3. Internetwork (internet)
			3. The solutions could be used to connect computer systems across the globe
				1. This caused revolution in the business world
4. Types of Networks
	1. PAN - Personal Area Network
		1. Limited in terms of coverage area (Private network)
			1. Accessibility is limited to one or few users
		2. Exmples:
			1. Bluetooth (between cell and other bluetooth enabled device, mouse, keyboard, ...)
	2. LAN - Local Area Network
		1. It is usually owned and administratively controlled by a single body
			1. Spread across
				1. Campus area
				2. Building
				3. Office
		2. For close proximity
			1. All end users in an office can be interconnected (cells, ...)
			2. Examples:
				1. Printers
				2. IP Phones
				3. Fax machines
				4. Scanners
				5. PCs
				6. Servers
		3. Networking devices used for LAN
			1. Routers
			2. Switches
			3. Hubs
			4. Firewalls
		4. Media
			1. Copper
			2. UTP
			3. Wifi
			4. Hybrid
				1. Combination of two or more types of media
					1. Wifi + Wired (for printers)
			5. Cables
	3. MAN - Metropolitan Area Network
		1. Expands across a city
			1. Cable TV network
		2. Use-case
			1. Organization looking to connect it's offices across the city
	4. Internetwork
		1. Network of networks
			1. Example: Internet
				1. It is the largest network on the plannet
		2. It is a larger network of smaller networks interconnected using some communication channels and protocols
			1. Protocol: It is a set of rules and policies defined to control and govern the data communication over a network
		3. Types of Internetworks
			1. Intranet
				1. Internal network (of an organization)
					1. private (to an organization)
				2. For it's own employees say
					1. To connect to
						1. HR System
						2. Payroll system
						3. Accounts
						4. Leave management system
					2. Services are provided by organisations through their private network
						1. No external users can access their services
			2. Extranet
				1. It is an extension of the intranet

						Extranet (vendors, partners, business associates)
							^
							|
							v
						Intranet (internal network)
						
					1. External access to intranet but
						1. Limited access and control
							1. Vendors might need access
			3. Internet
				1. It is a public network (network of networks)

						Internet (Public network)
							^
							|
							v
						Extranet (vendors, partners, business associates)
							^
							|
							v
						Intranet (internal network)

### Network Topologies ###
1. Types of network topologies
	1. Physical Topology
		1. Physical layout: How devices are connected physically (wifi, cables, ...)
	2. Logical Topology
		1. How data flows in the network (travel network)
	3. Network may have different physical and logical topology
2. Physical Topologies
	1. Bus topology
		1. What is this? Simplest
			1. All Nodes are connected to single main backbone cable
				1. Advantages:
					1. Low cost
					2. Easy to understand
					3. Suitable for small networks
					4. Easy to expand
						1. Single cable
							1. Just add a device to the end of the cable
				2. Disadvantages:
					1. Only one node can transmit at the same time (what about multiplexing?)
						1. If two more ore devices try to transmit data at the same time, collisions may occur
							1. Collision: Signals colliding
								1. More devices can increase the chances of collision
									1. It can bring down the network
									2. Network storm - high collisions that can bring down the network
	2. Ring topology
		1. Better than Bus topology
			1. Backbone connects to itself
			2. How does it work?
				1. Token goes around in the ring (reduces traffic)
				2. Token checks at each node, if it has anything to transmit
		2. Low collisions
		3. May slow down the network
			1. If many nodes want to transmit
				1. Token gives access to only one node at a time (all the other nodes have to wait until the tramission is completed)
					1. One node at a time
						1. Might not be possible to use the network due to slowness
		4. Difficult to troubleshoot (?)
		5. If one node fails
				1. The whole network might see the impact
	3. Star toplogy
		1. All devices are connected to a central device (switch - in most cases)
		2. Widely used in LAN networks
			1. switch is central device
			2. All devices are connected to the switch
		3. Easy to troubleshoot
			1. Different link is used (independent of other links)
		4. Single point of failure
			1. If switch fails, it brings down the whole network
	4. Mesh topology
		1. Two types
			1. Full mesh
				1. High redundancy
					1. If a node goes down, there are other links to communicate (another path can exist)
				2. High cost
					1. Every node is connected to every other node
				3. Mostly used in WAN networks
			2. Partial mesh
				1. Low cost than full mesh
				2. Not fully redundant
					1. A few extra links
3. Logical Topology
	1. How data flows in the network
		1. Consider star network
			1. Central box can provide the function of bus topology
				1. Data flows like a bus topology
			2. Central bos can provide the function of ring topology
4. Other topologies:
	1. Point-to-point
		1. No intermediate nodes
			1. One device is connected to another device directly
	2. Point-to-multipoint - generally used in WAN networks
		1. Central node (hub node say)
			1. It is connected to other nodes (branch nodes)
				1. No interconnection between branch nodes directly
				2. If branch node wants to communicate with another branch node, it has to go through the hub node
			
						node1 -> node2
							^
							|
							v
						node2
									
## Network Reference Models ##
### OSI Model Part-1 ###
1. Network reference models
	1. What are those?
	2. Why were they needed?
2. Evolution of technologies
	1. 1970 - increase of demand (to connect offices)
		1. No standard in place
	2. Challenges: (not standardised)
		1. Connecting multivendor, different networks
			1. Difficult to work together
			2. Difficult to connect together
		2. Different network protocols
		3. Reliability
			1. Because of incompatibility
		4. Decentralized network management
			1. Each vendor had a way to manage their networks
			2. Topologies were not consistent
		5. Inconsistent security policies
		6. Flexibility
	3. Solution: Standardization (OSI, TCP/IP models)
		1. Consistencies
		2. Standard protocols
		3. Standard designs
	4. Models
		1. They define how the end systems can communicate across network
		2. Reference model
			1. Defines how data communication can be established
3. Reference Models:
	1. A reference model defines:
		1. How information from a software application in one system moves through a network medium to a software application in another system
		2. Defines the functions of communication software in a generalized and structured manner
			1. Which helps to carry out the network product development activities.
	2. A network model must consider:
		1. Underlying communication hardware
		2. Network medium and/or type of channel
		3. Application programs
	3. Two popular reference models
		1. OSI reference model (by ISO - International Standard organization)
		2. TCP/IP (by DoD - Department of Defence)
	4. OSI Model
		1. In 1984
		2. It provides vendors with standards
			1. It ensures greater compatibility and interoperability between network technologies (produced by different vendors globally)
		3. Benefits - with layered approach
			1. Manageable (easier)
			2. Standardizes interfaces
			3. Ensures interoperability
				1. Different vendors can co-exist in the same network
					1. The vendors could use the same standard
			4. Promotes modular engineering
			5. Reduces devlopment cycle
				1. Each layer can be developed independently (and in parallel)
			6. Reduces complexity
				1. Responsibilities were divided between layers and communication between layers were standardized
		4. Layers:

				Application
				Presentation
				Session
				Transport
				Network
				Data Link
				Physical
				
			1. All people seems to need donut pepsi

### OSI Model Part-2 ###

## Layer 2 Networks ##
### Switching Fundamentals ###
### Unicast, Broadcast and Multicast ###
### How Switch Works ###

## Layer 3 Networks ##
### IP Address ###
### Subnet ###
### Routing ###

## Key Concepts ##
### Key Networking Concepts Part-1 ###
### Key Networking Concepts Part-2 ###

## Career Options ##
### Career Options in Networking ###