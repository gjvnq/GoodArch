# File System

The file system is basically an simple graph database (with transactions) that prioritizes bytestreams as the "main content"  for nodes.

Nodes can be both files and directories and the distinction between them is mostly irrelevant but can be eaisly obtained
by reading the number of children and the size of the bytestream.

As for notation, actual files are available by the `file://` protocol while local sockets use `socket://` and devices are available via other "protocols".

## Links

All node attributes (including children and bytestream) can be symbolic links to other nodes

## Metadata

Metadata a key value system divided into a few sections:

  * User: information provided by the user and applications.
    * E.g.: file title, comments, tags.
  * Node: information about the node itself and the bytestream.
    * E.g.: bytestream size, last modified, creation date, sync status.
  * Volume: information about the file system and volume where it is stored.
    * E.g.: file sytstem, physical device, device title, free space, features supported, sync status.
  * Security: node permissions, 

Keys are strings of up to 255 bytes.

Values are CBOR documents of up to 4 KiB, which can contain both symbolic or hard links to bytestreams.

## File Title

File titles are meant for display for the user and support both special characters and simple formatting.

Conversion from file title to filename:

  1. Replace spaces with undersocres.
  2. Replace colons and both slashes with dashes. (useful for ISO dates)
  3. Remove remaining special characters (also known as non-letter non-number).

## Filename endings

Filename endings can have special meanings.
`:[0-9]+` means a specific line,
`:[0-9]+:[0-9]+` means a specific line and column,
`:arc` means reading an archive file containing the node and its children in the default format,
`:arc:{arc-format}` means reading an archive file containing the node and its children in the format `{arc-format}`,
`:dir` means reading the node children list in the default format,
`:dir:{format}` means reading the node children list in the format `{format}`,
`:meta` means reading the node meatada in the default format,
`:meta:{format}` means reading the node meatada in the format `{format}`.
The segment `{format}` can be: `json`, `cbor`, `txt`, `xml` or similar.
The segment `{arc-format}` can be: `tar`, `iso`, `gar` (GoodArch Archive format) or similar.

When writing to `:meta`, the metadata will be patched or replaced depending on what is written. Changes only take effect when the wirte is finished.
