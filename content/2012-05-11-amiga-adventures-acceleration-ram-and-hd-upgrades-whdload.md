---
layout: post
title: Amiga Adventures (Acceleration, RAM and HD Upgrades, WHDLoad)
date: 2012-05-11 23:40
author: onionsamson
comments: true
categories: [Accelerator Card, Amiga, Amiga 1200, Amiga A1200, Gaming, RAM Upgrade, Syndicate, Tech, WHDLoad]
---
<div class="
          image-block-outer-wrapper
          layout-caption-below
          design-layout-inline
          
          
          
        ">

      

      
        <figure class="
              sqs-block-image-figure
              intrinsic
            " style="max-width:600px;">
          
        
        

        
          
            
          <div style="padding-bottom:75%;" class="
                image-block-wrapper
                
          
        
                
              ">
            <img src="http://onionsamson.files.wordpress.com/2012/05/7d674-image-asset.jpeg" alt="" /><img class="thumb-image" alt="" />
          </div>
        
          
        

        
      
        </figure>
      

    </div>
  



<p id="yui_3_17_2_1_1435859238553_115653">
While visiting the monthly auctions at <a href="http://taylors-auctions.com/">Taylors Auction Rooms, Montrose</a>, a friend happened upon a cardboard box. Not just any cardboard box, though. It was an old Gateway computer box. (Remember the black and white ‘cow spot’ branding, based on the Holstein breed of cow.)</p><p id="yui_3_17_2_1_1435859238553_115659">Within the box was not a lovely, old, decrepit Gateway Pentium-233 or suchlike. Instead, a glorious Amiga A1200, basking in it’s original box; kitted out with a 209Mb hard disk too. Also in the box were several cases of floppies, endearingly labelled and scribbled upon; an ancient printer; and some failing Atari 2600 style joysticks.</p><p id="yui_3_17_2_1_1435859238553_115662">Over the moon, I secured “LOT 3522 BOX OF COMPUTER WARE” for a small sum, along with a humorous lithograph, <em>Saving the Hens</em> by artist Barbara Robertson.</p><p id="yui_3_17_2_1_1435859238553_115668">On bringing the Amiga home, I jacked it in and booted it up. The sound of the floppy drive whirring away brought back waves of nostalgia. Happily, I went straight for <a href="http://amr.abime.net/review_1329">Syndicate</a>, a cherished old game that I originally played through on the Sega Mega Drive (pre-owned from Electronic Boutique, with Genesis printed on the box art). Sadly, installation failed partway through Disk 3 of 4.</p><p id="yui_3_17_2_1_1435859238553_115674">Undeterred I began a browse of eBay and stumbled upon many ways you can upgrade an Amiga. Foolhardy, I picked up a 4Gb Compact Flash (with IDE adaptor) “Hard Disk”, thinking, ‘Wow! What an upgrade. Now I can load all my games on.’</p><p id="yui_3_17_2_1_1435859238553_115677">Not so fast. Many [most?] games don’t come with an installer. That’s where I found <a href="http://whdload.de/">WHDLoad</a>, which is an amazing shareware product that integrates your original games with installers (some of which even add value in fixing or patching sketchy compatibility and bugs). Games are made into a single file (or image) and by default the whole game is loaded into RAM when opened.</p><p id="yui_3_17_2_1_1435859238553_115683">When I got Syndicate to install via WHDLoad, upon execution I was given an error message along then lines of ‘not enough RAM’. Taking a disingenuous stab as to why Syndicate (WHDLoad) would not run on my Amiga A1200, I thought: four floppies @ 800Kb (max) + Workbench 3.1 overhead ~800Kb = 4Mb RAM. The Amiga A1200 comes with only 2Mb RAM (as did my family 486 SX-25Mhz, which we upgraded to 4Mb for <em>Sim City 2000</em> back in 1994/5).</p><p id="yui_3_17_2_1_1435859238553_115689">So I started looking at Amiga RAM upgrade options:</p><ol id="yui_3_17_2_1_1435859238553_115692"><li>Fast RAM PCMCIA (up to 4Mb extra, simple)</li><li>Trapdoor expansion slot Accelrator card</li></ol><p id="yui_3_17_2_1_1435859238553_115698">Diving straight into upgrading Amiga RAM via an accelerator card, there are a plethora to choose from. Accelerators come with upgraded CPUs —from the slightly improved 68030 through to the beastly 68060 that necessitates uprated Power Supply Unit (PSU) and cooling—, some have Memory Management chips (MMUs) and Floating Point chips (FPUs). Most importantly (for my purposes), these accelerators facilitate RAM upgrades. 64Mb is not unusual.</p><p id="yui_3_17_2_1_1435859238553_115701">Depending on the configuration, these accelerator cards can typically sell for anywhere between £100 and £400 on the likes of eBay. I was able to snap up a Viper II 68030 with 8Mb RAM for ~£80 (April 2012).</p><p id="yui_3_17_2_1_1435859238553_115704">It took a genuinely scary amount of force to jam the card into place. I thought I was prepared for this as I had read up on forums such as the <a href="http://eab.abime.net/showthread.php?t=59817">English Amiga Board</a>, but it was still a fearsome moment, checking if that snapping sound was good or bad. Turns out it was good, but I had to tease it out ever so slightly afterwards to get a good connection. Accelerator fitted, I immediately found my next obstacle. </p><p id="yui_3_17_2_1_1435859238553_115710">Before installing the accelerator card, the system loaded fine and everything worked, except for not having enough RAM to run WHDload games. I fitted the accelerator card, but now on booting I got an error message stating:</p><p id="yui_3_17_2_1_1435859238553_115713">Loading failed: object not found
C:LoadModule failed returncode 10</p><p id="yui_3_17_2_1_1435859238553_115716">Commenting the following lines in the startup-sequence (by inserting a semi-colon at the start of the lines) allowed the system to load, but when I then double-clicked a WHDload game to run it, the task bar at the top of workbench would quickly flash “attempting to load[…]”, but nothing further happened:</p><p id="yui_3_17_2_1_1435859238553_115719">;IF EXISTS DEVS:scsi.device
; C:LoadModule DEVS:scsi.device
; EndIF
</p><p id="yui_3_17_2_1_1435859238553_115722">Thanks to a forum user <em>Retro-Nerd</em>, I came to the conclusion that my RAM module was not firing on all cylinders. Confirmed with a quick memory test. All was not lost. <em>Retro-Nerd</em> pointed out a fix. Un- comment (Delete the first semi-colon only) the following line in S:WHDLoad.prefs:</p><p id="yui_3_17_2_1_1435859238553_115731">;NoMemReverse ;do not allocate memory reverse
</p>







 

  
  
    <div class="
          image-block-outer-wrapper
          layout-caption-below
          design-layout-inline
          
          
          
        ">

      

      
        <figure class="
              sqs-block-image-figure
              intrinsic
            " style="max-width:600px;">
          
        
        

        
          
            
          <div style="padding-bottom:75%;" class="
                image-block-wrapper
                
          
        
                
              ">
            <img src="http://onionsamson.files.wordpress.com/2012/05/8a42c-image-asset.jpeg" alt="" /><img class="thumb-image" alt="" />
          </div>
        
          
        

        
      
        </figure>
      

    </div>
  



<p id="yui_3_17_2_1_1435859238553_115735">Bingo! Worked a treat. Now most of my Amiga woes are gone. Though I could do with more fully-functioning RAM…and a couple of zip-sticks for <em>Sensible Soccer</em>…and an old CRT TV for authenticity (and for Playstation 1 and Sega Saturn light gun games)…and…</p><p id="yui_3_17_2_1_1435859238553_115741">My love of the Amiga has been rekindled and I’m looking forward to playing some oldtimeless games with oldtimeless friends.</p>
