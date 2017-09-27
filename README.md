# vpn
A very simple vpn configuration manager for the shell. The main purpose is to connect to various bookmarked VPNs.

## Usage

    ⤷ ./vpn 

      __     ______  _   _  
       \ \   / /  _ \| \ | |
        \ \ / /| |_) |  \| |
         \ V / |  __/| |\  |
          \_/  |_|   |_| \_| 0.1


    Reading vpn configurations from file "~/.vpnfavs"...
    Available VPN connections:

    0) /etc/openvpn/se10.nordvpn.com.tcp443.ovpn
    1) /etc/openvpn/sg2.nordvpn.com.tcp443.ovpn

    Please choose a VPN configuration to use (0-1): 


## Configuration

### VPN bookmarks
Put your VPN bookmarks in a file called **~/.vpnfavs"**. Each in a separate line:

    /etc/openvpn/se10.nordvpn.com.tcp443.ovpn                                                           
    /etc/openvpn/sg2.nordvpn.com.tcp443.ovpn                                                            

### VPN credentials

*VPN* supports stored credentials encrypted with *OpenPGP*.
This is a simple, PGP encrypted, file containing just two lines: The Username in the first line and the password in the second line.

First, *VPN* looks for a file with **.vpnauth.gpg** extension in the same directory of the configuration file. If you, for example, connect to a VPN using a configuration file called */etc/openvpn/se10.nordvpn.com.tcp443.ovpn*, *VPN* will try to decrypt  credentials from */etc/openvpn/se10.nordvpn.com.tcp443.ovpn.vpnauth.gpg*.

If no such file is present. VPN will look for a general authentication file **~/.vpnauth.gpg**.

If no authentication file was found at all, OpenVPN will prompt for credentials.

## Limitations 

Although VPN supports PGP to let you store your credentials in a save place, the username and password are passed to OpenVPN via an expect script as command line arguments. Therefore the credentials could easily be obtained from procfs and ps(1). **Know your threat model**
