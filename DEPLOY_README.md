# Stay — Band Lab · GitHub Pages deployment

## Files to publish (all 11 must sit together in the repo root)

| File | What it is |
|---|---|
| `index.html` | the app (entry point — GitHub Pages serves this automatically) |
| `Vocals.mp3` | stem |
| `Drums.mp3` | stem |
| `Bass.mp3` | stem |
| `Guitar.mp3` | stem |
| `Keyboard.mp3` | stem |
| `Kick.mp3` | drum pad |
| `Snare.mp3` | drum pad |
| `Hat.mp3` | drum pad |
| `Clap.mp3` | drum pad |
| `Lyrics.txt` | lyrics, one blank line between each chunk (13 chunks) |

**Filenames are case-sensitive on GitHub Pages.** They must match exactly (capital first letter, `.mp3` lowercase). All files go in the **root** of the repo, next to `index.html` — no sub-folders.

Total size ≈ 34 MB, which is well within GitHub Pages limits.

---

## Option A — GitHub website (no command line)

1. Sign in at github.com → **New repository**. Give it a name (e.g. `stay-bandlab`), set **Public**, click **Create repository**.
2. On the repo page click **Add file → Upload files**.
3. Drag in all 11 files listed above. Wait for them to finish uploading, then **Commit changes**.
4. Go to **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**. Set **Branch = `main`**, **Folder = `/ (root)`**, click **Save**.
6. Wait ~1 minute, refresh the Pages settings screen. Your live URL appears at the top:
   `https://<your-username>.github.io/stay-bandlab/`
7. Open it. First load takes a few seconds while the stems download, then press **PLAY**.

---

## Option B — Command line (git)

```bash
# from inside the folder that contains index.html and the mp3s
git init
git add .
git commit -m "Stay Band Lab"
git branch -M main
git remote add origin https://github.com/<your-username>/stay-bandlab.git
git push -u origin main
```

Then do steps 4–7 from Option A to turn on Pages.

---

## Notes

- **Audio needs a click first.** Browsers block sound until the user interacts — that's why the first tap/press starts the audio. This is normal.
- **HTTPS is required for Web Audio** — GitHub Pages is always HTTPS, so you're fine.
- **Editing lyrics later:** edit `Lyrics.txt`, keeping one blank line between chunks. If you change the number of chunks, also update the `blockTimes` array near the top of `index.html` (one time value per chunk). The lyric chunk timings and the `blockTimes`/`drumSections`/`chordEvents` arrays are all plain, commented lists at the top of `index.html` if you ever want to hand-tune them.
- **If the lyrics don't move:** make sure the deployed `Lyrics.txt` is the block version (blank line between chunks). Even if the fetch fails, the app has the 13 chunks embedded, so it will still run.
- **Optional — smaller files:** the stems are ~7 MB each. If you want faster loading you can re-encode them to 128 kbps MP3 (e.g. cloudconvert.com) before uploading; keep the exact same filenames.
