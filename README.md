Junos 17.3 BETA Test Plan in cooperation with Coloclue
------------------------------------------------------

[Netwerkvereniging Coloclue](https://coloclue.net/) have the intention to test the following features in a production environment.

- RFC 8092 / BGP Large Communities (more details below)
- IPv6 on vMX on NFX250

Customer Contact Details
------------------------
* Name: Network committee
* E-mail: routers@coloclue.net
* Telephone: N/A
* Company name: Netwerkvereniging Coloclue
* Job Title: N/A
* Address: Frans Duwaerstraat 34 / 1318 AC / Almere / The Netherlands

Marketing
---------

We'd be happy to provide a reference for marketing for a product contained in this beta program.

Coloclue Network overview
-------------------------

Additional information regarding our setup:

- Our network has multiple peering connections, it is likely a Public Internet Exchange will be connected to the vMX/NFX. Coloclue maintains extensive BGP peering with hundreds of Autonomous Systems.
- We only have systems in production, currently based on Bird (for a quick overview visit our topological [weather map](https://sysadmin.coloclue.net/) )
- We have resources available to test the software
- We will inform you whenever we discover problems and think they might be related to the software/hardware

BGP Large Communities
---------------------

As described in Coloclue's `Aut-num` as registered in the RIPE DB, Coloclue supports a number of RFC 1997 and RFC 8092 BGP Communities through its BIRD deployment:

```
ACTION COMMUNITIES:
===================
RFC 1997  | Large      | Meaning (Action)
----------+------------+-------------------------------------
8283:50   | 8283:1:50  | Set LOCAL_PREF to 50 (default is 100)
8283:150  | 8283:1:150 | Set LOCAL_PREF to 150 (default is 100)
-         | 8283:2:0   | Prepend 8283 once to all eBGP peers
-         | 8283:2:nnn | Prepend 8283 once to peer AS nnn
-         | 8283:3:0   | Prepend 8283 twice to all eBGP peers
-         | 8283:3:nnn | Prepend 8283 twice to peer AS nnn
-         | 8283:4:0   | Do not export to eBGP peers
-         | 8283:4:nnn | Do not export to peer AS nnn
65535:0   | -          | G-SHUT [draft-ietf-grow-bgp-gshut]
65535:666 | -          | BLACKHOLE [RFC 7999]
----------+------------+-------------------------------------
```

Specific to RFC 8092 Communities, the following routing policy tests will be performed:

- Are Large Communities visible through `show route extensive` and 'show route detail`
- Does the routing policy allow to delete one or more Large Communities from a route
  * Delete through full simple matching
  * Delete through regular expression matching
  * Delete through inverse matching of the above two approaches
- Does the routing policy allow to add one or more Large Communities to a route
- Does the routing policy allow to match on one or more Large Communities:
  * Through full matching "from community foo"
  * Through regular expression based matching
  * If a positive or negative match is found, can an action be set such as LOCAL_PREF manipulation
