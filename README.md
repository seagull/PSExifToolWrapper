# PSExifToolWrapper
PSExifToolWrapper, or "seagull's EXIFTool Wrapper", if a PowerShell script that places a shortcut on the user's desktop onto which they can drag-and-drop files, folders, or both. The files dragged will then be run past Phil Harvey's [ExifTool](https://www.exiftool.org), with the user being prompted to either display the files' metadata, write the files' metadata to a text file, or scrub it altogether.

## Features
- Downloads ExifTool automatically
- Keeps ExifTool up-to-date
- Searches recursively through folders dragged onto Desktop shortcut
- Attempts to work around ExifTool's filename limitations (but not when scrubbing)

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
The wrapper script does its best to work around ExifTool's weaknesses with regards to filenames containing uncommon characters (eg, anything outside of [this Unicode block](https://jrgraphix.net/r/Unicode/0020-007F), but that doesn't go as far as for scrubbing.
Sorry. You'll have to rename your files to be more boring. It'll work fine for analysis, though.

Once the tool has completed, you'll need to manually quit the CLI window; it won't close automatically.

I have done my best to make the script PowerShell 2.0-compatible, but I do this more as a point of pride than for any specific reason.
Feel free to run this on your ZX Spectrum but don't complain if it doesn't work.

## Token Screenshot

![image](https://github.com/seagull/PSExifToolWrapper/assets/241834/a1b6e9b3-98a8-4f5b-96d0-b07f3e54883a)
