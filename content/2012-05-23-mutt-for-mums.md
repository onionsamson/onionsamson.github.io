---
layout: post
title: Mutt for Mums
date: 2012-05-23 08:52
author: onionsamson
comments: true
categories: [documentation, mums, mutt, Tech, unix]
---
<p><a href="http://www.mutt.org/">Mutt</a> is “a small but very powerful text-based mail client for Unix operating systems”.</p>

<p>The problem I find with many clever computer programs, is that they are written by people who are exceptionally intelligent and demand a large amount of specific knowledge to install and use. Considering myself competent in using computers, but not knowing much about the command-line, nor *nix of any kind, exploring the possibilities can be a devilish but rewarding challenge.</p>

<p>For free software to be truly free (as in both beer and speech), it should be easily installable and configurable by any literate adult. By that, I mean my mum should be able to follow the documentation to install and use the software. Any prerequisite knowledge not in the documentation should be referenced right at the start. There should be no or as low as possible a barrier to entry for everyone.</p>

<p>Why should we care about free and open source software? That’s a discussion for another day. But I will say this. People are working together to develop software that is useful to us, and sharing their working so anyone can contribute and make the software better.</p>

<p>I propose all software should have a mum’s guide. Especially free software:</p>

<ol>
<li>As a way to attract newcomers who feel generally that free (as in speech) software is unfamiliar and hard to learn, and;</li>
<li>To lead with a good example for others to follow.</li>
</ol>

<p>If the software cannot be installed and configured successfully, is that a fault of the user or the developer(s)?</p>

<p>So here is <em>mutt for mums (on Mac OS X)</em>. Basic muttrc supplied by <a href="http://koralatov.com">Koralatov</a>.</p>

<p><em>Note: Although this is written up to be informative (and a little tongue-in cheek), I will be user-testing this with my mum. Don’t slam me for errors in this case, as I am proving a concept. And yes, I am also aware that my mum would not use Mutt over a GUI mail client.</em></p>

<h2>Prerequisites</h2>

<ul>
<li>A computer running Mac OS X 10.5 or above (check by clicking the Apple icon at the top left of your screen, then clicking ‘About This Mac’)- </li>
<li><em>Homebrew</em> and it’s prerequisites, here: <a href="https://github.com/mxcl/homebrew/wiki/Installation">https://github.com/mxcl/homebrew/wiki/Installation</a></li>
</ul>

<h2>Installing Mutt</h2>

<ol>
<li>Open Terminal by pressing the cmd key and space bar together, begin typing terminal, and hit enter when terminal is highlighted. <em>Or</em>, you can go to your Applications folder, open the Utlities folder, then double-click on Terminal.</li>
<li>(You will have installed Homebrew per the prerequisites section above.) type the following command: <code>brew install mutt</code></li>
<li>Next install msmtp. (a smtp mail client for sending email). Type the following command: <code>brew install msmtp</code></li>
</ol>

<h2>Setting up Mutt</h2>

<p>This should be enough to get your started, but you’ll need to fill in your password in the appropriate places, and create the following folders by typing the command <code>mkdir</code>, leave a space, then type the folder name, and finally hit enter):</p>

<pre><code>mkdir ~/mutt
mkdir ~/mutt/cache
mkdir ~/mutt/cache/bodies
</code></pre>

<p>You also need to create the following files (create files by typing the command <code>touch</code>, leave a space, then type the file name):</p>

<pre><code>touch ~/mutt/sig
touch ~/mutt/aliases
</code></pre>

<p>To edit text files, we will be using a program called Nano. To use nano we type the command into our terminal.</p>

<pre><code>nano ~/mutt/sig
</code></pre>

<p>Type in your signature, e.g., mine below. Use ctrl key and oh key together to save, hit enter, then use ctrl key and ex key together to exit.
<img src="https://dl.dropbox.com/u/5435090/Mutt/nano-sig.png" alt="Signature editing with Nano" title="" /></p>

<p>Your aliases file is populated in the following fashion, one entry per line (spacing is optional, but there must be at least one space between each
part of the entry):</p>

<pre><code>   alias son Iain Simpson &lt;iain@m.com&gt;
   alias bob1 Bob Robertson &lt;bob.robertson29145@uk.magicalunicornmail.com&gt;
</code></pre>

<p>Setting aliases is handy for later. When you are sending mail to someone, you can write <em>bob1</em> in the <em>To:</em> field, rather than <em>bob.robertson29145@uk.magicalunicornmail.com</em>  </p>

<h2>Setting muttrc</h2>

<p>This step involves editing two files (muttrc and msmtprc) using Nano, e.g., <code>nano ~/muttrc</code></p>

<p>Firstly copy the text below (highlight with your mouse then press cmd key and c key together to copy).
(We will paste this into Nano later.)</p>

<p>COPY FROM NEXT LINE, starting # muttrc</p>

<pre><code># muttrc
# ----------------------------------------------------------------------
# BASIC SETTINGS
# ----------------------------------------------------------------------
## IDENTITY
set        realname            =   "Your Name"
set        from                =   "your@email.com"
set        use_from            =    yes
set        hidden_host
set        envelope_from       =    yes

## ALIASES SETTINGS
source   ~/mutt/aliases
set        alias_file          =   ~/mutt/aliases
set        sort_alias          =     alias
set        reverse_alias       =     yes

## CACHE SETTINGS
set        certificate_file    =   ~/mutt/certificates
set        header_cache        =   ~/mutt/cache/headers
set        message_cachedir    =   ~/mutt/cache/bodies


# LAYOUT
# ----------------------------------------------------------------------
## INBOX SETTINGS
set    sort           =  "reverse-date-received"
set    index_format   =  "%4C  %Z   %-18.18L   %-30.30s   %{ %b %d %H:%M }"
set    markers        =   no

## CLEAN HEADERS
ignore      *
unignore    From Date Subject To CC
hdr_order   From To CC Date Subject

# FORMATTING
# ----------------------------------------------------------------------
## COMPOSITION
set     autoedit        =    yes
set     recall          =    no
set     include         =    yes
set     tilde
set     editor          =    nano
set     signature        =   ~/mutt/sig
set     delete          =    yes
set     fast_reply      =    yes
set     fcc_clear
set     include         =    ask-yes
set     move            =    no
unset   reply_self

## FORMAT SETTINGS
set    allow_8bit       =    yes
set    charset          =   "utf-8"
set    send_charset     =   "utf-8"
set    locale           =    en_GB
set    use_8bitmime     =    yes
set    indent_string    =   "&gt; "
set    wrap             =    78
set    smart_wrap
set    attribution      =   "On %D, %n wrote:n"
set    date_format      =   "!%a, %b %d, %Y at %H:%M"
set    forward_format   =   "Fwd: %s"


# SERVER SETTINGS
# ----------------------------------------------------------------------
## IMAP SETTINGS
set    imap_user        =   "your@email.com"
set    imap_pass        =   "your password"
set    mail_check       =    60
set    check_new        =    yes
set    imap_keepalive   =    900

## SMTP SETTINGS
set sendmail = "/usr/bin/msmtp"
set sendmail_wait = -1

## FOLDERS
set    spoolfile       =   "imaps://imap.1and1.co.uk:993"
set    folder          =   "imaps://imap.1and1.co.uk:993"
set    record          =   "imaps://imap.1and1.co.uk/Sent"
set    postponed       =   "imaps://imap.1and1.co.uk/Drafts"
set    mbox            =   "imaps://imap.1and1.co.uk/Archives/2012"
set    pager_stop
</code></pre>

<p>STOP COPYING after <code>set    pager stop</code></p>

<ol>
<li>Type the following command <code>nano ~/muttrc</code></li>
<li>To paste into Nano, click within Nano, then press the cmd key and vee key together, <em>or</em> secondary click (right-click). That’s it. <img src="https://dl.dropbox.com/u/5435090/Mutt/secondary-click.png" alt="Secondary click" title="" /></li>
<li>You will need to look through the file using the arrow keys and change the IDENTITY, IMAP and FOLDERS settings. (You may need to google your IMAP settings, e.g., google search for AOL IMAP settings)</li>
<li>As before, when finished editing, press ctrl key and oh key to save, hit enter, then ctrl key and ex key to exit.</li>
</ol>

<h2>Setting msmtprc</h2>

<p>Lastly we will edit msmtprc. Following the same steps as above, copy the below and edit.
Edit your host (per your googled IMAP settings), user and password.</p>

<pre><code>nano ~/msmtprc
</code></pre>

<p>COPY FROM NEXT LINE, starting # msmtprc</p>

<pre><code># msmtprc:
# ----------------------------------------------------------------------

account default
host auth.smtp.1and1.co.uk
port 587
auth on
user your@email.com
password xxxxx
auto_from off
from your@email.com
tls on
tls_starttls on
tls_certcheck off
</code></pre>

<p>STOP COPYING after tls_certcheck off</p>

<p>Edit your host (per your googled IMAP settings), user and password.</p>

<h2>RUNNING MUTT</h2>

<p>To run <em>Mutt</em>, open a Terminal window (by pressing the cmd key and space bar together, begin typing terminal, and hit enter when terminal is highlighted), type mutt and hit enter.
Mutt will open and provided you entered your settings correctly in <em>muttrc</em> and <em>msmtprc</em>, you will be receive and send mail.
Now you just have to learn the keyboard shortcuts, and you’ll be navigating and managing your mail very speedily indeed.
To exit mutt, just hit the ex key.</p>
