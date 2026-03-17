<p align="center">
  <h1 align="center">🎬 Video Subtitles</h1>
</p>

<p align="center"><strong>Generate subtitle files (.srt) from any video using GitHub Copilot CLI — free, local, no account needed.</strong></p>

---

## What does this do?

You ask Copilot CLI to generate subtitles from a video, and it does it. You get back a `.srt` file with timestamps that works in VLC, YouTube, Premiere, Final Cut, DaVinci Resolve, and most video editors.

---

## Setup (one time, ~10 minutes)

### Step 1: Install GitHub Copilot CLI

If you don't have it yet:

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

Then sign in:

```bash
copilot auth login
```

### Step 2: Install Whisper and ffmpeg

Open **Terminal** (search "Terminal" in Spotlight on Mac) and paste:

```bash
brew install openai-whisper
brew install ffmpeg
```

> 💡 Don't have Homebrew? Install it first:
> ```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
> ```

### Step 3: Add the skill

Download the `SKILL.md` file from this repo and put it in the folder where your videos are. That's it — Copilot CLI will pick it up automatically.

---

## How to use it

1. Open **Terminal**
2. Go to the folder with your video:
   ```bash
   cd ~/Downloads
   ```
3. Start Copilot CLI:
   ```bash
   copilot
   ```
4. Ask it naturally:

   > Generate subtitles for my-video.mp4

   or

   > Create an SRT file from presentation.mov in Spanish

   or

   > Transcribe all the mp4 files in this folder

Copilot reads the skill file, picks the right model, runs Whisper, and gives you your `.srt` file. Done.

---

## Examples

| What you say | What happens |
|---|---|
| "Generate subtitles for demo.mp4" | Creates `demo.srt` with English subtitles |
| "Transcribe interview.mov in Spanish" | Creates `interview.srt` with Spanish subtitles |
| "Make subtitles for all videos in this folder" | Processes every video file it finds |
| "Generate subtitles with the large model for best accuracy" | Uses the highest quality model (slower) |

---

## Tips

- **First run takes a minute** — Whisper downloads its AI model the first time (~800MB for medium). After that, it's fast.
- **Start with the default** — the skill uses the `medium` model, which is the best balance of speed and accuracy.
- **Non-English?** Just tell Copilot the language: *"transcribe this in Portuguese"*
- **Long videos** work fine, they just take longer.
- **Review the output** — AI transcription is good but not perfect. Give it a quick read-through.

---

## Troubleshooting

**"command not found: whisper"**
→ Run `brew install openai-whisper` again, then close and reopen Terminal.

**"command not found: copilot"**
→ Install Copilot CLI: `curl -fsSL https://gh.io/copilot-install | bash`

**It's taking forever**
→ Ask Copilot to "use the small model" — it's faster.

**Subtitles aren't accurate**
→ Ask Copilot to "use the large model for better accuracy." Adding the language also helps.

---

## License

MIT — use it however you want.
