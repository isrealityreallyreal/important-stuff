# important-stuff
A consolidated list of commands I keep forgetting

Sort ALL mirrors according to speed and overwrite the current mirrorlist with the result in Arch Linux:
```bash
reflector --verbose --sort rate --save /etc/pacman.d/mirrorlist
```
---

Enable midi when using wine to play old games:
```bash
fluidsynth -l -s -i -aalsa -o audio.alsa.device=default gm.sf2 &
```

---

Convert a midi file and a soundfont to a flac file with fluidsynth:
```bash
fluidsynth -ni gm.sf2 file.midi -F file.flac -r 44100
```

---

Change the permissions to 0755 on all subdirectories of the current directory:
```bash
find . -type d -print0 | xargs -0 chmod 0755
```
---

Change the permissions to 0644 on all files in the current directory and subdirectories:
```bash
find . -type f -print0 | xargs -0 chmod 0644
```
---

Generate a correct keyframes file for `input.mkv` with ffmpeg (this is particularly useful for fansubbing):
```bash
ffmpeg -i input.mkv -f yuv4mpegpipe -vf scale=640:360 -pix_fmt yuv420p -vsync drop - | scxvid input_keyframes.log
```
---

Create hard links in current directory for all mkv files in source directory:
```bash
for x in path/to/source/directory/*.mkv; do ln `$(basename "$x")` "$x"; done
```
---

Kill whatever process is running on port `8080`:
```bash
kill $(lsof -t -i :8080)
```
---

Stop and remove all currently running dockers (requires root):
```bash
docker rm -f $(docker ps -a -q)
```
