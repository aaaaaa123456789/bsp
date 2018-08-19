# BSP specification versions

This document aims to both describe the versioning system to be used for the BSP specification, and to act as a
changelog that briefly describes all past versions and points to them.

Any version listed in this document is considered immutable; the version and revision number shall be a persistent
identifier for that specific version.

  * [Versioning scheme](#versioning-scheme)
  * [Changelog](#changelog)

## Versioning scheme

Version numbers for the specification consist of three numbers separated by dots followed by a single revision number.
The version numbers are respectively called the major, minor and patch version numbers. For instance, a version number
of 23.45.67, rev. 8901 has a major version number of 23, minor version 45, patch version 67, revision 8901.

The meaning of the numbers is as follows:

* The major version number indicates that the specification is not compatible with prior versions. As of the time of
  writing, this number is 0, meaning that the specification is not yet considered stable; major version 1 will be the
  first stable version, and any further major versions may be completely incompatible with prior ones.
* The minor version number increases when additional features are added to the specification, without breaking already
  existing ones. For as long as the specification remains in major version 0, this will also be incremented for
  breaking changes; however, such changes should be rare and clearly indicated in the changelog.
* The patch version number increases when the specification is updated to fix corner cases, undefined behavior, or
  other updates that do not constitute new features and should not alter the behavior of strictly conforming code.
* The revision number is merely an update counter, and increases with every change to the specification. The revision
  number may be changed on its own, without modifying the version numbers, if the change is completely trivial (for
  instance, spelling fixes) or if it only changes the way in which already-present information is shown. Any
  implementations written to conform to a specific version number should not be affected by an update that only
  increments the revision number.

Note that, since the revision number is never reset, it may be used by itself to identify a single version of the
specification. However, this does not convey as much information as the full version number.

## Changelog

#### [Version 0.5.2, rev. 37 (19 August 2018)](https://github.com/aaaaaa123456789/bsp/blob/master/specification.md)

* Adds a version number to the specification and a link to the (newly-written) changelog

#### [Version 0.5.2, rev. 36 (14 August 2018)](https://github.com/aaaaaa123456789/bsp/blob/b4fb39c8a62077a0cdd11a930b64ae2bca08999e/specification.md)

* Adds an index to the specification

#### [Version 0.5.2, rev. 35 (28 July 2018)](https://github.com/aaaaaa123456789/bsp/blob/d9936fba051f11c01b3deda6e36f65c3f5addc52/specification.md)

* Adds a note that mandates overflows in the calculation of the effective address for `jumptable` to result in fatal
  errors

#### [Version 0.5.1, rev. 34 (22 September 2017)](https://github.com/aaaaaa123456789/bsp/blob/c2afec8713dd13f95f74c8c685008e455d2f2965/specification.md)

* Fixes various writing errors (grammar mistakes, unclear sentences, etc.) throughout the specification

#### [Version 0.5.1, rev. 33 (9 March 2017)](https://github.com/aaaaaa123456789/bsp/blob/e1f011bce4c5f3f3ef02d1bf5d71f5904fbda42b/specification.md)

* Fixes a formatting error in the description of `longmulacum`

#### [Version 0.5.1, rev. 32 (5 March 2017)](https://github.com/aaaaaa123456789/bsp/blob/acd7fb099e1fd280e219ea1a455f14f67ab0d2d3/specification.md)

* Adds a note specifying the behavior of the `getbyteinc`, `getbytedec`, `gethalfwordinc`, `gethalfworddec`,
  `getwordinc` and `getworddec` instructions when both of their arguments point to the same variable

#### [Version 0.5.0, rev. 31 (14 February 2017)](https://github.com/aaaaaa123456789/bsp/blob/10a6845f2a6e530844377e908874d1665b9b9c54/specification.md)

* Adds 64-bit arithmetic instructions

#### [Version 0.4.0, rev. 30 (5 February 2017)](https://github.com/aaaaaa123456789/bsp/blob/5c7370006a036bc2eedae8490fb97d0d328f1844/specification.md)

* Fixes another grammatical mistake in the description of instructions that read from the file buffer

#### [Version 0.4.0, rev. 29 (5 February 2017)](https://github.com/aaaaaa123456789/bsp/blob/b5284bb6ad6270203604ab9877e529082e85fbd3/specification.md)

* Fixes a grammatical mistake in the description of instructions that read from the file buffer

#### [Version 0.4.0, rev. 28 (5 February 2017)](https://github.com/aaaaaa123456789/bsp/blob/a562f943830f3d0b11a7ab4d54c839c9e7492aa0/specification.md)

* Adds the `getfilebyte`, `getfilehalfword`, `getfileword` and `getvariable` instructions

#### [Version 0.3.0, rev. 27 (30 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/5abca7bf6a391f020ace1a35a6f2489bae73f5e5/specification.md)

* Fixes several grammatical errors in the description of `checksha1`

#### [Version 0.3.0, rev. 26 (14 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/09ca5dfc562e2610ee83ca8e4cac464ecb28d8b7/specification.md)

* Fixes formatting errors in the description of the bit-shifting instructions

#### [Version 0.3.0, rev. 25 (14 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/1062993bfaac708ba449b4900707b8f7d9b0fef4/specification.md)

* Fixes a formatting error in the description of `getstacksize`

#### [Version 0.3.0, rev. 24 (10 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/8eff45b9cd3bd9cdb8c08145b1992eb3dcf80dc5/specification.md)

* Improves the formatting of the table listing the bit-shifting instructions

#### [Version 0.3.0, rev. 23 (10 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/d41003113e8456b7cb45859f5ca3ffd96c21b76d/specification.md)

* Fixes a grammatical error in the description of `rotateleft`

#### [Version 0.3.0, rev. 22 (10 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/131d484579cd82c2238c08d2fddbaa8ad755a872/specification.md)

* Adds the `setstacksize` and `getstacksize` instructions, and the bit-shifting instructions

#### [Version 0.2.2, rev. 21 (2 January 2017)](https://github.com/aaaaaa123456789/bsp/blob/f816e066a69b00497f05755f37caeed1b32576c8/specification.md)

* Fixes a few typos and similar errors

#### [Version 0.2.2, rev. 20 (12 December 2016)](https://github.com/aaaaaa123456789/bsp/blob/15f3ca40120e10add4b773e58d23aa629922d804/specification.md)

* Adds notes clarifying the interaction of `poppos` and the `seek` family of instructions with a locked current file
  pointer

#### [Version 0.2.2, rev. 19 (12 December 2016)](https://github.com/aaaaaa123456789/bsp/blob/82f51ba1bf867c7bae0011a73c04fc18732147ee/specification.md)

* Updates `stackread` and `stackwrite` to accept negative stack positions

#### [Version 0.2.1, rev. 18 (12 December 2016)](https://github.com/aaaaaa123456789/bsp/blob/7fd8f7aded664d92f7f226def3457eea065ca1ce/specification.md)

* Amends the description of `bufchar` to require engines to accept spaces

#### [Version 0.2.0, rev. 17 (12 December 2016)](https://github.com/aaaaaa123456789/bsp/blob/4ad5af7bc9ea151e55d6817d50edf65ba8145074/specification.md)

* Adds a message buffer to the execution environment of the patch
* Adds the `bufstring`, `bufnumber`, `bufchar`, `printbuf` and `clearbuf` instructions
* Updates the description of the `bsppatch` instruction regarding behavior of the newly-introduced message buffer

#### [Version 0.1.1, rev. 16 (2 December 2016)](https://github.com/aaaaaa123456789/bsp/blob/15b63746acecadd7569e12944a8480b79545c2e4/specification.md)

* Fixes an error in the argument lists for the `truncate` instruction

#### [Version 0.1.0, rev. 15 (29 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/454cd7d24c05566f86de599f4a707b3253986acb/specification.md)

* Fixes a formatting error in the description of the `bsppatch` instruction

#### [Version 0.1.0, rev. 14 (29 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/750ab28bff50c928ab8cdda694fcba54430f8238/specification.md)

First complete version of the specification.

* Adds a description for the `bsppatch` instruction

#### [Version 0.0.8, rev. 13 (29 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/fdd6daf6024efd67759ca965247bd2df502d37d9/specification.md)

* Further improves the wording in the description of the `ipspatch` instruction

#### [Version 0.0.8, rev. 12 (29 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/575b7e90d5bff4c8cb62d2f3e984a0d587016736/specification.md)

* Fixes the wording in the description of the `ipspatch` instruction

#### [Version 0.0.8, rev. 11 (29 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/86c30c5fdca1935935da4d7ea87b73f7f4765ad8/specification.md)

* Updates the argument lists for the `ipspatch` instruction
* Adds descriptions for `ipspatch` and `checksha1`

#### [Version 0.0.7, rev. 10 (28 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/d6e900b07f8fe0f8d962eaabc6b0ee9985d13428/specification.md)

* Fixes grammatical mistakes in the descriptions of the `pushpos` and `poppos` instructions

#### [Version 0.0.7, rev. 9 (28 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/79cff74a8fba55e587ead3e2dffc7cb9c6ff9d5d/specification.md)

* Specifies the behavior of the `print` instruction when an invalid string is encountered
* Adds a note mandating that one-option menus must be shown to the user
* Adds descriptions for the `writedata`, `xordata`, `length`, `truncate` and `truncatepos` instructions, and for the
  instructions dealing with manipulating or retrieving the current file pointer

#### [Version 0.0.6, rev. 8 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/9f6a712692ef9303b37be36ea9e55ef589f27fe1/specification.md)

* Adds descriptions for instructions that read from and write to the file buffer

#### [Version 0.0.5, rev. 7 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/a143d24f3736edfe3e9ee91c14efd5bc4d923112/specification.md)

* Fixes the formatting of a section header

#### [Version 0.0.5, rev. 6 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/97da86ec40c60c46d16971ebc8719313b398d84d/specification.md)

* Fixes the writing in the description of instructions that read values from patch space
* Adds a note in that section regarding compiler behavior

#### [Version 0.0.5, rev. 5 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/a8fb59ee3e9a6ae3fbb1ec3d374122e56f1770a1/specification.md)

* Adds descriptions for advanced stack operations and instructions that read values from patch space

#### [Version 0.0.4, rev. 4 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/064a7cf95efae472b325759de22071b522c7bea8/specification.md)

* Updates the argument lists for `menu` and `jumptable`
* Adds descriptions for conditional jumps, `menu`, `print`, `exit` and `jumptable`

#### [Version 0.0.3, rev. 3 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/87d74cf3669c1a4040887aa03e41c728226b5297/specification.md)

* Adds descriptions for arithmetic instructions, basic control flow, `push` and `pop`

#### [Version 0.0.2, rev. 2 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/2f26f24664bd5a6e8b204f9e1e7b9a2d6a522e79/specification.md)

* Adds a list of all instruction names and describes the `nop` instruction

#### [Version 0.0.1, rev. 1 (26 November 2016)](https://github.com/aaaaaa123456789/bsp/blob/0e871909f4f47d1bdd5c75fa8d5732adcc010b37/specification.md)

* Initial draft version of the specification; contains an introduction and the initial instruction list
