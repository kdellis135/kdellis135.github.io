# kdellis135.github.io

Personal page of Jian (James) Huang, live at **https://kdellis135.github.io/**.

It is one static file, `index.html`, with no build step, plus the music excerpts in `audio/`. Edit it and push to `main`; GitHub Pages republishes within a minute or two.

To preview locally:

```sh
python -m http.server 8000
# open http://localhost:8000/
```

## Music

The background music is three short excerpts from Rachmaninoff's Piano Concerto No. 2. They are cut from public-domain recordings by [Musopen](https://musopen.org/), hosted on Wikimedia Commons. Both the music and the recordings are in the public domain; Musopen asks for a credit line, which the page shows under the Rachmaninoff list.

| File | Source on Commons | Cut |
| --- | --- | --- |
| `audio/rach2-i-theme.mp3` | [i. moderato](https://commons.wikimedia.org/wiki/File:Sergei_Rachmaninoff_-_piano_concerto_no._2_in_c_minor,_op._18_-_i._moderato.ogg) | 2:15.9 to 3:49.9, the piano's lyrical second theme |
| (not yet added) `audio/rach2-ii-climax.mp3` | [ii. adagio sostenuto](https://commons.wikimedia.org/wiki/File:Sergei_Rachmaninoff_-_piano_concerto_no._2_in_c_minor,_op._18_-_ii._adagio_sostenuto.ogg) | 8:25.5 to 10:56, the closing climax and the quiet ending |
| `audio/rach2-iii-theme.mp3` | [iii. allegro scherzando](https://commons.wikimedia.org/wiki/File:Sergei_Rachmaninoff_-_piano_concerto_no._2_in_c_minor,_op._18_-_iii._allegro_scherzando.ogg) | 2:02 to 3:31.5, the lyrical theme |
| `audio/rach2-iii-finale.mp3` | same as above | 10:35.9 to 12:10, the Maestoso return and coda (applause starts at 12:10) |

Each excerpt was encoded with ffmpeg at 128 kbps MP3 with short fades and a small volume trim, for example:

```sh
ffmpeg -ss 135.9 -t 94 -i i-moderato.ogg \
  -af "volume=-1dB,afade=t=in:st=0:d=0.4,afade=t=out:st=91:d=3" \
  -ar 44100 -c:a libmp3lame -b:a 128k audio/rach2-i-theme.mp3
```

The Bach prelude on the page is not a recording: it is synthesized in the browser with the Web Audio API.
