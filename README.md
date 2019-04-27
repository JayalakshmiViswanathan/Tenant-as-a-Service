# Tenant-as-a-Service
Configure linux bridges and VxLAN tunnels for tenants in virtualized data centre environment to achieve tenant isolation and address reusability 
------------------------------------READ ME------------------------------------------
---------------------------TaaS: Tenant-as-a-Service---------------------------------
---------------------------------------by--------------------------------------------
----------------------------Jayalakshmi Viswanathan----------------------------------


Topology example



                               +------+
                               |AS 100|
                      +--------|      |------+
                      |        |  C1  |      |
                      |        +------+      |
                      |                      |  
                 +---------+             +--------+
                 | SP1     |             | SP2    |
                 +-+-+-+-+-+             +-+-+-+-++
                   | | |                   | | |
                   | | |                   | | |
                   | | +------------+      | | |
          +--------+ +-+            |      | | |
          |   +----------------------------+ | | 
          |   |        |  +------------------+ | 
          |   |        |  |         |  +-------+   
          |   |        |  |         |  |           
        +-+---+-+   +--+--+-+     +-+--+--+     
        | L1    |   | L2    |     | L3    |     
        |AS 200 |   |AS 200 |     |AS 200 |
        +-------+   +-------+     +-------+
        / |  | \     / |  | \     /  |  |  \
      H1 H2  H3 H4  H5 H6 H7 H8  H9 H10 H11 H12


Procedure:
This procedure has to be followed after creating a virtualized data center network.
The input text file tenantinput.txt should be in the following format:
{Leaf1-Name}, Tenant1-{H1,H2}, Tenant2-{H3,H4},
{Leaf2-Name}, Tenant1-{H5,H6}, Tenant3-{H7,H8},
{Leaf3-Name}, Tenant2-{H9,H10}, Tenant3-{H11,H12},
For successful run of the program:
 1. give router ids to all the routers.
 2. configure OSPF in all the routers such that the networks south of core and north of leaves are advertised.
 3. enable bgp peering and l2vpn evpn peering.
 4. advertise prefixes of the server networks in bgp.
 5. run the python program: python ECE792_TaaS_test.py.
   
