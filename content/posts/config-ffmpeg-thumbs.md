---
title: "Green video thumbnails on nautilus"
date: 2019-01-30T08:20:42+01:00
draft: false
---

# How to fix green thumbnails on .mkv videos

![Screenshot of a folder with green video thumbnails](/webpage/img/green-thumbs.png)

- First install ffmpeg and ffmpegthumbnailer

On Ubuntu:

1. Enable universe and multiverse repos on software app.

2. Update:
``sudo apt update``

3. Install restricted extras:
``sudo apt-get install ubuntu-restricted-extras``

4. Finally install ffmpeg and ffmpegthumbnailer:
``sudo apt install ffmpeg ffmpegthumbnailer``

On Debian:
``sudo apt install ffmpeg ffmpegthumbnailer``

On Arch and derivatives:
``sudo pacman -S ffmpeg ffmpegthumbnailer``

- Second remove thumbnail folder:
``rm -r ~/.cache/thumbnails``

- Third edit totem.thumbnailer file:
``sudo nano /usr/share/thumbnailers/totem.thumbnailer``

Change the value on ``TryExec`` with ``ffmpegthumbnailer``.

Change the value on `Exec` with ``ffmpegthumbnailer -s %s -i %i -o %o -c png -f -t 10``

Finally, the edited lines should look like this:
```
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -s %s -i %i -o %o -c png -f -t 10
```

- Finally restart nautilus:
`nautilus -q`

If the changes don't apply for all files should be useful removing again the thumbnail folder.
``rm -r ~/.cache/thumbnails``
