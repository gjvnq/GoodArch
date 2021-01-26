# GoodArch
Some ideas of a new architecture of computers that actually make some sense.

## Core Goals

  1. **Correctness**: any operation should always return either the correct answer or an error.
  2. **Security**: no exploits, hardware vulnerabilities nor "traps" that even experts fall into (*cof* C memory managment *cof*).
    * Maybe have a separate "security screen" that is controlled only by the OS and shows that program is currently running (if fullscreen). (show name and application UUID)
  3. **Stability**: no unexpected changes that break stuff without warning. (Use formal verification where possible)
  4. **Usability**: the system should be responsive to input and hold the user hand just enough to prevent mistakes but not so much it becomes obnoxious. Also avoid hiding stuff from the user.
  5. **Composability**: as much as possible, it should be a live system that the user can extend and modify as they see fit (like SmallTalk).
  6. **Accessiblity**: as much as possible, it should be possible to use the computer with only a keyboard and TTS.
  7. **Performance**: no time wasted with useless calculations and "fancy but unusable UI". Also multi-thread by default.
  
Provide both an OS (Operating System) and an OE (Operating Environment) to help with cross-compatibility.


## Inspirations

  * [Replacing the Unix tradition by Brian Will](https://www.youtube.com/watch?v=L9v4Mg8wi4U)
  * [Orwl: physically secure computer](https://www.hackster.io/news/orwl-an-open-source-physically-secure-computer-8830f17d5730)

## Core Considerations/Ideas

  * UUIDs and URIs for almost everything.
  * Computers shared by many people ho don't trust each other.
  * Networked "by default": assume that the computer will be using networked resources most of time but over an unreliable network. Also assume hardware may be shared over the network.
  * Encrypt and sign by default.
  * Permissions based not on user but triple (user, application, workspace). All these objects can be grouped into hierarchical groups.
  * Fine granular permissions.
  * Transactional file system that works more like a database.
  * Unified package managment that supports multiple simultaneous versions of applications and libraries. (Also allow the user to "rewire" libraries to deal with unexpected breaking changes)
  * No real distinction between files and folders (sort of like resource forks or alternate data streams).
  * Hardlinks and softlinks.
  * Track everything applications do: what files are opened, when network is used, etc.
  * Heavy usage of metadata/xattrs on files (even for file type).
  * Special characters may appear on a file "display name" but are omitted on the file path? (So `Book: subtitle?.pdf` is `Book subtitle.pdf` for file paths, e.g. `/home/user/Book subtitle.pdf`)

## Main mistakes to avoid

  * Error codes that are valid ids (see [fork() can fail: this is important](https://rachelbythebay.com/w/2014/08/19/fork/)).
  * Any stack poisoning or mismanagment.
  * Manual memory managment.
  * Object orientation.

## Main vulnerabilities to avoid

  * Hardware components reading impropper memory (see Thunderbolt and RAM dump)
  * IO sniffing. (Probably have the keyboard be integrated and delete HD encryption keys if anyone tries to disassemble the computer)

## Nice to have

  * Use the schema part of URLs to separate the "regular" filesystem from other things like devices. Example: ```serial://usb/005/002``` instead of ```/dev/usb/what-ever```.
  * Combining configuration on various levels: domain (this needs a better name), local machine, curernt user, current application, current workspace.
  * Better keyboard with dedicated keys for things like: copy&paste, ctrl for OS level things, ctrl for applications, ctrl for sub-application level (e.g. web apps)
