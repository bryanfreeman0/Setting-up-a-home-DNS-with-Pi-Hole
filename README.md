I wanted to set up a home DNS with Pi-Hole to block adds on devices on my network. 

Pi-Hole works by acting as a DNS server on your home network. When it recieves a DNS request it checks the address against a list of known add servers before going to an upstream DNS service to get the address. If the address is on the list of known add servers it returns an ip address of 0.0.0.0 which goes nowhere so the add is never served.
