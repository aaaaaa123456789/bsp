# BSP compiler documentation

This document describes the functioning of the BSP compiler program included in this project, bspcomp, and the version
of the syntax that it uses. This document does _not_ intend to document the BSP format itself; the [specification] does
that, and it also documents the instruction set. Since the instruction set is documented there, duplicating it here
would be redundant; however, this document does describe the overall syntax that the compiler uses, and the various
pseudo-instructions that it supports.

[specification]: specification.md

## Invocation

The script compiler is invoked with two parameters: the source file and the target BSP filename. For instance, the
following invocation:

```
./bspcomp patch.txt patch.bsp
```

would create a `patch.bsp` file from the source code in `patch.txt`.

Note that it is impossible to use more than one source file in the invocation. However, this can be remedied by having
the main source file include the rest — this way, multiple source files can freely be combined into a single resulting
BSP file. All inclusion paths are resolved relative to the current working directory (that is, the directory from which
`bspcomp` is invoked).

## Overall syntax

This is a sample source file:

```
	define result, 0xff

Main:
	checksha1 #result, .empty_file_hash
	jumpnz #result, Error
	seek 0
	subtract #result, MessageEnd, Message
	writedata Message, #result
	exit 0
.empty_file_hash
	hexdata da39a3ee5e6b4b0d3255bfef95601890afd80709 ;hash for an empty input (0 bytes)

Error:
	print .error
	menu #result, .options
	jumptable #result
	dw .go_ahead
	dw .exit
.options
	dw .go_ahead_string
	dw .exit_string
	dw -1
.error
	string "The input file is not empty. Continue?"
.go_ahead_string
	string "Yes"
.exit_string
	string "No (abort)"

.go_ahead
	truncate 0
	jump Main

.exit
	exit 1

Message:
	db "Hello world!"
MessageEnd:
```

This script would patch an empty file into a file saying "Hello world!". If the source file isn't empty, the script
would give the option to the user of continuing anyway (deleting the data previously in the file in the process) or
aborting the patching process.

Several features of the syntax can be shown in the above sample script:

* Indented lines contain instructions (or pseudo-instructions). Non-indented lines contain labels. (Indentation can be
  any amount of whitespace; that is, spaces and/or tabs.) A label can only contain letters (uppercase or lowercase;
  they are case-sensitive), numbers and underscores; it also must not begin with a number. A label can also be preceded
  by a dot, in which case it is a local label. A label can be on its own in a line, or it can be followed by a colon,
  and optionally an instruction in the same line.
* A label can be used in an instruction (or pseudo-instruction) as a value. The value of a label is the address at
  which the label will be located when the BSP file is compiled and built; the compilation process resolves the labels
  into constant values. A local label can only be used in the same scope it is defined, the scope being between one
  global (that is, non-local) label and the next; the `.empty_file_hash` label defined in the above sample script can
  only be used between the `Main` and `Error` labels.
* Labels must be unique; local labels only need to be unique within their scope.
* Blank lines are ignored. A semicolon marks a comment; anything between a semicolon and the end of the line is ignored
  as well.
* Arguments to instructions are given after the instruction itself. The first argument is separated from the name of
  the instruction simply by whitespace; further arguments are separated from prior ones by a comma surrounded by
  arbitrary amounts of whitespace.
* String arguments to pseudo-instructions that accept them are surrounded by double quotes. A `"` character itself
  inside a string argument may be escaped by duplicating it; there are no other escape sequences in strings. (In
  particular, the `\` character has no useful effect other than representing itself in a string argument.)
* Numerical constants may be written explicitly (in decimal, in hexadecimal preceded by `0x`, or in octal preceded by
  `0`; negative constants will be converted to unsigned constants in the usual two's complement form), or they may
  be represented by a label or a definition. A label can only be used where a word constant (or a word-sized immediate
  argument) would fit; a definition may be used in any context where a number is required, including a variable number.
  Hence, `#result` is simply a clearer way of writing `#255` in the above example, since `result` has been defined to
  represent `0xff` (which is 255).
* Variables are written in the form `#<number>`, where `<number>` is either a number or a defined symbol representing a
  number. Therefore, `#255` means variable number 255. Note that variable numbers are byte-sized; a number greater than
  255 will be silently truncated to fit.
