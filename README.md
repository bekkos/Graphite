# Graphite - NO Server-Side Anti-Cheat

This document describes a verification loop that runs every second, every unit (second) is referred to as ticks.

Graphite will count suspicious episodes. It will allow for customizable actions upon reaching a set limit of suspicious episodes within X minutes.

Register bans to a centralized database, check each player against this database on join. Server owners must register their server to get an API key and the plugin file (in an attempt to delay hackers from decompiling the anti-cheat). 

Plugin can send a notification on all suspicious episodes to a discord channel through a webhook.

Bans must be easily reversable for server administrators. Anti-cheats are never perfect, incorrect bans can happen and NO is in early development, so changes to the game must also be anticipated. Therefore it is important to be able to reverse bans on a specific server, for a specific timespan and/or a specific trigger. This will allow reversals to be performed easily, if some trigger bans legitimate players.

Prevent teleportation and speed hacks
Get the current position. Check the delta between last tick, against a table of maximum positional delta for aircraft type. If its larger than and up to 1.5 times the maximum delta, record suspicious episode. If the deviation is larger than 1.5 times the maximum, it is highly likely that the player is cheating (teleportation or massive speed hack), instantly ban.

Prevent money/rank/score hacks
Compute what the maximum one tick increment possible for score/rank/money. If value increases faster than this, record suspicious activity. 

Prevent ground unit spam
Limit number of ground units per 10m to something reasonable. If the user spambuys units >X in Y seconds, record suspicious activity.

Prevent in-air re-arming
When the player re-arms, verify that they are infact not in the air, and at a correct location for re-arming. If re-arming is attempted in an illegal position, instantly ban.

Prevent illegal aircraft acquisitions by bypassing UI.
When a player aquires an aircraft, verify that their stats allow for this acquisition (rank/money).
