# audiobooks conversion tutorial for iPhone books app

### 1. Download youtube audio stream only

    yt-dlp --extract-audio "https://www.youtube.com/watch?v=fSg9qDivmUY"

open opus file IINA, open there inspector window cmd+i and check audio bitrate 

### 2. Convert opus file to m4b
If bitrate is around 93k set 96k in conversion command.
This will create m4b file with similar bitrate as opus file

    ffmpeg -i Brian-Aldiss-Skleník-2.opus -c:a aac -b:a 96k output2.m4b

### 3. Merge m4b files
If having multiple m4b files merge them with m4b-tool.

https://github.com/sandreas/m4b-tool

    brew install m4b-tool

All m4b files in current directory `.` will be merged without conversion.
Might need to increase the memory limit

    php -d memory_limit=256M /usr/local/bin/m4b-tool merge --no-conversion . --output-file=merged.m4b

### 4. Edit m4b metadata
Use kid3 tag editor to edit author, book title and book cover image
