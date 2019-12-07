# Download Youtube videos & audio

To install "youtube-dl" first:

> sudo apt install youtube-dl

In the following examples, we use a "Amazing Grace" youtube video for illustrations.<br>
The video is available at the following link:<br>
https://www.youtube.com/watch?v=CDdvReNKKuk

# Example - download video / audio with default formats:

> youtube-dl https://www.youtube.com/watch?v=CDdvReNKKuk

To download a youtube audio with default format:

> youtube-dl -x https://www.youtube.com/watch?v=CDdvReNKKuk

# For example, download a video in mp4

To check available format for a video:

> youtube-dl -F https://www.youtube.com/watch?v=CDdvReNKKuk

Terminal output:

> [youtube] CDdvReNKKuk: Downloading webpage<br>
> [youtube] CDdvReNKKuk: Downloading video info webpage<br>
> [info] Available formats for CDdvReNKKuk:<br>
> format code  extension  resolution note<br>
> 249          webm       audio only tiny   67k , opus @ 50k (48000Hz), 1.79MiB<br>
> 250          webm       audio only tiny   83k , opus @ 70k (48000Hz), 2.32MiB<br>
> 140          m4a        audio only tiny  130k , m4a_dash container, mp4a.40.2@128k (44100Hz), 4.84MiB<br>
> 251          webm       audio only tiny  148k , opus @160k (48000Hz), 4.43MiB<br>
> 160          mp4        256x144    144p   36k , avc1.4d400c, 30fps, video only, 664.49KiB<br>
> 394          mp4        256x144    144p   51k , av01.0.00M.08, 30fps, video only, 1.40MiB<br>
> 133          mp4        426x240    240p   62k , avc1.4d4015, 30fps, video only, 1.19MiB<br>
> 395          mp4        426x240    240p   69k , av01.0.00M.08, 30fps, video only, 2.00MiB<br>
> 242          webm       426x240    240p   84k , vp9, 30fps, video only, 2.10MiB<br>
> 278          webm       256x144    144p   88k , webm container, vp9, 30fps, video only, 1.54MiB<br>
> 134          mp4        640x360    360p  123k , avc1.4d401e, 30fps, video only, 2.64MiB<br>
> 243          webm       640x360    360p  133k , vp9, 30fps, video only, 4.00MiB<br>
> 396          mp4        640x360    360p  156k , av01.0.01M.08, 30fps, video only, 4.19MiB<br>
> 244          webm       854x480    480p  230k , vp9, 30fps, video only, 6.88MiB<br>
> 397          mp4        854x480    480p  233k , av01.0.04M.08, 30fps, video only, 5.53MiB<br>
> 135          mp4        854x480    480p  242k , avc1.4d401f, 30fps, video only, 4.50MiB<br>
> 247          webm       1280x720   720p  525k , vp9, 30fps, video only, 10.81MiB<br>
> 136          mp4        1280x720   720p  528k , avc1.4d401f, 30fps, video only, 8.76MiB<br>
> 18           mp4        640x360    360p  342k , avc1.42001E, mp4a.40.2@ 96k (44100Hz), 12.79MiB (best)<br>

For example to dowload the last one with format of "mp4 640x360":

> youtube-dl -f 18 https://www.youtube.com/watch?v=CDdvReNKKuk

# Example, download a mp3 file directly from a video link

> youtube-dl -x --audio-format mp3 https://www.youtube.com/watch?v=CDdvReNKKuk

# Open video / audio files

At the moment of writing, WSL doesn't support audio, but you can easily open the files with a Windows app.

First, open Windows "File Explorer" from where your video / audio file is located:

> explorer.exe .

[Remarks: Don't forget the dot "." at the end of the command line above.]

Second, double-click your video / audio file.


