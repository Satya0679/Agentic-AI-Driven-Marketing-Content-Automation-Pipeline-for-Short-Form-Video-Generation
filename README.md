## What's in this folder

| File | Purpose |
|------|---------|
| `README.md` | This file. Execution checklist + time budget. |
| `REELS.md` | Full scripts for 4 reels: scene-by-scene image + video + voiceover prompts, paste-and-go. |
| `STRATEGY.md` | The strategy & workflow document you submit (covers workflow, taste, agentic pipeline, tool research). |
| `EMAIL.md` | The submission email template. |
| `character-ref/` | Empty — download Bob's reference photos from the client Drive link and put them here. |

---

## Pre-flight (do this FIRST — 15 min)

1. **Download Bob's reference photos** from `https://drive.google.com/drive/folders/1Dnwh_l1hYwK2VbLlSy8AxHZ0zQ_jTcon` into the `character-ref/` folder. Pick the clearest front-facing portrait as your "canonical" reference.
2. **Confirm Product Hunt task is done** (the PDF mentioned upvoting/commenting). Don't skip — it's a gate.
3. **Sign into accounts** (all free):
   - Google AI Studio (for Gemini 2.5 Flash Image / "Nano Banana") — `https://aistudio.google.com`
   - Google Flow — `https://labs.google/fx/tools/flow/`
   - ElevenLabs (voiceover) — `https://elevenlabs.io` — 10k chars/month free
   - CapCut desktop — for editing
   - Hailuo AI (MiniMax) — `https://hailuoai.video` — strong character consistency, free
   - Kling AI — `https://klingai.com` — backup video model

---

## Execution order (target: 4–6 hours)

| Step | What you do | Time |
|------|-------------|------|
| 1 | Read REELS.md end-to-end, decide which 3–4 reels to ship (Reel 1 is mandatory; pick 2–3 more) | 15 min |
| 2 | In Google AI Studio, generate the 7 scene **stills** for Reel 1 using the image prompts in REELS.md. Upload Bob's face as reference each time. Iterate until faces look consistent. | 45 min |
| 3 | In Google Flow (or Hailuo), animate each still into an 8–10s clip using the video prompts. | 45 min |
| 4 | In ElevenLabs, paste each voiceover line, pick voice "Brian" or "Daniel" (mature American male), download as MP3. | 15 min |
| 5 | In CapCut, stitch clips + audio. Add auto-captions. Add a soft music bed (CapCut royalty-free library). Export 1080×1920. | 30 min |
| 6 | Repeat steps 2–5 for Reels 2, 3, 4. Faster each time (~45 min each once you have the rhythm). | 2.5 hr |
| 7 | Upload all videos to a Google Drive folder, set sharing to "Anyone with link". Add the STRATEGY.md as a Google Doc in the same folder. | 15 min |
| 8 | Send the email (see EMAIL.md). | 5 min |

---

## Quality bar (don't ship until this is true)

- [ ] Each video is 9:16, ≥55 seconds
- [ ] Bob's face is recognizably the same person across all scenes in a reel
- [ ] Voiceover is audible and synced to scene changes
- [ ] Captions burned in (TikTok/Reels viewers watch muted)
- [ ] First 1.5 seconds has a visual that stops the scroll
- [ ] No watermarks from free tools (CapCut and Google Flow free outputs are clean; verify)
- [ ] Drive folder is publicly viewable

---

## If you run out of time

**Priority order:** Reel 1 (Dishwasher Heist) > Reel 3 (Helicopter Burger) > Reel 2 (Firewalk) > Reel 4 (Ganges).

Reel 1 alone, executed well, beats 4 mediocre reels. The brief says: *"Output quality — nothing beats this."* If you can only deliver 3, that's the minimum. Submit 3 polished + your strategy doc.

**Fallback:** If video generation keeps producing artifacts on a specific scene, replace that scene with a stylized **static still + Ken Burns slow zoom + voiceover**. Saves time, still tells the story.

---

## What you are being evaluated on (per the brief)

1. **Output quality** — final video. Iterate hard.
2. **Innovation in workflow** — show in STRATEGY.md you went beyond their suggested tools.
3. **Visual consistency** — same character across scenes.
4. **Strategic thinking** — interview discussion. Read STRATEGY.md, internalize the reasoning before the interview.
5. **Agentic pipeline thinking** — STRATEGY.md has the architecture; be ready to defend each agent's role.
