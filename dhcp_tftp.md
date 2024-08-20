# DHCP TFTP setup
load process of soc and microprocess sub setup
## DHCP server enable 
  Frist install the DHCP server by these commad in linux [DHCP_SERVER SETUP LINK](https://www.linuxtechi.com/how-to-configure-dhcp-server-on-ubuntu)
* $ sudo systemctl start isc-dhcp-server
* $ sudo systemctl enable isc-dhcp-server
* sudo systemctl status isc-dhcp-server
  
## TFTP server enable
  Install the TFTP server as per the [TFTP SERVER SETUP LINK](https://www.coryfiala.com/how-to-install-tftp-on-ubuntu-22-04)
<br>
* sudo systemctl restart tftpd-hpa
* sudo systemctl status tftpd-hpa
<br>
Here tftp server setup location, has to paste and run the targer to to fetch tftp server files
  <br>
  /srv/tftp/   <br>
  > image-bmc   <br>
  > image-default 
