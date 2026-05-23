I wanted to set up a home DNS with Pi-Hole to block adds on devices on my network. 

Pi-Hole works by acting as a DNS server on your home network. When it recieves a DNS request it checks the address against a list of known add servers before going to an upstream DNS service to get the address. If the address is on the list of known add servers it returns an ip address of 0.0.0.0 which goes nowhere so the add is never served.

I started with a Raspberry Pi 5 and added a hat to enable it to operate over POE (power over ethernet) because the area with my router and switch where I plan connect the Raspberry Pi is currently short on 12v power outlets and it will also cut back a little on the amout of wires in the tight space which will be convenient.

Once the Raspberry Pi was assembled and connected I connected to it over SSH and ran the below command to retrieve the installer for Pi-Hole and run it.

<img width="562" height="68" alt="1" src="https://github.com/user-attachments/assets/6b6e7848-48d0-4e4a-8824-b987b570b8d6" />

When prompted to select an interface I selected eth0 because I will be leaving the Raspberry Pi connected over ethernet instead of using wifi.

<img width="832" height="573" alt="2" src="https://github.com/user-attachments/assets/dff90af8-3f5f-439c-9da6-7950d3bcd726" />

After selecting the interface I was prompted to select the upstream DNS service that Pi-Hole will use. For this I selected OpenDNS, a free DNS service owned by Cisco, because of its general good reviews when used as an upstream for Pi-Hole.

<img width="849" height="565" alt="3" src="https://github.com/user-attachments/assets/17ed6f04-cae7-4c3c-bc72-d1c24db02d65" />

After this the install finished and it was time to set Pi-Hole as my DNS. I signed in to the admin portal on my home router and set a static ip address for the Pi-Hole so that it will always have the same ip address and then set that address as the primary DNS for my router.

<img width="1082" height="441" alt="4" src="https://github.com/user-attachments/assets/7f415e96-7b86-4c35-a479-e66583bc91b0" />
<img width="805" height="204" alt="5" src="https://github.com/user-attachments/assets/1db6eeb1-cc6a-435b-904a-770f64296ab2" />

After changing these settings I restarted my router and after about a minute the router was back up and operating. I was then able to connect to the Pi-Hole's admin page and see that it was recieving DNS requests and blocking addresses that matched it's list.

<img width="1882" height="1541" alt="6" src="https://github.com/user-attachments/assets/929d1308-0f1e-48b9-bc33-344a5aa64813" />
