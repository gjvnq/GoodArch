# UI

 * Mostly some mix of GUI and CLI. (maybe like AutoCad or Emacs in which people can use commands)
 * Possibly use a 3D mouse to move between windows that overlap each other.
 * Maybe use 3D grids of icons to represent files, icons, etc.
 * Maybe actor based framework.
 * Force a client server model for applications.
 * [Object browser](https://wiki.c2.com/?ObjectBrowser)?
 * What if applications merely provided "APIs" for the user to interact with?
 * Separate the ideas of copying and cloning. Perhaps call it regular copy and entangled copy (i.e. hardlink).

## Mouse

  * If 3 buttons: select, move and options/menu.
    * E.g. you can't move an object by keeping left clicked, you need to have middle clicked.

## Client-Server Model

  * Lower latency as calculations are done on the server.
  * Allows windows to be seamlessly moved to other computers.
  * Allow access to resources (e.g. files) both of the client and the server.
    * Either different "schemas", e.g.: ```file-srv:///usr/app``` and ```file-clt:///home/user```
    * Or different subroots, e.g.: ```/client``` and ```/server```
