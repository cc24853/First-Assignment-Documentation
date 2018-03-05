# First-Assignment-Documentation
The goal of this assignment was to see if it was possible to set up an IRC server. After the server is set up, test if it works using a raspberry pi to communicate to the server as a client.

Major Objectives:
Seeing if it would actually work
Creating the server
Making sure the server can communicate with clients on the same network

picture 1


picture 2


picture 3


There is only 1 working model of the IRC server I set up.

Setting up an IRC server is possible on a closed network. Typically in a free or developing environment. One can also use a SSH tunnel 

to connect to areas off network.


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

step 5: After you get the encrypted password, write it down and keep it. We will use it later.

step 6: Open the config, you can do this with sudo nano /etc/ircd-hybrid/ircd.conf

Step 7a: In the server block, find name = "hybrid8.debian.local"; and replace it with name = "pimylifeup.irc";

step 7b: replace description = "ircd-hybrid 8.1-debian"; with description = "Raspberry Pi IRC Server";

Step 7c: 
       replace both network_name = "debian"; 
       
       and network_desc = "This is My Network";

       with network_name = "YOUR NETWORK NAME HERE";
         
       network_desc = "YOUR DESCRIPTION HERE";
         
step 7d: Find max_clients = 512; and replace it with max_clients = 128;

Step 8: inside of the OPERATOR { block, find and remove #. Only 1 layer, so if you see ##, leave #. This is horribly tedious.

Step 8a: After that pain is done, find name = "sheep"; and replace it with name = "op";

Step 8b: Find user = "*192.0.2.240/28:; and delete* Replace it with user = "*@*";

Step 8c: Replace password = "xxxxxxxxxxxxx"; with password = "REPLACE WITH YOUR ENCRYPTED PASSWORD YOU WROTE DOWN";
         
Stap 9:  Press CTRL +X, then press Y and then ENTER to exit.

Step 10:

   now that you are free, you can modify sudo nano /etc/ircd-hybrid/ircd.motd 

   (the message of the day) to your hearts desire, but this is not required.
        
   Step 11: restart everything with sudo /etc/init.d/ircd-hybrid restart to



PART 2.

Now the hard part is over, the server is broadcasting and can now serve.

Now we set up the client side. Hop on your windows computers with the mIRC software installed.

Launch it, then click FILE -> Select SERVER (or just press alt + E)

another window will pop up, for the description, you can use anything you want, just make it something you remember and stands out.

For the address, put in the IP of your pie. you can get this with ipconfig in the terminal on your pie. should have 4 dots from

the inet line.

Click add.

Find your server from the list, and select it. It should have a dunce arrow pointing right to it.

one more screen will pop up, asking you what nickname you want. Type it in and then connect.

Finally, make a channel. An example one would be "#channel", then join. If done right, you should actually see a working GUI.

Do the same on the other windows box, but make a different nickname.

What I learned:

Setting up an IRC server is rather tedious, but it did give me some information on how to use command line on linux. The hardest part 

was finding a guide that actually had all the steps for me to follow. Once I acquired this I was able to learn by example how to set up 

an IRC server and can now repeat the process much faster, should I need to again in life.

Conclusion of Project:

IRC server working and users and send messages to each other. It is possible to do this in a closed delevopment environment or similar.

It is also possible to accomplish this by using a tunnel to reach outside connections.

Citations

The guide I used: https://pimylifeup.com/raspberry-pi-irc-server/
