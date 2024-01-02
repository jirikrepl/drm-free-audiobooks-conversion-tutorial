# Audiobooks Conversion Tutorial for iPhone's Books App

### 1. Download YouTube Audio Stream Only

    yt-dlp --extract-audio "https://www.youtube.com/watch?v=fSg9qDivmUY"

Open the Opus file in IINA, open the inspector window with Cmd+I, and check the audio bitrate.

### 2. Convert Opus File to M4B
If the bitrate is around 93k, set 96k in the conversion command.
This will create an M4B file with a similar bitrate to the Opus file.

    ffmpeg -i Brian-Aldiss-Skleník-2.opus -c:a aac -b:a 96k output2.m4b

### 3. Merge M4B Files
If you have multiple M4B files, merge them with m4b-tool.

[m4b-tool](https://github.com/sandreas/m4b-tool)

    brew install m4b-tool

All M4B files in the current directory `.` will be merged without conversion.
You might need to increase the memory limit.

    php -d memory_limit=256M /usr/local/bin/m4b-tool merge --no-conversion . --output-file=merged.m4b

### 4. Edit M4B Metadata
Use the Kid3 tag editor to edit the author, book title, and book cover image.
