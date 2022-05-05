# PS2 Classics Vault's Official Source Code #

## What is PS2 Classics Vault? ##

PS2CV is a platform designed top preserve PlayStation(R)2 games in the way you expect PS2 games to be played, however PS2 Classics vault https://ps2classicsvault.com/ was the 1st website/service to bring PlayStation(R)2 titles to play PS2 games natively w/out the need of a disc nor emulate them using a 3rd party emulator. Our services converted PS2 games from their original format "ISO" to "PKG" format and allowed users to download available titles from both the website and through our PKGI live service directly to their PS3 systems ready to install and play.

## Why are we open sourcing our code? ##

This will allow anyone to build their own servers using our code for the greater good of the community, this has unlimited potential to help fan made community servers thrive and create their own vision of game preservation. This has became a huge choice for us since PS2CV is ran using money to keep everything up and running & are unsure if one day i will not be able to maintain or afford the costs related to the sites and it's services development.

## FEATURES: ##

- Full url support
- Partial http/https support (PKGI fully supports https but only in direct download mode)
- Full TLS v1.2 support (Direct downloads are not supported for https/TLS v1.2+, File hosts in https will not be background download compatible)
- Full support for title i.ds, region codes, content name, md5, date of creation, sha256, rap file and size.
- Full category support (allows to seperate games, app, tools etc)

## How To Setup a Server? ## 

To get started setting up your own seerver you need to have some knowledge of editing files using "notepad" on a PC. Once you figured that out you can either creat your own tsv file such as for example the ps3_games.tsv to create one you will need to create a txt file and trhaen save it as ps3_games.tsv on your desktop.

now reopen that tsv file in your notepad and copy and paste this into it w/out the quotation marks, remember this must be always at the top of the document ensure spaces are between each word you can verify this if their is extras lines that has no latter in it.

"Title ID	Region	Name	PKG direct link	RAP	Content ID	Last Modification Date	Download .RAP file	File Size	SHA256"

Now you can start adding content, to add content below the above instruction here is what it will look like


"TITLEID	XX	NAMEOFCONTENT	URL TODOWNLOADOFCONTENT	RAPFILE?	NAMEWHERE FILEWILLBESAVEDAS	DATEOFCREATION		FILESIZE"	


Here is a perfect example of what a game will look like when you apply the above line to your tsv you can also use this line as a refrence to assit you in understanding the structure on how it works:


"NPUA3XXX5	US	My Awesome Game	http://myawesomegame.pkg	NOT REQUIRED	UP00XX-NPUA3XXX5_00-MYAWESOMEGAME	2018-02-06 20:03:54		107037968"


you can also add the same line but the alternative method in case the above one is not working for you:


NPUA3XXX5	US	My Awesome Game	http://myawesomegame.pkg	MISSING	UP0XX-NPUA3XXX5_00-MYAWESOMEGAME		3270590464	3270590464"


The line above shows how you can make it simplified without the need of a rap files or date and time the file was created, pkgi will reconize it either way with no issues. Ensure that after reaching the file size to added a new break/line to be able to repeat the same process and add another item. Useally Enter is the same button the adds a break.


if this is complex we created every available tsv in our code for you to get started, if you do not like the manual approach.

Now we need somewhere to host your tsv file this is where pkgi will need to fetch the tsv files to read it's contents, we **HIGHLY RECOMMEND** users to host them on a server or webhost that will not change the url it's hosted on when over writing the file for the future this helps avoid having to reupdate the config.txt everytime and gets your users less annnoyed, trust me we dont want to lose users, we want to gain users.

We recommend using https://weebly.com to host your tsv on as they are a very reputable web host when it comes to hosting your tsv files and you can overwrite the existing files you uploaded and never have to change the url unless you remove the file and publish the site afterwards, remember everytime you overwrite the previous version of the tsv file you have hosted make sure you publish those changes to the public so pkgi can obtain them wihtout issues.

Now that you have setup the tsv file and uploaded them to a server for pkgi to fetch, you now need to proceed on setting up a config,txt.

## Setup a config.txt file ##

To setup a config,txt file you will need to create a text document using notepad and you will need to put these lines as you see it in the document first before proceeding to the next step:


url_games URL_TO_PS3_GAMES.TSV
url_tools URL_TO_PS3_TOOLS.TSV
url_dlcs URL_TO_PS3_DLCS.TSV
url_themes URL_TO_PS3_THEMES.TSV
url_avatars URL_TO_PS3_AVATARS.TSV
url_demos URL_TO_PS3_DEMOS.TSV
url_apps URL_TO_PS3_APPS.TSV
url_emulators URL_TO_PS3_EMULATORS.TSV
url_updates URL_TO_PS3_UPDATES.TSV


The above lines daiplays where you want pkgi to connect to to obtain the latest definitions from wehre the tsv you have available wheree ever you hosted your files at and will auto download the list to the users ps3 system. If your not supplying downloads or content for a specific category such as for example apps, you can either remove the line "url_apps" before saving your config.txt and pkgi will not fetch that file from your server, you can always have it fo to a server your hosted the ps3_apps.tsv but nothing has to be inside the tsv except the initial setup line, users will just be met with the "no items" notice in the app and you can laweays add them to it and the next time they do a refrssh the content will show up.

Now below the url_xxxx lines you will need to add these line after it, do not add any breaks otherwise pkgi will break:

language en
content 1
sort name
order asc
filter ASA,EUR,JPN,USA
no_music 0


To configure these lines here are some useful changes you can adjust and they will always set this way unless the users has manually changed then in pkgi or you set them up by default

**language en** (Language will tell pkhi what language pkgi should display in, such as if it is in english it will be displayed as "en" or its abrivated version of the word)

**content 1** (Content will tell PKGI to either directly download the content or perform a background download, 1=Direct Download | 0=Background Download, default is set to 1)

**sort name** (sort will tell PKGI how it will sort out the list of content you have available such as name, title, date added etc, defult is set to "name"

**order asc** (order will tell PKGI in what order it should display the content eith from A-Z or Z-A or vice versa, default is "asc")

**filter ASA,EUR,JPN,USA** (filter will tell PKGI to what region of content should be shown to the end user, so the user can sort out content based on the region the content was created for/in, default is set  to "ASA,EUR,JPN,USA)

**no_music 0** (no_music will tell PKGI if the app should play it's built-in melody, default is set to 0. 0=On | 1=Off We useally set this to 1 as it can become annoying at times when downloadingcontent that can't be background downloaded)

# END OF SETUP #

##NOTICE:##
If you choose to use this source code please be aware that this code intentions is to allows others to build thier own projects on their own terms, though we cannot guarantee that there will not be some indivduals that will utilize this code to spread malware or content that may seem legit. We strongly ask everyone to only use sources you 100% trust and has a decent reputation when it comes to offering digital downloads of any content they host. We are not responsible if your personal data is stolen, damaged etc from sources that has bad intentions of spreading malware to your PS3 system using this code to spread it. We want you to stay safe. We will never ask or force you to pay for this code, if your asked to pay for the use of this code, do NOT pay them.
