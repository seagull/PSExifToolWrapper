# PSExifToolWrapper
PSExifToolWrapper, or "seagull's EXIFTool Wrapper", if a PowerShell script that places a shortcut on the user's desktop onto which they can drag-and-drop files, folders, or both. The files dragged will then be run past Phil Harvey's [ExifTool](https://www.exiftool.org), with the user being prompted to either display the files' metadata, write the files' metadata to a text file, or scrub it altogether.

## Features
- Downloads ExifTool automatically
- Keeps ExifTool up-to-date
- Searches recursively through folders dragged onto Desktop shortcut
- Can scrub the metadata off a file without having to remember the command-line flags
- Attempts to work around ExifTool's filename limitations (but not when scrubbing)
- **Detects and displays NTFS Alternative Data Streams** (_not_ an EXIFTool feature)

## Installation & Usage
- Download the .zip file and extract the PS1
- Right-click the Start menu and open PowerShell as an Administrator
- Type in `Set-ExecutionPolicy Unrestricted` and use Y or A to confirm
  - (The Powershell.png file in the .zip file says basically the same thing)
- Place the .ps1 file in a folder, ideally one made specifically for it, somewhere your account has write access
  - (ie NOT Program Files)
- Right-click it and select "Run with PowerShell"
- The script will produce a shortcut on the Desktop called "EXIFTool"
- Launch the wrapper by dragging a file, a folder, or a combination onto that shortcut to see files' metadata

_Doesn't disabling my PowerShell execution policy pose a security risk?_
- No

## Considerations & Shortcomings
The wrapper script does its best to work around ExifTool's weaknesses with regards to filenames containing uncommon characters (eg, anything outside of [this Unicode block](https://jrgraphix.net/r/Unicode/0020-007F)), but that doesn't go as far as for scrubbing.
Sorry. You'll have to rename your files to be more boring. It'll work fine for analysis, though.

Once the tool has completed, you'll need to manually quit the CLI window; it won't close automatically.

I have done my best to make the script PowerShell 2.0-compatible, but I do this more as a point of pride than for any specific reason.
Feel free to run this on your ZX Spectrum but don't complain if it doesn't work.

I use the buttons Q, A and Z when I write scripts with prompts because my keyboard doesn't have labels on it and those buttons are at the leftmost so they're the easiest to peck.
It might feel a little unintuitive at first but you'll get used to it.  
My condolences to AZERTY typists. Feel free to leave an issue case, but don't worry about using fullstops – I'd hate to make you use your SHIFT keys.

## Token Screenshot
![image](https://github.com/seagull/PSExifToolWrapper/assets/241834/90163293-61fa-4324-aab9-4f631e555049)

## Changelog
- Build 21: Initial release
- Build 22: Made it so you can mash ENTER to analyse a file instead of forcing you to press Q
- Build 24: Added support for finding NTFS Alternative Data Streams, a feature EXIFTool bafflingly does not include
