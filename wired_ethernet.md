On Raspberry Pi:

Edit your Pi's network configuration to use a static IP. Assuming you're using Raspberry Pi OS:

Edit the dhcpcd.conf file:

sudo nano /etc/dhcpcd.conf

Add the following lines at the bottom:

interface eth0
static ip_address=192.168.137.2/24
static routers=192.168.137.1
static domain_name_servers=192.168.137.1

Then reboot the Pi:

sudo reboot


On Ubuntu Laptop:

    Open Settings > Network > Wired

    Click the gear ⚙️ next to the Ethernet connection

    Go to the IPv4 tab

    Change Method to Manual

    Enter:

        Address: 192.168.137.1

        Netmask: 255.255.255.0

        Gateway: Leave blank

    Save and reconnect.