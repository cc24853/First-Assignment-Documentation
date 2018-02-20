# First-Assignment-Documentation
Exactly what it says on the tin

legal reasons link: https://pimylifeup.com/raspberry-pi-irc-server/

Setting up an IRC server is possible on a closed network. Typically in a free or developing environment. One can also use a tunnel to connect or set up a different port to reach areas off network.

Hardware needed:
1 raspberry pie
2 computers
a ethernet connection between them

Software needed:
ircd-hybrid (for the pi)
mIRC (for clients)
Windows 10 for the computers
raspberrypi OS

step 0: Open terminal on your pie.
step 1: make sure all software on your pie is up to date. sudo apt-get update and then upgrade.
step 2: sudo apt-get install ircd-hybrid to install the required software on your pie.
step 3: make bad puns while it downloads.
step 4: next, fetch an encrypted password. You can do this by /usr/bin/mkpasswd password
step 5: After you get the warrgarble, write it down and keep it. We will use it later.
step 6: Open the config, you can do this with sudo nano /etc/ircd-hybrid/ircd.conf
Step 7a: In the server block, find name = "hybrid8.debian.local"; and replace it with name = "pimylifeup.irc";
step 7b: replace description = "ircd-hybrid 8.1-debian"; with description = "Raspberry Pi IRC Server";
Step 7c: replace both network_name = "debian"; and network_desc = "This is My Network"; 
         with network_name = "YOUR NETWORK NAME HERE";
         network_desc = "YOUR DESCRIPTION HERE";
step 7d: Find max_clients = 512; and replace it with max_clients = 128;
Step 8: inside of the OPERATOR { block, find and remove #. Only 1 layer, so if you see ##, leave #. This is horribly tedious.
Step 8a: After that pain is done, find name = "sheep"; and replace it with name = "op";
Step 8b: Hunt down user = "*192.0.2.240/28:; and KILL IT* Replace it with user = "*@*";
Step 8c: your mission is to track down password = "xxxxxxxxxxxxx"; and relocate it with password = "REPLACE WITH YOUR ENCRYPTED PASSWORD";
         (use will use the warrgarble form eariler here)
Stap 9: escape this hell with CTRL +X, then press Y and then ENTER.
step 10: now that you are free, you can modify sudo nano /etc/ircd-hybrid/ircd.motd (the message of the day) to your hearts desire
        , but you do not need to.
Step 11: restart everything with sudo /etc/init.d/ircd-hybrid restart


PART 2.

Now the hard part is over, the server is broadcasting and can be hacked so hard, it will make your computers manufacturer cry.
Now we set up the client side. Hop on your windows computers with the mIRC software installed.
Launch it, then click FILE -> Select SERVER (or just press alt + E)
another window will pop up, for the description, you can use anything you want, just make it something you remember and stands out.
For the address, put in the IP of your pie. you can get this with ipconfig in the terminal on your pie. should have 4 dots from
the inet thing.
Click add.
Find your server from the list, and select it. It should have a dunce arrow pointing right to it.
one more screen will pop up, asking you what nickname you want. Type it in and then connect.
Finally, make a channel. An example one would be "#channel", then join. If done right, you should actually see a working GUI.
Do the same on the other windows box, but make a different nickname.
HORRAY! YOU MADE A THING!
