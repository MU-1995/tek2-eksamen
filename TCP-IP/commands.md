ip.addr == 195.254.168.52

tcp

udp

dhcp

dns

http

tcp.port == 80

ip.addr == ip && http

# /find ip på hjemmeside/
nslookup ek.dk

ping ek.dk, ping google.com

# /min lokale ip og public ip/
ipconfig

curl -4 ifconfig.me
# /ip med DHCP/
ipconfig /release

ipconfig /renew

# /tcp handshake/
ip.addr == 195.254.168.52 && tcp

curl ek.dk
