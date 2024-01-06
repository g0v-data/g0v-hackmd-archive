---
title: "2D Online Chat: Teleport Point Feature"
tags: "2d-online-chat"
---

# 2D Online Chat: Teleport Point Feature

## Proposal
"Assembly Point" is a new type of game object.  When it is placed on the ground, an NxN region will be marked, a flag (picture) will be placed.  The NxN region works as a virtual room, which has its own jitsi room.  When an user enters the virtual room, the jitsi channel will be changed.  So people in the room can here each other.

## Required Works
- [name=stimim]: Code will be uploaded to this [repo](https://github.com/stimim/2d-online-chat/tree/master), and [demo](https://stimim.github.io/2d-online-chat)

1. [WIP] Refactor Jitsi code in "index.html", create a wrapper class.
2. Add new game object type

## Open Questions
1. We have to keep the connection to the global Jitsi room, since the global room data is transmit via global channel.
    - Do we want to enable audio on global channel?
      [name=stimim]: Probably not, we can have "audio output" enabled, but not "audio input (mic)".  Otherwise the global channel would be too noisy.  Jothon admins can have permission to broadcast (in audio) on global channel.  (But this probably needs another design doc)
2. Should we "teleport" users to a "new room" (different map)?
    [name=stimim]: This approach is another way to solve the open question (1), and probably don't need to add too much features to Jitsi wrapper (we should still do the refactoring to make our code more managable).
    [name=stimim]: In this case, the assembly point becomes "teleport point", and users can add multiple teleport point on a map.  Most importantly, probably a teleport point that sends user back to lobby (global channel).
    [name=stimim]: **Cons** Because the room is changed, users can't easily "see" others outside the room.  This might not be an issue for desktop users, they can always use multiple tabs / windows, but not the case for mobile users.
    [name=stimim]: **Cons(?)** A new map have to be created on server, which is an extra step comparing to "virtual room" proposal.  But the upside of having a new map is flexibility (custmoization for different rooms).
3. ...