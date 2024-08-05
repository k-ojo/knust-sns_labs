FIREWALL RULES:

/**
* Rejects all packets going to server (at 192.168.1.55)
*
*/
iptables  -A FORWARD  -p tcp  -d 192.168.1.55  --dport 22  -j REJECT

/**
* Allow admin
*/
iptables  -I FORWARD  -p tcp  -s 192.168.2.33  -d 192.168.1.55  --dport 22  -j ACCEPT 

/**
*Reject Network A
*/
iptables  -A FORWARD  -p tcp  -s 192.168.0.0/24  --dport 80  -j REJECT

/**
* Allow user
*/
iptables  -I FORWARD  -p tcp  -s 192.168.2.33  -d 192.168.1.55  --dport 22  -j ACCEPT
