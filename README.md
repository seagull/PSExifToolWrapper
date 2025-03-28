# PSExifToolWrapper
PSExifToolWrapper, or "seagull's EXIFTool Wrapper", is a PowerShell script that places a shortcut on the user's Desktop, onto which they can drag-and-drop files, folders, or both. The files dragged will then be run past Phil Harvey's [ExifTool](https://www.exiftool.org), with the user being prompted to either display the files' metadata, write the files' metadata to a text file, or scrub it altogether.  
_tl;dr: You can use this to display a file's metadata without learning any command-line flags_

## Features
- Downloads ExifTool automatically
- Keeps ExifTool up-to-date
- Searches recursively through folders dragged onto Desktop shortcut
- Can scrub the metadata off a file without having to remember the command-line flags
- Attempts to work around ExifTool's filename limitations (but not when scrubbing)
- Features not part of EXIFTool:
    - **Detects and displays NTFS Alternative Data Streams**
    - **Detects and displays Digital Signatures**
    - **Displays SHA1 and SHA256 file hashes**

## Installation & Usage
- Download the .zip file and extract the PS1
- Right-click the Start menu and open PowerShell as an Administrator
- Type in `Set-ExecutionPolicy Unrestricted` and use Y or A to confirm
  - (The Powershell.png file in the .zip file says basically the same thing)
- Place the .ps1 file in a folder, ideally one made specifically for it, somewhere your account has write access
  - (ie **NOT Program Files**)
- Right-click it and select "Run with PowerShell"
  - _Administrator privileges not required_
- The script will produce a shortcut on the Desktop called "EXIFTool"
- Launch the wrapper by dragging a file, a folder, or a combination onto that shortcut to see files' metadata

_Doesn't disabling my PowerShell execution policy pose a security risk?_
- No

## Considerations & Shortcomings
The wrapper script does its best to work around ExifTool's weaknesses with regards to filenames containing uncommon characters (eg, anything outside of [this Unicode block](https://jrgraphix.net/r/Unicode/0020-007F)), but that doesn't go as far as for scrubbing.
Sorry. You'll have to rename your files to be more boring. It'll work fine for analysis, though.

**Scrubbing does not remove NTFS Alternative Data Streams or Digital Signatures.**

I have done my best to make the script PowerShell 2.0-compatible, but I do this more as a point of pride than for any specific reason.
Feel free to run this on your ZX Spectrum but don't complain if it doesn't work.

I use the buttons Q, A and Z when I write scripts with prompts because my keyboard doesn't have labels on it and those buttons are at the leftmost so they're the easiest to peck.
It might feel a little unintuitive at first but you'll get used to it.  
My condolences to AZERTY typists. Feel free to leave an issue case, but don't worry about using fullstops – I'd hate to make you use your SHIFT keys.

## Token Screenshot
![image](https://github.com/seagull/PSExifToolWrapper/assets/241834/90163293-61fa-4324-aab9-4f631e555049)

## Changelog
* Build 21: Initial release
* Build 22: Made it so you can mash ENTER to analyse a file instead of forcing you to press Q
* Build 24: Added support for finding NTFS Alternative Data Streams, a feature EXIFTool bafflingly does not include
* Build 33:
  - Exiting the tool now closes the command window instead of making _you_ do it
  - We now pull **digital signatures** from applicable files (another feature ExifTool inexplicably lacks)
  - We now automatically pull data if only one file was loaded in, with a subsequent choice to scrub the metadata or load it into a file (no more mashing the ENTER key)
  - We now display the version of EXIFTool present on the device before updating it
  - Writing a report to a file now produces a slick file-picker instead of forcing you to enter a file path
* Build 35:
  - SHA1/SHA256 filehashes/checksums are now calculated
  - Running the PS1 file with no arguments will recreate the shortcut on the Desktop (useful when updating wrapper versions)
* Build 45:
  - New build compatible with the weird new Strawberry Perl x86/x64 builds offered on ExifTool.org
* Build 46:
  - Added `varNoInternet` flag to top of script which can be set to `TRUE` to disable attempts to access the internet
    (You will need it enabled at least once in order to _actually download_ EXIFTool)
* Build 50:
  - Fixed various issues making text output suck; now text reports work properly with no errors
  - Errors reading non-existent ADS data are now properly, 𝒈𝒓𝒂𝒄𝒆𝒇𝒖𝒍𝒍𝒚, caught
  - Social media link transferred from the fascist website to bSky
