# bsp — Binary Script Patching

This project focuses on creating binary patch files; that is, files that encode the conversion between a source and a
target file, both of them being binary files regardless of internal structure.

Instead of following the typical approach of building a file containing the differences as pure data, this project aims
towards building scripted patches — that is, patch files that contain a script that is executed in order to perform the
patching process. While this implies that, unlike in standard approaches, patch files must be built manually, it in
turn allows arbitrarily complex patching and verification processes, including the possibility of handling multiple,
different source and/or target files, or allowing the user of the patch to select which target to produce.

This software is released to the public domain. For more information, view the (conventionally but inaccurately named)
[LICENSE] file.
