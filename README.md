# Project Soteria - 0.0.8 - closed Alpha

A Bot, for Discord, in Python, hosted in the PrivateCraft-Network. But wait! There is more! Project Soteria has a second component, which is downloadable Software for **your** PC! [_(More Info about the Client here)_](https://github.com/Creepmeboom/soteria-client)

## Table of Contents

- [Project Soteria - 0.0.8 - closed Alpha](#project-soteria---008---closed-alpha)
  - [Table of Contents](#table-of-contents)
  - [What is Soteria all about?](#what-is-soteria-all-about)
  - [What makes Soteria unique?](#what-makes-soteria-unique)
  - [Soteria's Features](#soterias-features)
    - [**Security related Features**](#security-related-features)
    - [**Other Discord Servermoderation Features**](#other-discord-servermoderation-features)
    - [**Data and Analysis related Features** _(most of them required to operate!)_](#data-and-analysis-related-features-most-of-them-required-to-operate)
    - [**(Cross-)Community Features**](#cross-community-features)
    - [**Exclusive Features**](#exclusive-features)
  - [Usage](#usage)
    - [**Setup**](#setup)
    - [**Getting started**](#getting-started)
    - [**Setting up advanced Features**](#setting-up-advanced-features)
    - [**Server- and Usermoderation with Soteria**](#server--and-usermoderation-with-soteria)
    - [**Using Soteria for Event-Announcements using TeamUp**](#using-soteria-for-event-announcements-using-teamup)
    - [**What you can do in Soteria's DMs**](#what-you-can-do-in-soterias-dms)
    - [**Managing Access to Soteria's Commands**](#managing-access-to-soterias-commands)
    - [**Integrations in the Soteria-Client**](#integrations-in-the-soteria-client)
    - [**All available Commands**](#all-available-commands)

## What is Soteria all about?

Her primary purpose is to help out the Servers Staff Team, by taking over some parts in terms of moderation. Further she is able to use TeamUp Calendars, to write Event-Pings and Announcements.

## What makes Soteria unique?

Soteria is an allrounder when it comes to security and moderation in your community! She can fight against all kinds of threats you might know. Serverraids, Users trying to ping everyone without using "@everyone" and those who share malicious links to get access to your or your users accounts! You have a huge community spreading across different servers? No problem! Sync Soterias behavior between them! Broadcast Announcements across them! Use one TeamUp Calendar to make Cross-Server Events! All of that and many more features to come!

## Soteria's Features

### **Security related Features**

- Deletes Messages with executable files attached or linked to it immediatly and returns a Warning. This Feature is designed to prevent phishing- or other hackingattempts and **cannot be disabled!**
- Deletes Messages with Links to Websites, known to be phishing-Sites which try to grab account-data to be used for hacking immediatly and returns a Warning
- Deletes Messages where X or more Users get pinged individually _(default is 5, this is set global across all Servers. Individual Setting comming soon!)_, servermutes the Author in all Textchannels using a dedicated "strike-mute"-Role and returns a Warning. This Operation will just ping the Serverowner with a warning if no strike-mute-role is set!
- A per-server Blacklist with forbidden phrases to filter Textmessages
  - Coming Soon: An intelligent System (Codename: B.D.S) which detects iterations and alterations of blacklisted words
- A Strikesystem against users who disobey f.e. the Blacklist or the "no-executables"-rule
  - Strikes can be adjusted manually per user
  - Once a user reaches X amounts of strikes _(set per server, default is 3)_ an action will get executed on that user. _(As for now)_ This can be:
    - Servermute/deaf in Textchannels or all Channels _(done by adding the user to role, which was set up for that)_
    - Temp-/Timeban or permanent ban
    - Timeout _(soon TM)_
    - custom Action _(soon TM)_
  - Striked Messages get deleted from the server, logged in Soterias internal per-server Messagecache and logged in Soterias internal per-server Usercache, all of those contain the Original Message ID, Timestamp of Deletion, Information about the originating channel and the latest version of the content.
- Access to Soteria's Commands is reserved for the Serverowner and the inhabitants of one Role, that the Owner can set as an "auth-role". **This cannot be bypassed** when using the DM_CLI Feature.

### **Other Discord Servermoderation Features**

- The Standard Purge Command
- Profiles with different Roles to bulk-add/-remove Roles from one or more Users in one command.
- Mute/Unmute User manually

### **Data and Analysis related Features** _(most of them required to operate!)_

- Logging all Textchannels history live on read _(the history before Soteria came can be cached manually via command. EDIT: This is deprecated! In the future, Soteria will read the Chathistory when she joins the Server.)_
- Logging _(and optionally notifying)_ when a User changes his Visibility _(EDIT: This is deprecated and will soon be removed from Soteria!)_
- Logging _(and optionally notifying)_ when someone changes a User's Nickname and who changed the Nickname using the Audit-Log. This is used to keep the internal User-Cache Up-To-Date.
- Logging when someone starts typing, including the channel of the event _(EDIT: This is deprecated and will soon be removed from Soteria!)_
- Logging Messages, when they get deleted _(optionally posting their content to their original place)_
- Logging commands sent to Soteria either through DM or Server-Textchannel, including origin, author and accesslevel _(won't work cross-server!)_
- Each time Soteria throws an Error, this gets stored to a global Error-Log-File. Each Error-Report will contain the Event it happened in, the origin including Channel and Server Information, the Timestamp of occurance and a full-stack Traceback of the Error itself. This cannot be disabled! This is a little help for myself to improve, reinforce and bugfix Soteria. As soon as an occured Bug got addressed and fixed, the Errorlog will be cleared!

### **(Cross-)Community Features**

- Broadcast Messages from a Source Textchannel to Destination Textchannels on other Servers _(Like the default Announcementchannels in Community-Servers, where you can follow a channel. But with this, you dont have to make your server public.)_
- Ban people from one server and sync their banlist with other Servers using Soteria's Global-Ban-List. For this to work, you need to mount your server to an alliance. Other Servers in this alliance, can then use and modify the Global-Ban-List assigned to your alliance.
- 2FA to group Servers to one "Alliance", to use the other Community Features, mentioned above. For that, an Administrator of the Alliance's Masterserver has to work with the new Members Serverowner together to establish the Link within Soteria.
- Writing Pings for Events using TeamUp. Which Roles need to be pinged for what type of event can be adjusted. This feature also supports setting up events.

### **Exclusive Features**

- W.I.P! - The B.D.S or Blacklist Detection System in long:
  - Advanced System to detect not just the raw phrases from a blacklist, but also iterations and alterations of that using AI. _(A basic version of this, is already in place!)_
- W.I.P! - The Watchdogs:
  - Basically a framework for background tasks to be executed in set intervals, outside the Discord API's Event Loop System. Instead Python's Threading Library will be used. This will also enable Soteria to be contained in a bigger Framework, greater than just a single Discord Bot.
- The Services-Framework
  - Each of Soteria's Modules and Features can be enabled or disabled per Server using the Services-Framework.
- The Integrity-Test
  - I personally don't know if other bots provide this aswell, but Soteria has one command, with which she tests the current Server's environment for:
    - errors in configuration files
    - required roles being set up correctly.
    - required permissions in the Discord Server.
    - Read/Write/Management Access in all Textchannels.
    - beeing able to DM the Server Owner.
    - other requirements to operate, layered in OK/WARN/ERROR/FATAL.

## Usage

In this Chapter, you will learn how to setup Soteria, using an Example Server as a Best-Practice Showcase and a few examples of how she acts. Further down, you will also find a Table of all available Commands.

### **Setup**

1. Invite Soteria to your Server _(Available once in open Beta)_ using her Invitelink or - if you already are on a server with her - by viewing her profile and pressing the "Add to your Server" Button.

2. Once she has joined your Server, you need to enter the Command
   
   ~~```soteria-setupServer```~~ _Deprecated! Soteria will set up her environment automatically once she joined the Server_
   
   Once that command has been executed, Soteria will take care of setting up her internal Datastructure to be able to keep track of serverspecific settings and events. Take note, that some of her features are enabled by default when she joined the Server and other features are not. To retrieve a full list of available features, run the following Command

   ```soteria-service listall```

   **_NOTE: When you are here, Soteria will only follow Commands, given by the current Serverowner! This can be changed later on, by setting up an auth-role!_**

3. Soteria will now tell you about a few settings you want to change or set, so that her advanced features can be used. By now, only basic protection is engaged, including:
   
   - Massping Protection
   - Dot-EXE Protection
   - Phishing Protection
   
   To enable the more advanced Features, you would need to:
   
   - Enable Blacklist-based Protection using the Service Framework
   - Add Phrases/Words to the Blacklist, since that is empty by default
   - Tell Soteria which Role she needs to assign to a User when he misbehaves
  
4. Done! Soteria's basic functionality is now active in your server.

### **Getting started**

In this step, we will look at some basics, which are partially optional and of course, can be disabled.

1. Auth-Role
   
   This is what you need, when you want your Administrative Team to be able to access Soteria, since it is currently limited to you, the Serverowner, only. This is Part of the "set"-Command and is used as follows:

   ```soteria-set auth-role```
### **Setting up advanced Features**

### **Server- and Usermoderation with Soteria**

### **Using Soteria for Event-Announcements using TeamUp**

### **What you can do in Soteria's DMs**

### **Managing Access to Soteria's Commands**

### **Integrations in the Soteria-Client**

### **All available Commands**
