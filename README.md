<p align="center"><img src="https://cdn.rawgit.com/imminentfate/compactgui/master/banner.svg" width="500"></p>
  
&nbsp;

CompactGUI is a standalone GUI to make using the Windows 10 compact.exe function easier to use. This allows games, programs and other folders to be compressed transparently (i.e they can still be used normally) with no performance loss.

This is similar to the NTFS-LZNT1 compression built-in to Windows (Right click > Properties > Compress to save space) however the newer algorithms that CompactGUI use were introduced in Windows 10 and are much more efficient, multi-threaded, and designed for use on executable programs resulting in greater compression ratios with almost no performance impact.Those with older HDDs may even see a decent performance gain in the form of reduced loading times as the smaller files means it takes less time to read programs and games into RAM.[More information can be found here](https://msdn.microsoft.com/en-us/library/windows/desktop/hh920921(v=vs.85).aspx) 

<p align = "left"><h2>Installation</h> <a href="https://github.com/ImminentFate/CompactGUI/releases"><img src="https://img.shields.io/github/release/ImminentFate/compactgui/all.svg""></a>  <a href="https://github.com/ImminentFate/CompactGUI/releases"><img src="https://img.shields.io/github/downloads/ImminentFate/CompactGUI/total.svg""></a></p>

&nbsp;

Download from **[GitHub Releases](https://github.com/ImminentFate/CompactGUI/releases)**

__*Or:*__

Install with **Chocolatey** from Powershell or CMD:
```cs
choco install compactgui
```
<p align = "left"><a href="https://chocolatey.org/packages/compactgui/"><img src="https://img.shields.io/chocolatey/v/compactgui.svg""></a></p>

## Uses
Use this tool to: 
- Reduce the size of games (e.g. Nioh: 73.9GB > 20.7GB)
- Reduce the size of programs (e.g. Adobe Photoshop: 1.71GB > 886MB)
- Compress any other folder on your computer
  
<h3 align="center"><b>See the <a href="https://github.com/ImminentFate/CompactGUI/wiki/Compression-Results:-Games">Wiki</a> for a list of <a href="https://github.com/ImminentFate/CompactGUI/wiki/Compression-Results:-Games"><img src="https://img.shields.io/badge/Games-2152-blue.svg"></a> and <a href="https://github.com/ImminentFate/CompactGUI/wiki/Compression-Results:-Programs"><img src="https://img.shields.io/badge/Programs-76-blue.svg"></a> that have been tested</b></h3>
<p>&nbsp;</p>


## Extra Features
 - Visual feedback on compression progress and statistics
 - Online integration with community-sourced [database](https://github.com/ImminentFate/CompactGUI/wiki/Compression-Results:-Games) to get compression estimates and analyses 
 - Integration into Windows Explorer context menus for easier use.
 - Drag-and-drop functionality
 - Analyze the status of existing folders
 - Shutdown/restart/sleep on completion. 

## Screenshots
<p align="left"><img src="https://i.imgur.com/3auMAtO.png" alt="compactGUI"></p>

<p align="left"><img src="https://i.imgur.com/93fk8t0.png" alt="compactGUI"></p>

## Background
Windows 10 includes a little-known but very useful tool called Compact that allows one to compress folders and files on disk, decompressing them at runtime. With any modern CPU, this added load is hardly noticed, and the space savings are of most use on those with smaller SSDs. 

As program folders and games can be shrunk by up to 60%, this has the added bonus of potentially reducing load times - especially on slower HDDs. 

More information on the inbuilt Windows function can be found [here](https://technet.microsoft.com/en-au/library/bb490884.aspx) and [here](https://msdn.microsoft.com/en-us/library/windows/desktop/hh920921(v=vs.85).aspx) or by typing `compact /q` into the commandline

This tool is intentionally designed to only compress folders and files. Whole drives and entire Windows installations cannot be modified from within CompactGUI - users seeking that functionality should use `compact /compactOS` from the commandline. 

The compression is fully transparent - programs, games and files can still be accessed as normal, and show up in Explorer as they normally would — they'll just be decompressed into RAM at runtime, staying compressed on disk.

## Options
By default, the program runs Compact with the `XPRESS8K` algorithm active. This provides a good balance between compression speed and size reduction. The default that Windows uses is `XPRESS4K` which is faster but compresses less. 
The options available are: 
- XPRESS4K: Fastest, but weakest
- XPRESS8K: Reasonable balance between speed and compression
- XPRESS16K: Slower, but stronger
- LZX: Slowest, but strongest - note it has a higher overhead, so use it on programs/games only if your CPU is reasonably strong or the program/game is older. 

### Additional Notes

In my testing, using any of the XPRESS modes has no discernible impact on CPU performance when the compressed program is run (Using an i7-6700HQ). Here's the output tests for Adobe Photoshop:
<p align="center"><img src="https://i.imgur.com/ou0D0B1.png" alt="PSResults"></p>


However, if your processor is especially old, you may find that performance is worse when folders are compressed with 8K and 16K. Use 4K instead. Despite this, I've successfully tested it on an i3-370M from 2010, and it had no issues with performance on any of the compression modes. 
