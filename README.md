---
tags: game admin, trial admin
---
# WIP Wizden's Admin Documentation for commands and general VV stuff WIP

:::info
This document aims to bring both common and obscure commands to light for ease of use by the admin team.

Some of the examples used use arbitrary entity IDs as well as usernames for clarity. You should change these to fit your needs.
:::

[TOC]

# Classic/VV commands
:::info
Throughout this document, command permissions will be tagged with an emoji depending on the permissions needed for it.

Trialmin: :star:
Propermin: :star2:
Gamemaster: :sparkles:
Anything higher than game master: 🌠
:::
## Simple commands
### Helpful (Basics)
|P|Command|Description|Syntax|
|:-:|-|-|-|
||help, oldhelp|Returns a description of the following command and it's usage.|`help <command>`|
||list|Returns a list of all commands. Paired with a keyword, returns a list of commands containing that word.|`list <keyword>`|
||adminwho|Returns a list of online admins, excluding deadminned admins.||
||aghost|Turn yourself into an admin ghost, or back again.||
||deadmin|Removes all admin functions from the user.||
||readmin|Returns all admin functions to the user after they deadmin. Not necessary to run upon joining.||
||quit| Closes the Game.
||tpto|Teleport all targets to the first ID/user in the command.|`tpto Skarlet Chief_Engineer liltenhead 1234567`<br><br>This will teleport CE, Lilten and entity with ID 1234567 to Skarlet.
||tp|Teleports yourself to the coordinates on the specified map. Syntax goes X, Y, mapID.|`tp 14 -186 61`
||customvote|Creates a custom vote for all players, requires at least two choices. Always do this before running any important events.|`customvote "Do fish fly?" Yes No "Sometimes, I dream about cheese" Maybe`
||delayroundstart|Delay round start in seconds. Leave blank to pause, use again to unpause.|`delayroundstart 30`
||votemenu|Opens the 'Call Vote' menu.|`votemenu`
||warp|Teleports you to a warp point.|`warp evac`
||cancelvote|Cancels an ongoing vote. Autocompletes.|`cancelvote 3`

### Helpful (Adminning)
|P|Command|Description|Syntax|
|:-:|-|-|-|
||lsobjectives|Shows all objectives of the targeted user.|`lsobjectives Skarlet`|
||crewmanifest|Opens the station's manifest without using a PDA. Autocompletes the station's ID.|`crewmanifest 1234567`|
||rename|Renames the entity and also its PDA. More powerful than the rename trick.|`rename 1234567 "John Centcomm"`|
||delayroundend|Delays the round end summary in seconds. Use while the evacuation shuttle is in transit to centcom.|`delayroundend 90`|
||griddrag|Used like a force gun, moves grids around quickly. Use at your own risk, it is a toggle.|`griddrag`|
||kicknonwhitelist|Kicks non-whitelisted players from the server.|`kicknonwhitelist`|
||ban_exemption_update|Used for adding ban exemptions, eg. to exclude player from IP ban on shared connections. These exemptions require votes.|`ban_exemption_update Repo 127.0.0.1` |
||menuvis|Used to see every entity you can find when right clicking a tile|`menuvis all` to use `menuvis` to remove|


### Debug
|P|Command|Description|Syntax|
|:-:|-|-|-|
||vv|Opens graphical VV editor for given entity. Can help with accessing something you can't right-click, including server-only entities.|`vv 12345678`|
||vvwrite|Used to change a component's values.||
||vvread|Used to read a component's values. Used like vvwrite.||
||addcomp|Adds a component to an entity.|`addcomp 1234567 Jittering`|
||fixgridatmos|Resets the grid's atmos. This WILL reset pipe contents as well.<br><br>Be careful about running this on the main station, as this may also reset anything crew (e.g. atmos techs) did intentionally, like frezon production setups.|`fixgridatmos 1234567`|
||showradiation|Displays a radiation source's range, the entities it hits, and the radiation protection of entities.|`showradiation`|
### Admin Abuse
|P|Command|Description|Syntax|
|:-:|-|-|-|
||setadminooc|Changes color of your OOC messages. Persists between reconnects and servers, will not apply while `deadmin`ned.|`setadminooc #ff7777`|
||scale|Lets you change an entity's scale. 1 is the default value.|`scale 1234567 0.5`|
||playglobalsound|Plays a sound based on the given path and sets the volume.|`playglobalsound /Uploaded/Skarlet/pretzels.ogg 1`
||adduplink|Adds an uplink to a PDA and links it to a user.| `adduplink Skarlet`
||addobjective|Adds an objective to the user. Traitor objectives can be found [here](https://github.com/space-wizards/space-station-14/blob/master/Resources/Prototypes/Objectives/traitor.yml).|`addobjective Skarlet CMOHyposprayStealObjective`|
||rmobjective|Removes an objective from the user. Objective number is found using `addobjective`.|`rmobjective Skarlet 0`
||setmind|Puts the user’s soul into the ID (may require the entity to have a mind).|`setmind 1234567 Skarlet`
|:star2:|addhand|Adds a hand to the entity, not all entities are supported, requires the "Hands" component in the entity.|`addhand 1234567`
||addgamerule|Adds the chosen game event to the game. Autocompletes.|`addgamerule MeteorSwarm`
||endgamerule|Removes the chosen gamerule from the game. Autocompletes.|`endgamerule 1234567`
## Useful Commands
:::info
All of these are achievable by VVing an entity and clicking the server components instead of writing a command.
:::
aGhost privacy strings

:   Change your ghost's layer with:

        vvwrite /player/Skarlet/AttachedEntity/Visibility/Layer 7

    Putting your ghost on layer 7 puts you on a different layer than other ghosts, which means you won't be seen by anyone but those who can see layer 7.
    
    With the same notion, setting your layer to 0 would make you visible to players. Sadly, you won't be able to set your layer back to normal after the fact and players will still see you no matter what layer you set yourself to, meaning you'll need to aghost once more.
    
    You can also set the layer your eyes can see; by default, aghosts cannot see all layers. You have to manually set it with:
    
        vvwrite /player/Skarlet/AttachedEntity/Eye/VisibilityMask 7

Borg Laws
:   Check borg laws with:
    
        player:entity "nikthechampiongr" laws:get



## Upload tutorial and commands (Game Master)

|P|Command|Description|Syntax|
|:-:|-|-|-|
|:sparkles:|uploadfile|Used to upload singular files. Works anywhere on your PC.|`uploadfile Skarlet/pretzels.ogg`
|:sparkles:|uploadfolder|Used to upload a folder. The folder's name has to be one word or it won't work. [NEEDS DOCUMENTATION]|
|:sparkles:|loadprototype|Uploads a YML and runs it. Make sure you have the right material in the YML before uploading.|`loadprototype`

Uploading a prototype with `uploadfile` WIP
:    Uploading singular files is very straightforward, but if you are uploading multiple files for, example, a prototype, it can become quite tiresome. Here is an example to show exactly how to use this command to upload a prototype.

    In this example, I will upload a set of pajamas:

        uploadfile Skarlet/pretzels.ogg
    Then all you need to do is run playglobalsound the way I formatted

# VV/Components Documentation
:::info
A lot of components have had their values unlocked to admins, so a lot of customization is possible now.
:::
```
 stationID, then open StationBankAccountComponent
```
Lets you adjust the station's spesos account.


***Mind-related Components***
:   Some components are placed in the mind, rather than the entity. This allows you to change things such as antag status or custom objectives. Open the MindContainer component on a player's entity. The second string should say "Mind 1234567". Use the VV command with this to access components such as TraitorRole, InitialInfected, or RoleBriefing.

# Toolshed
Toolshed is the newer alternative of BQL and was developed by Moony.

Toolshed commands must start with a `>` to work properly. The official (unfinished) toolshed documentation can be found [here](https://docs.spacestation14.com/en/robust-toolbox/toolshed.html?highlight=toolshed#toolshed), but it is not necessary to read, nor to learn. Most toolshed commands have autocomplete.
## The Basics
:::danger
Be extremely careful when using `entities` based Toolshed commands. It is *very* easy to kill the server or end a round. If you are unsure what the command will fully do please test run it in a dev environment or empty server.
:::

|P|Command|Description|
|:-:|-|-|
||explain|You can add this in front of a command/string to show you exactly what they do and how to use them.|
|:sparkles:|entities|Returns a list of all entities. Must be used with a filter (`with` or `prototyped`) to be effective.|
||select|Takes N number of of the input list. Accepts %.|
||take|Take a N items off the top of the list.|
||pick|Takes a single random item from the list.
||with|Lists entities with the specified prototype.|
||join|Joins a list with another list. (e.g. entities1 join {entities2})|
||nearby|Takes the entity listed before it then gets entities within N tiles. (e.g. `self nearby 3`)|
||prototyped|Lists entities that are a specific prototype. (e.g. `prototyped PoweredLight`)|
||actor:controlled|Lists entities that are actively being controlled (i.e. active players).|
||self|Returns the EID of yourself.|
||do|Runs normal commands for each entity in the list provided. Must be used at end of Toolshed string. All commands must be wrapped in quotations and inner quotes must be escaped (e.g `do "thing $ID \"stuff\""`).|


## String examples

Playing with `entities`
:	`entities` lets you affect multiple entities at once with your commands. You can mix and match commands to achieve a lot of useful or fun things. In the example here, we use entities to return a BQL list of all ghosts:

       > entities with Ghost visualize
       OR
       > entities prototyped MobObserver visualize

    These particular strings are useful should you need to find out how many ghosts you have access to for an event.

```
> stations:get
```
Lets you find out what the station's entity ID is.

## Useful Toolshed Commands
Delete all space garbage: `> entities with SpaceGarbage delete`

# Code wishlist
:::warning
Feel free to add commands to this wishlist to make buttons or verbs out of them; This would be useful for common usage commands.
:::

- Verb for player objectives

# Fun
:::info
Almost all of these are going to be Game Master level Toolshed commands because that's the best way to cause chaos.
:::


Turn all MobGlockroach into ghost roles with custom text: `> entities prototyped MobGlockroach do "makeghostrole $ID GLOCKROACH \"ARRGGHHH\" \"BANG BANG POW\""`

Make everyone scream: `> entities with Actor do "osay $ID Emote screams!"`

Night shift lighting: `> entities prototyped Poweredlight do "vvwrite /entity/$ID/PointLight/Radius 4.5" do "vvwrite /entity/$ID/PointLight/Energy 0.5" do "vvwrite /entity/$ID/PointLight/Softness 3"`

# Other
:::danger
Skarlet is silly.
:::
