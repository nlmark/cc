We, Coloclue, have the intention to test the following features in a production environment.
- Large BGP communities (this will mainly be tested by Job Snijders, one of the persons that did work on RFC 8092)
- IPv6 on vMX on NFX250 (we have the NFX250's)

>    Customer Contact Details
>    ========================
>    Name            E-Mail          Tel No: Responsibility During Beta
Network committee	routers@coloclue.net	N/A

 >   * What is your company name, job title and address?
Netwerkvereniging Coloclue

>    * Would you be able to provide a reference for marketing of for a product
>      contained in this beta program ?
Yes, this is not a problem

Additional information regarding our setup:
- Our network has multiple peering connections, it is likely AMS-IX will be connected to the vMX/NFX. The peers we have are listed on https://github.com/coloclue/peering/blob/master/peers.yaml
- We only have systems in production, currently based on Bird (a weather map can be found on https://sysadmin.coloclue.net/ )
- We have resources available to test the software
- We will inform you whenever we discover problems and think they might be related to the software/hardware

Test support for the action communities listed below:
remarks:        ACTION COMMUNITIES:
remarks:        ===================
remarks:        RFC 1997  | Large      | Meaning (Action)
remarks:        ----------+------------+-------------------------------------
remarks:        8283:50   | 8283:1:50  | Set LOCAL_PREF to 50 (default is 100)
remarks:        8283:150  | 8283:1:150 | Set LOCAL_PREF to 150 (default is 100)
remarks:        -         | 8283:2:0   | Prepend 8283 once to all eBGP peers
remarks:        -         | 8283:2:nnn | Prepend 8283 once to peer AS nnn
remarks:        -         | 8283:3:0   | Prepend 8283 twice to all eBGP peers
remarks:        -         | 8283:3:nnn | Prepend 8283 twice to peer AS nnn
remarks:        -         | 8283:4:0   | Do not export to eBGP peers
remarks:        -         | 8283:4:nnn | Do not export to peer AS nnn
remarks:        65535:0   | -          | G-SHUT [draft-ietf-grow-bgp-gshut]
remarks:        65535:666 | -          | BLACKHOLE [RFC 7999]
remarks:        ----------+------------+-------------------------------------
