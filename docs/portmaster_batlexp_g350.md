# Portmaster on the Batlexp G350 with PAN4ELEC

This includes an incredibly basic set of setup instructions, and more detailed instructions for portmaster.

How to get Portmaster working on the Batlexp G350 running [PAN4ELEC](https://github.com/Kegg1701/P4ELEC).  
This is a challenge because the G350 doesn't have wifi / any easy way or free way to get internet access.
It's likely that these directions will work for other linux CFW for the G350, but I can't confirm that.
It's likely that these directions will work for the R36S, but I can't confirm that.

# Installing PAN4ELEC

Briefly, to install [PAN4ELEC](https://github.com/Kegg1701/P4ELEC/), download the newest [release](https://github.com/Kegg1701/P4ELEC/releases/) (you want the file ending in `G350.img.gz`).

* Burn it to an sd card using [rufus](https://rufus.ie/) or your preferred sd card image writer.
* Put it in your G350, wait a few minutes while the OS installs.

# Adding Bios / Roms

* Turn the unit off, and insert the card back in your computer.  
* There will be two drives - you want the games drive.
* Put your bios files into `/roms/bios`
* Put your roms into the relevant directories in `/roms/`
* If you want to change the default hotkeys (or anything else), change them in retroarch.

# Install Portmaster

The first step is installing [Portmaster](https://portmaster.games).
Contrary to the [installation instructions](https://portmaster.games/installation.html), which didn't work for me,
we will download and install the package directly.
From the most recent [Release](https://github.com/PortsMaster/PortMaster-GUI/releases), download PortMaster.zip.
Unzip it.  It should have a single folder named PortMaster. Copy that folder (not just it's contents) to 
your games drive;s `/roms/ports` directory.  
For other CFW, you'd copy it to the directory indicated in [this table](https://portmaster.games/installation.html).

Extra step that *might* be optional: copy the PortMaster.sh file from that PortMaster directory to `/roms/ports` (in this case there'd be two copies of the file).  I'm not sure that this is necessary, but it worked for me, so here it is.

Now boot your device with the card, go to Ports, and run the Install Portmaster command that appears.  Shutdown the device and put the card back in your computer.

# Add Games

Now you pick the games you want to add.  

* Go [here](https://portmaster.games/games.html)
* Find the games you want to install (note that for games that aren't ready to run, you'll need to already own them and likely have them installed somewhere.  Each game entry has instructions - follow them) and Download the port package.  Copy these zip files to your sd card in `/roms/ports/PortMaster/autoinstall`.  Don't unzip them.
* Put the card back in your device, boot and run portmaster.  It will auto-install these ports.
* For Ready-to-run games you're done (yay!)
* For other games you'll need to add files

# Adding game files

Put your card back in your computer, and following the directions on the portmaster game [site](https://portmaster.games/games.html) for the game you're installing, copy the relevant files to `/roms/ports/X` (usually `/roms/ports/X/gamedata`, but not always), for port X.

# Adding Libraries

Several ports I like, like Stardew Valley and Celeste, require the Mono lib.
Some of them complain about the lack of it.  Others just fail to launch without it.

You can grab it (and other libraries) [here](https://portmaster.games/runtimes.html).  
Download the `mono-6.12.0.122-aarch64.squashfs` file (version may change).
Copy it to `/roms/ports/PortMaster/libs`.

Presumably this approach would work with other libs too, if that's relevant for you.