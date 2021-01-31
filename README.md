********************************************************
Straightforward Training™
Windows 10 Security (Paranoid Mode) aka Threat Level Midnight!
Author: Saulo S. Ortiz
Date: 20210113
Update: 20210130
Contact: thetiredretired@gmail[.]com
Copyright ©2021 Saulo Ortiz. All Rights Reserved!
********************************************************

No reproduction/modification of this guide is allowed for commercial purposes without explicit written permission from the author!

==================================================================================================================================================
A Bit About the Author:
==================================================================================================================================================
A retired US Air Force Logistics Planner with two tours of war, was introduced to computers (Commodore 64) at the an early age (11). Then, during
High School he found a summer job in a local "Mom's and Pop's" computer repair shop where he learned to honed his PC repair and building skills.

After joining the US Air Force in 1995, he continued to engage in all computers and technology matters, and learning more about network security
and management. He went on to have his own successful side-business as a Cyber-security Consultant and SOHO Technician during and after his Air
Force career.

Today, he works as a Senior Malware Analyst for the Department of Defense. Holds 22 federal certifications, several industry leading certificates,
and a Bachelors in Cyber Forensics/Information Security from Keiser University. He lives with his beautiful wife of 27 years which has giving him
two great, but equally hyper kids.

==================================================================================================================================================
Disclaimer:
==================================================================================================================================================
	1. All steps in this guide have been confirmed multiple times that will not cause any damage/corruption to data, but as always, this is not
	100% guaranteed. So, take all necessary steps to save all important data to an external device before attempting this or any OS modifications.
	Don't forget to	include any browser bookmarks backups which almost everyone forgets to do.

	2. These modifications are set for a system that will no longer accept updates (patches). I cannot guarantee that the modifications will remain
	if you continue	to receive updates. *More on this on a later revision.

	3. The modified settings in this guide are for a Desktop environment. If any functions are required by the user to perform work/school (video
	chat, smart card remote desktop functions, etc) modifications will need to be reset to their original settings or simply just don't disabled
	them at all. Modifying these on a laptop environment will result in very limited video communications...unless you know what you need to do.

	4. Please read each modification option carefully to understand what they do before you disable/enable them. Always backup your current Windows
	settings to an external device using Windows Backup or any third party tool you favor. Also do a restore point before modifying Windows just
	in case you need to go back.

	5. Bloatware removed can not be reinstalled unless you re-install the OS from scratch! This may change later on.

	6. These steps have only been tested with Windows 10 10240 and 19041. I cannot confirm they will work with any other Windows 10 versions.

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	Windows 10240 has way less Bloatware than higher versions, but are more difficult to remove. Cortana cannot be removed in 10240 version.
		This guide goes over Windows 10 (19041) which is easier to modify.
--------------------------------------------------------------------------------------------------------------------------------------------------

==================================================================================================================================================
Knowledge Level:	Advanced
==================================================================================================================================================

==================================================================================================================================================
Tools needed:
==================================================================================================================================================
	-Glasswire 1.2 (only use this old version...newest is no longer free)
	-ApateDNS (FireEye/Free)
	-CCleaner 5.6.7
	-Notepad++ (Any version)
	-Wise Registry Cleaner 9.4.7.619

*All tools located in my Google Drive...contact me for access. SHA hashes will be provided for each program.

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important!	Create an Image Backup and a restore point before making any changes toi you system! Better yet, if enough resources are available,
			do all this changes in a VM for testing purposes before doing them in your actual system.
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==

==================================================================================================================================================
Index:
==================================================================================================================================================
		1. 	Disabling Some Privacy Settings
		2.	Software Tool Setup
		3.	Capturing Callouts
		4.	Removing Bloatware
		5.	Modifying the Firewall
		6. 	Exporting Firewall Rules and Hosts File Changes for Backup
		7.	Disabling Some Services
		8.	Modifying the Group Policy
		9.	Cleaning and Backing Up the Registry
		10. 	Bonus Info!
==================================================================================================================================================

==================================================================================================================================================
Intro:
==================================================================================================================================================
Who benefits from this guide:
If you do not intend to connect to the Microsoft Store and believe all your data is yours to keep in your own location and not a cloud environment,
then modifying the OS may be for you. Always make sure you create able restore point to go back to if you notice something you need is no longer
working.

This guide was created to allow users to customize/harden their Windows 10 operating system to stop data leaks. It can provide a more secure OS but
the trade off is probably some broken applications or services needed by the user. Carefully read this guide and the options you will be modifying
in Windows to know if you'll need them or not.

You can use this guide with Windows XP, 7 and 8/8.1. Of course, they don't have the Bloatware Windows 10 comes with, but you can do the rest of the
modifications in the same manner as explained here. Some areas are named differently on each OS but they work in the same way. By the end of this
guide you will have a greater understanding of the Windows operating system at an advance to expert level.

FYI...There is a PowerShell script (Windows10Debloater) available to remove Bloatware, but I could not get it to remove anything in version 19041.
Therefore I do not recommend it at this time.


==================================================================================================================================================
Step #1: Disabling Some Privacy Settings
==================================================================================================================================================
This is the easy part, so enjoy it while you can.

	1. In the Search Bar type and run: privacy settings

	2. Go through each section in the meny and Disable (turn off) what you don't want running automatically

	3. Reboot for changes to take effect

	4. In the Search Bar type and run: settings

	5. Disable any options here you do not want


==================================================================================================================================================
Step #2: Software Tool Setup
==================================================================================================================================================
This step is going to take a while to complete, but necessary based on my findings.

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	You'll need .NET 3.5 for ApateDNS to work. Install it before starting this step!
--------------------------------------------------------------------------------------------------------------------------------------------------

	1. Download all tools mentioned in the Tools section

	2. Disable your Internet connection by either:
		a.	Control Panel > Network and Sharing Center > Change Adapter Settings > Right click on the NIC icon and select Disable
		b.	Or remove the USB antenna
		c.	Or remove the cat5 cable
		d. 	Right click on the Internet Access icon on the right side in the Taskbar > Open Network & Internet Settings > Status > Adapter Options
			Right Click on your connection icon, then select Disable

	3. Install ApateDNS first

	4. Install Glasswire second

	5. Install Notepad++ third

	6. Install all other software tools now

	7. Reboot the system for changes to take effect


==================================================================================================================================================
Step #3: Capturing Callouts
==================================================================================================================================================

	1. Run ApateDNS and use DNS 127.0.0.1 then click Start

--------------------------------------------------------------------------------------------------------------------------------------------------
Note:	Pay attention to ApateDNS and Glasswire. If anything tries to call-out during or after tool installation, or when you run each tool, use
		Glasswire to block them. Also you can modify the hosts file using Notepad++ and entering the URL or IP found in ApateDNS and Glasswire.
		All this will take a while for you to capture, edit and repeat.
--------------------------------------------------------------------------------------------------------------------------------------------------

	2. In Glasswire:
		a. Look for the Alert
		b. Click on the Fire icon next to it to create a Firewall Rule

--------------------------------------------------------------------------------------------------------------------------------------------------
Note:	To see the Glasswire Firewall rules: Control Panel > Windows Defender Firewall > Advance Settings
--------------------------------------------------------------------------------------------------------------------------------------------------

	3. To use Notepad++ to edit the Hosts file and create a loop for any call-outs to return to your host machine:
		a.	Go to C:\Windows\System32\drivers\etc\
		b. 	Right click on the hosts file
		c.	Select Edit with Notepad++
		d.	When you save the changes (Ctrl+S) it will ask you to open Notepad++ as administrator, select Yes for your changes to be moved to the
			new Notepad++ instance
		e. 	Save any changes

	4. Under all the commented out statemens start a new line and enter any findings ApateDNS. Example:
			127.0.0.1		adobe.updates.com		#Adobe Reader 11

--------------------------------------------------------------------------------------------------------------------------------------------------
Note:	A good resource for an already edited hosts file can be found in www.someonewhocares.org. I highly recommend using this server hosts file
		for personal use. Make sure you inspect it all and change any 0.0.0.0 to 127.0.0.1. There is a difference in how these two IPs work.
--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	You may need to allow for hidden files and folders in to be viewed:
			a. 	Control Panel > File Explorer Options > View Tab
			b.	Select Show hidden files, folders...
			c.	Uncheck Hide extensions for known file types...
			d. 	Save the changes
--------------------------------------------------------------------------------------------------------------------------------------------------

Optional: To enter any Glasswire findings in the hosts file:
		a.	Move your mouse over the alert and wait for the URL or IP address to show
		b.	Using Notepad++ enter a new loop line with that information. See step #4 above.

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important!	Make sure you block all of these tools from calling out to their home servers, especially CCleaner, Glasswire and Wise Registry
			Cleaner. You don't want them to update and locked you out from certain options. Also you don't want leaks from them either.
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==


==================================================================================================================================================
Step #4: Removing Bloatware
==================================================================================================================================================
This step is going to take a while to complete...

Use CCleaner to remove Bloatware like MS Store, Cortana, Mail, Tips, Weather, Messaging, Eclipse, XBOX, OneDrive, People, Remote, Maps, Mixed
Reality, etc. Depends on what you don't want to use.

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important: 	You cannot re-install any of the Windows Modules so make a Restore Point and an Image Backup if you think you may need any of these
		features later!
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==

	1. Run CCleaner and uninstall any of the Windows Modules you don't need mentioned above.
		a. CCleaner > Tools > Uninstall
		b. Remove any Windows modules

--------------------------------------------------------------------------------------------------------------------------------------------------
Note:	FYI the CALC may be the only one you will need and you need to block it from calling out...which it does.
--------------------------------------------------------------------------------------------------------------------------------------------------

	2. While you're here, stop CCleaner from auto running when Windows starts and also from updating:
		a. Options > Privacy > Uncheck box
		b. Options > Smart Cleaning > Uncheck Enable Smart Cleaning
		c. Options > Updates > Uncheck all checkboxesboth
		d. Options > Settings > Uncheck Run CCleaner when computer starts
		e. Tools > Statup > Disable any program here you don't want to automatically start when Windows starts like CCleaner, SteamOS, etc.
		This can save memory on low memory systems

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important!	Do not disable any Antivirus or security program!
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==


	3. Just like before, open the hosts file in Notepad++ as Administrator and type under all the default commented out statements any new findings
	Example:
		127.0.0.1		adobe.updates.com			#Adobe Reader 11.01
		127.0.0.1		Any_ApateDNS_Findings		#Your_Comment_Here_To_Indicate_From_Where_This_is_Coming_From

	4. Leave it running for a while to capture all of the call-outs...also do it after a few reboots and try all your software if you want to stop
	leaks. For example, why does File Explorer need to connect to the Internet?! Why does CALC also connects? These applications should just RUN
	from the computer and not contact anyone for any reason!

	5. If anything shows up in Glasswire, make sure you block it by selecting the Fire icon next to the alert

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	If you don't want to keep CCleaner then uninstall it when you're done...If you're going to keep it, secure it with the steps I've mentioned
	above but also disable the Autorun, Auto Update and Monitoring features in its Settings tab
--------------------------------------------------------------------------------------------------------------------------------------------------


==================================================================================================================================================
Step #5: Modifying the Firewall
==================================================================================================================================================
Once you are done editing the hosts file and modifying the Firewall through Glasswire, make sure you save a copy of the hosts file and also export
the Firewall settings and again them in a safe place. But first lets modify the Firewall a little bit more.

	1. Go to:
		a. Control Panel > Windows Defender Firewall > Advance Settings
		b. Or in the Search bar or icon search for Windows Defender Firewall with Advance Security

	2. Select Inbound Rules

	3. Click on the Profile column to sort out starting with All

	4. Any IPv6 settings Disable them or Block them...either way they will not be used at this moment

	5. Disable the following:
		a. AllJoyn Router
		b. Any Remote Assistance/Remote Services
		c. Any Modules that have been removed or still being used
		d. Any other programs you don't want them to call-out to their home servers

	6. Select Outbound Rules and sort it the same way as the Inboud Rules

	7. Disable any IPV6 settings

	8. Disable the following:
		a. AllJoyn Router
		b. Any Remote Assistance/Remote Services
		c. Any Modules that have been removed or still being used
		d. Any other programs you don't want them to call-out to their home servers

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	You can delete the firewall rules for the Windows modules or just disable them! Just know that if you're still using them, they will
	message you asking for a way out. Disabling them is the easiest way to block them. Also notice all the Glasswire rules...to view them:
			a. Double click on one of them
			b. Select Program and Services tab
			c. Find the name of the application being blocked
--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	I highly suggest for all to get smart on the default firewall rules. Use another computer or take note then Google what you are not sure
		of and how it may affect your communications.
--------------------------------------------------------------------------------------------------------------------------------------------------


==================================================================================================================================================
Step #6: Exporting Firewall Rules and Hosts File Changes for Backup
==================================================================================================================================================
Exporting them is very important...you don't want to redo all of this from scratch if you have to reinstall the OS later on!

	1. Once you are done modifying the Firewall:
		a. On the left menu select Windows Defender Firewall with Advance Security on Local Computer
		b. Right click on it and select Export Policy...
		c. Give it a name...I usually use the following format:
			WFW20210113-1 (WindowsFireWallYearMonthDay-Version), you can use what ever you want
		d. Save the file in a secured device away from the computer
		e. Save a second export in case the first one gets corrupted...it has happened to me

	2. Export the hosts file:
		a. C:\Windows\System32\drivers\etc\
		b. Copy the hosts file and save it in a secured device away from the computer and also have a second one just in case


==================================================================================================================================================
Step #7: Disabling Some Services
==================================================================================================================================================
This step will take you a bit of time to complete. Go through each one, read their description and Disable the Services depending on what they do.

Some Services I've disabled are: ActiveX, Smart Card, Geolocation, Windows Updates, Fax, XBOX, Secondary Logon, anything Remote, Telephony,
Bluetooth, Error Reporting and *Windows Event Logon.

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	*If you turn off Windows Event Logon it will also turn off Network List Services and Network Location Awareness which may disable the
	Search Bar and Search Icon and you won't be able to search for anything...but this issue depends on the Window 10 version
--------------------------------------------------------------------------------------------------------------------------------------------------

	1. In the Search Bar type and run: Services

	2. Go through the list of Services and make sure you Disable them from the Drop-Down menu and also Stop the Service if its running...Look for
	any Services that are of Privacy concerns or just plain useless for	a regular Desktop computer to have

	3. To fully disable them:
		a. Select the Service to disable and read the description
		b. If you do not want it then double click on it
		c. On the Startup Type drop-box select Disable
		d. If its running select the Stop button
		e. Save the changes

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	Some services cannot be stopped!!!
--------------------------------------------------------------------------------------------------------------------------------------------------

	4. Reboot the system and when you return don't forget to run ApateDNS to continue finding callouts!

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important!	I recommend taking screen captures using the Snipping Tool in Windows or notes to save the original settings in case you need to
		revert them
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==


==================================================================================================================================================
Step #8: Modifying the Group Policy
==================================================================================================================================================
Ok...almost done! I've left the longest step in this guide for last. FYI...Some rules state Allow while others state Turn Off...read what they say
then make the necessary changes by double-clicking on them. I highly recommend you checking all of the other folders here so you can get a sense
of all the options you have available. You'll be amazed!

	1. In the Search Bar type and run: gpedit.msc

	2. Open	Computer Configuration > Administrative Templates > Windows Components

	3. Go through each folder and look for any policy you may not need or is a Privacy concern
		(e.g. Maps, Find My Device, *TablePC in a Desktop environment)

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
Important!	*Do not disable TabletPC or anything Tablet related in both Group Policy and Services if you have a Wacom or similar peripheral!
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==

	4. Carefully read each option that reads Turn Off or Enable and what they do...FYI, you need to Enable a Turn Off policy

--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	By default Policies will read "Not configured" which is the same to say the Policy is either On or Off depending of what it states in its
		description
--------------------------------------------------------------------------------------------------------------------------------------------------
Note: 	If you see an icon of an arrow pointing down, it means that the Service was turned off. You don't need to do anything in Group Policy
	unless you want to. But since this is Paranoid mode then...
--------------------------------------------------------------------------------------------------------------------------------------------------


==================================================================================================================================================
Step #9: Cleaning and Backing Up the Registry
==================================================================================================================================================
The last thing to do is clear the registry from all the dead registry keys left from all the removing and modifications. This is another easy
part.

	1. Run CCleaner > Registry > Scan for Issues

	2. Once the scan is complete, it will ask you if you want to save the registry before commiting to any changes...this is optional

	3. When done close CCleaner

	4. Run Wise > Deep Scan

	5. When done click on the CCleaner button...you may have to do this a few times

	6. Done!


==================================================================================================================================================
Step #10: Bonus Info!
==================================================================================================================================================
1. GodMode:
What if I told you there is such a thing as GodMode in Windows? Yes! Just like a video game where you can have access to every available option or
make your character invinsible you can have access to all the Windows user features in one single screen. To do this:
	a. In Desktop create a new Folder

	b. Right click on it and copy and paste this: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}

	c. Hit the Enter keys

	These options are not Group Policy or Services options but user options. But it gives you even more control and modification of the OS.

2. Stop Windows from Remembering:
This option can disable Windows from remembering files that were opened.

	a. In the Search Bar type and run gpedit.msc

	b. Open User Configuration > Administrative Templates > Start Menu and Taskbar

	c. Double click on Do not keep history of recently opened documents and Enable this Policy

--------------------------------------------------------------------------------------------------------------------------------------------------
Note:
	a. Check all other options here! How about: Clear history of recently opened documents on exit
	b. Check the All Settings folder at the bottom of this Folder Tree and also under Computer Configuration...so many options!
	c. These options are per user account and cannot be applied Globally in the system
--------------------------------------------------------------------------------------------------------------------------------------------------

3. Even more options!
I know, I know...by now you have spend probably close to 3 hours navigating all these exiting options and now I gave you about another hour of
bonus options...I just love digging into Windows and finding ways to customize it. So for my last options I give you msconfig!

	a. In the Search Bar type and run: msconfig
	b. On the pop-up go to the Boot tab then the Advance options... button
	c. If you have a multi-core CPU (and we all do now a-days) you have to wonder why Windows doesn't recognize them...not all programs use all
	CPU, but you can tell it here to show you all CPUs by changing the Number of Processors as well as the Maximum Memory.
	d. While you're here check the other tabs

FYI, you can create shortcuts to the Desktop of the Firewall, Resources and other options.


==================================================================================================================================================
Final Words!
==================================================================================================================================================
By now I hope you have a better and greater understanding of the many options Windows has at your disposal. With it we can even find user access
like Windows Updates that Microsoft removed. I hope I have teached you something new about Windows and how you can do more that just be an idle
user.

I've been dealing with Microsoft since DOS 5.0 and I have learned a lot about making an OS run the way I want it. With security in mind, I tell
you the following:

	1. If you're missing a .dll file DO NOT download it from ANY website. Try finding it from another system or reinstalling the program. Usually
	DirectX is the one that gets these problems.

	2. Malware doesn't come infected anymore...it downloads from servers once it's installed...do not install files from unknown sources.

	3. You can easily view if a link in an email is legit by hovering your mouse over the link and waiting for a pop-up...also be aware of typos
	in links like: BankofAmer1ca, 1inkedIn, etc., or redirection from a link or a message asking you to update your Browser. Automatic updates
	from Browsers should always be on.

	4. Never give your info to anyone...no company or financial institution will ever ask you to confirm anything. That is not how they work...
	also be aware of phone scams or emails that stir fear, anger feelings or religious feelings...everything is collected.

	5. Clear your cookies...ALWAYS! Set your browser to NEVER REMEMBER settings.

Contact me if you have any questions on anything I've mentioned here, I've missed something or need clarification.
==================================================================================================================================================
