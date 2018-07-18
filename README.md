# Tor-Notes
Some Tor Notes...  

# General  
You can also use a Tor or I2P hidden service. If you use a hidden service, everything is encrypted and you also don't need dynamic DNS because you can reach your .onion or .i2p address from anywhere automatically. Hidden services also have much larger networks and more redundancy than using a VPN. For example, if ProtonVPN has a network problem or they are doing maintenance or their service is down, it means you will not be able to access your server. You can always access a hidden service. I like I2P because it's more secure, but the problem is not as many people use it as Tor so the I2P network is slower because it has less nodes. But it also depends on where you live, so maybe more people use I2P in Germany, I don't know. Where I live nobody uses I2P in my entire country, so the network is not efficient at all. If more people used I2P, it has the capability to be much faster than Tor.  

I2P is also much easier to configure and comes with a web GUI. Here are some configs for Tor though.  

First, for a Tor hidden service, I recommend installing Tor as a service on your machine. Personally I like to put as few options as possible and control everything with the config file. In the below command, XXX is the path to your Tor config file.
tor --service install -options -f C:\Users\XXX  

Some basic configs for your Tor file should be to specify where your Data directory is. Usually your geoip and geoip6 files are inside the Data directory, but they don't have to be. The geoip files are lookup tables so Tor knows what countries its exit nodes are in so you can use special commands like ExitNodes {de} to only use exit nodes in Germany. If you are always in Germany when you connect to your server, you will get better performance if you connect to a German exit node and not to another country more far away. If you only allow German exit nodes, there is also a small risk that you have less exit nodes to pick from and maybe it will take longer to find one you can connect to. However, Tor has so many nodes in every country, that is usually not a problem.  
DataDirectory C:\Users\XXX\Tor\Data  
GeoIPFile C:\Users\XXX\Tor\Data\geoip  
GeoIPv6File C:\Users\XXX\Tor\Data\geoip6  

You must specify the path to the folder with "hostname" and "private_key" files. If the folder is empty, Tor will automatically generate them. You can also use those files I sent you in Dropbox, depending on what address you want.
HiddenServiceDir C:\Users\XXX  

Each local service must be specified individually in the Tor config. The "TTT" is the port number you want to connect to using Tor, XXX.onion:XXX. The "LLL" is the port number of the local service you want Tor to forward into the Tor network. If your website on your home server is running on port 80, then this should be 127.0.0.1:80. If your SSH server on your local server is 22, then this should be 127.0.0.1:22. Every service will have a different line and you can use HiddenServicePort multiple times.  
HiddenServicePort TTT 127.0.0.1:LLL  
HiddenServicePort 1000 127.0.0.1:80  
HiddenServicePort 1001 127.0.0.1:22  

Here are some more useful links:  
https://www.torproject.org/docs/tor-manual.html.en  
https://www.torproject.org/docs/tor-onion-service  

<br>

# Linux  
Follows...  
