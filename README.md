# CP77_CR2W

A 010 Editor binary template for editing Cyberpunk 2077 game files, with a collection of scripts

**Basic Info:**

This is my binary template (a file-parser for 010 Editor) CP77_CR2W.bt, used for reading generic CR2W files. It should be able to parse the majority of Cyberpunk 2077 non-buffer files and read whatever values are inside. Classes are properly nested and variables are displayed in the following format: 

[type]        [identifier]  =  [value] (string for that value)


for example, a color value:

Uint8          Red  =  0.788325


-After changing a value such as color or some string indexes, press F5 to refresh the display of those colors or strings in the template. 
-Double click directly on the "[identifier] = [value]" part of a closed struct and type in a number to change the [value] part to that number
-You can change a CName string and the corresponding hash will automatically be updated
-Check the top of the file for a list of options

-Open "Path" files that exist on your computer by attempting to write a spacebar to their Value fields.
-You can set your extracted archives path at the top of the file, as "extractedDir"

Get 010 Editor from https://www.sweetscape.com/

------------------
# Scripts:

You can use CP77_CR2W_Erase.1sc, CP77_CR2W_Paste.1sc, and copyBytes.1sc to quickly change CR2W files to be however you want.
Install the scripts with Scripts -> View Installed Scripts first. 
Then set them to the keyboard shortcuts ALT+SHIFT+C for copyBytes.1sc, ALT+SHIFT+V for CP77_CR2W_Paste.1sc, and ALT+SHIFT+X for CP77_CR2W_Erase.1sc

For the paste script: 
-Add a new CName by highlighting an existing CName and using the script. A prompt will come up asking you to name it. It will generate a matching hash for it as well

-Add a new CR2WImport / file by selecting CR2WProperty and using the script, or by selecting an existing CR2WImport and running it. It will ask you for the new file path to add

-Add a new CR2WExport by selecting one of those and running the script. It will be a blank slate, you must edit its name and add properties to the class it creates yourself

-Add any property by copying another property with copyBytes.1sc, then pasting it over some other property elsewhere in the same file

-Add a new CR2WBuffer by selecting another CR2WBuffer in the template (or by selecting "CR2WTable") and running the script. The buffer must be configured to be loaded by a class using a DataBuffer property, and then a new buffer file must be created and rebuilt into your file using CP77Tools


# Unkarkify.1sc Buffer Decompression Script:

-You can use this script to decompress the buffers of a CR2WFile. The template will read the decompressed data if it contains CR2W data of its own within. You can also use the template to save the decompressed buffer data as a .buffer file, for use when rebuilding with CP77Tools. To do so, input anything into the "[Input Here to save as File]" field for the decompressed buffer.

-You must put oo2ext_7_win64.dll next to your installed CP77_CR2W.bt or in your 010 Repository folder for this script to work

-Thanks to Loomy for making Unkarkify.1sc


# Rebuild.1sc Buffer Compression script:

-You can use this script to re-compress buffers decompressed by Unkarkify.1sc or ones detected as loose buffer files next to your CR2W file (if they have the correct "[extension].[bufferNumber].buffer" name)

-It will automatically re-compress decompressed buffers in the file, or will replace them with buffer files if those file are detected.
