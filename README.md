# शब-ए-ग़ज़ल · Shab-e-Ghazal

A one-page browser mehfil for ghazal listeners. No build step, no dependencies
to install, no audio files.

## Running it

Do not double-click `index.html`. YouTube will not load a playlist into a
`file://` page, so the play button does nothing. Serve the folder instead:

    cd ~/Downloads/gazal
    python3 -m http.server 8000

Then open <http://localhost:8000>. The page detects `file://` and shows a red
banner with this command if you forget.

## What is in here

    index.html        the entire site
    img/              optional drop-in background art (see img/README.txt)

## The pieces

**The scene.** A moonlit haveli courtyard drawn as inline SVG: three lit arches,
hanging lanterns, a chandni spread on the floor, harmonium, tabla and two
candles. Drop a painted image into `img/` to replace it.

**The mood switches.** Three mutually exclusive ambiences, each with its own
canvas particles, colour wash and sound, all synthesised in the browser with the
Web Audio API.

| Switch  | Look | Sound |
|---|---|---|
| बरसात   | rain, splashes, lightning bolts and screen flash | filtered noise plus thunder every 6–15s |
| शमा     | embers drifting up, warm amber wash | occasional fire crackle |
| चाँदनी  | slow moonlit motes, cool blue wash | faint night air |

**तानपूरा** is independent of the three, so it can sit under any of them. Four
strings tuned around C# are plucked in a 1.15s cycle through a feedback delay.

**वाह वाह** throws mehfil appreciation across the screen and plays a short
crowd murmur.

**The player** is the YouTube IFrame API with the video hidden offscreen. Four
ghazal stations, shuffled on load, auto-advancing. The spinning disc shows the
current video's thumbnail behind a shellac-groove overlay.

**The shers** rotate every 11 seconds from a list of twelve couplets in
`SHERS`, each attributed to its poet.

## Changing things

Stations live in the `<select id="stationSelect">` options and in
`STATION_LABELS`. Both keys are YouTube playlist IDs — add a row to each to add
a station.

Couplets live in the `SHERS` array. Poet names, FAQ entries and the singer grid
are the `USTAAD` and `FAQ` arrays just below it.

## Keyboard

    Space   play / pause
    n / p   next / previous ghazal
    ← / →   seek 10s, when the progress bar has focus

## Notes

Playback needs a click first — browsers block autoplay, and the Web Audio
context only starts on a user gesture. Music is streamed from YouTube and
belongs to the respective artists and labels.
