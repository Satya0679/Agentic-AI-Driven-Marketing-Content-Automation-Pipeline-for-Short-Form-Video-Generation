## 1. What I was actually optimizing for

The brief framed this as "produce 3–4 reels." I read it as: *prove you can design a repeatable pipeline that produces emotionally-loaded, brand-consistent shorts at scale, with the taste of a content strategist and the discipline of an engineer.*

So I didn't optimize for "pretty clips." I optimized for three things, in order:

1. **Hook strength.** A short-form video lives or dies in the first 1.5 seconds. Every reel here was written backwards from a stop-the-scroll image.
2. **Character consistency.** This is the hardest unsolved problem in AI video. I locked Bob's identity using a triple-anchor approach (see §3).
3. **Workflow reusability.** Every choice — tool, prompt structure, file naming — is built so the next 40 reels take 10% of the effort of the first 4.

---

## 2. Story selection — why these 4 (out of 12)

I read all 12 Bob Campana stories and ranked them on three axes:

| # | Story | Hook strength | Visual potential | Universal lesson |
|---|-------|---------------|------------------|------------------|
| 1 | Hippie Trail + Beirut | 9/10 | 10/10 (Ganges cremation, Beirut tarmac) | "Privilege is a debt" |
| 2 | Hot Tub Hustle | 6/10 | 6/10 | "Luck masquerades as skill" |
| 3 | Pools + Psychology of Sales | 5/10 | 7/10 ("Stealing our dream" line) | "Sell the dream, not the deck" |
| 4 | 1990 Firewalk | 9/10 | 10/10 (glowing coals) | "Fear is fuel" |
| 5 | Micromanagement → Vegas | 5/10 | 5/10 | "Stewardship beats gofer delegation" |
| 6 | Real Estate Standoff | 6/10 | 5/10 | "Know your leverage" |
| 7 | Discount Plumbing | 4/10 | 4/10 | "Change the pricing model, change the business" |
| 8 | Helicopter / McDonald's | 9/10 | 9/10 (burger in cockpit) | "Mastery is play" |
| 9 | Restaurant / Dishwasher | 10/10 | 9/10 (steak in dumpster) | "Ego kills businesses" |
| 10 | Mormon Temple Buyout | 7/10 | 6/10 | "Hold the asset they need" |
| 11 | NZ Billionaire | 8/10 | 7/10 (broken supercar) | "No agenda is the only key" |
| 12 | River Islands Pitch | 6/10 | 6/10 | "Skills compound into legacy" |

I picked **Stories 9, 4, 8, 1** because they share a structural pattern: each opens on an *absurd or visceral image* that survives the algorithm's first-frame test. The "Dishwasher throwing steaks in a dumpster" is exactly the kind of image-hook the brief's own example called out as viral. The "Burger-in-a-helicopter" image and "Bare feet over 800-degree coals" follow the same pattern: a single frame your brain refuses to scroll past.

Stories I rejected for now (3, 5, 7, 12) are more cerebral — they'd work as long-form YouTube but not 60s Reels. They could be revisited for a "Bob's Business Lessons" carousel format later.

---

## 3. The character-consistency stack (the hardest problem)

Most AI-generated short-form fails because the protagonist's face drifts scene to scene — viewers feel the uncanny without being able to name it, and they swipe. My approach:

**Triple anchor:**

1. **Reference image, every prompt, every time.** No exceptions. Even if the model "remembers" the character, re-upload — drift is non-deterministic.
2. **Locked character-description string.** Every image prompt includes the same verbal description ("60s American man, salt-and-pepper hair, glasses, kind eyes, expressive eyebrows…"). Verbal anchor compensates for vision model variance.
3. **Style lock + seed reuse.** Pixar-style 3D animation chosen because (a) it's the most-trained-on style in modern image models, so character continuity is the most stable, and (b) it forgives small face variances better than photorealism (which exposes every drift).

**Tool choice:** **Gemini 2.5 Flash Image** ("Nano Banana") via Google AI Studio. As of June 2026 this is the best free tool for multi-image character consistency — it accepts up to 5 reference images and explicitly models identity preservation. ChatGPT's GPT-Image-1 is the backup for stubborn scenes.

**Time-shifted character problem:** Reel 4 needs 21-year-old Bob; Reels 1–3 need older Bob. I solved this by treating "young Bob" as a *separate character* with its own locked description, anchored on Bob's actual reference photo plus the prompt phrase "younger version of the same person, age 21, long hair, beard stubble." Tested in early scenes — if it diverges too far, fallback is to use a real photo of young Bob if the client has one.

---

## 4. Workflow — the actual production pipeline

```
[STORY] → [HOOK] → [STORYBOARD] → [STILLS] → [ANIMATION] → [VOICE] → [EDIT] → [SHIP]
```

### Step 1: Story → Hook (15 min)
Take the story. Identify the *single absurd image* in it. That's the hook. Write the cold-open voiceover (≤12 words, ends on a curiosity gap).

### Step 2: Hook → Storyboard (20 min)
Break into 6–7 scenes of 8–10s each. Each scene = (visual description, voiceover line, on-screen text if any). Structure: **Hook → Rising tension → Discovery → Twist → Stakes → Resolution moment → Payoff line**.

### Step 3: Storyboard → Stills (45 min/reel)
Open Google AI Studio. For each scene:
- Upload Bob's reference photo
- Paste the locked character string + scene-specific prompt
- Generate 4 variants
- Pick the best, iterate if face drifts
- Save as `reel1_scene1.png`, etc.

### Step 4: Stills → Animation (45 min/reel)
For each still:
- **Primary:** Google Flow (Omni Flash model). Image-to-video with motion prompt.
- **Fallback 1:** Hailuo AI (MiniMax) — strong on character preservation in motion
- **Fallback 2:** Kling AI 1.6 — best for natural human movement
- **Fallback 3:** Stop, use the still + Ken Burns zoom in CapCut

Generate 2 variants per scene, pick best.

### Step 5: Voice (15 min/reel)
ElevenLabs. Voice: "Brian" (mature American male, warm gravel). Settings: Stability 50, Similarity 75, Style Exaggeration 30. Paste each scene's voiceover line, download MP3.

### Step 6: Edit (30 min/reel)
CapCut desktop. Drop clips on timeline. Layer voiceovers. Auto-generate captions (Montserrat Bold, white + 4px black stroke, 60% screen height). Add music bed (royalty-free from CapCut library) at -18dB under voice. Light color grade pass. Export 1080×1920, 30fps.

### Step 7: Ship
Upload to Google Drive. Set sharing to public. Drop link in email to client.

**Total time per reel after first one: ~2.5 hours.** First reel takes ~4 hours because of iteration on character lock.

---

## 5. Tools I tested (beyond the brief's suggestions)

The brief recommended Google Flow, Google Vids, Adobe Firefly, Seedance. I tested those plus 8 more. Findings:

| Tool | Used for | Why I chose / rejected |
|------|----------|------------------------|
| **Gemini 2.5 Flash Image** (Nano Banana) | Stills (primary) | Best character consistency in free tier. Multi-image reference. |
| **ChatGPT (GPT-Image-1)** | Stills (fallback) | Best for stubborn face-lock failures. Slower. |
| **Google Flow + Veo/Omni Flash** | Animation (primary) | Brief's recommendation. Generous free quota. Image-to-video works. |
| **Hailuo AI** (MiniMax) | Animation (fallback 1) | Outperforms most paid tools on character preservation in motion. Genuinely impressive free tier. |
| **Kling AI 1.6** | Animation (fallback 2) | Best natural human motion. Slower queue. |
| **Pika 2.0** | Tested, not used | Quality dropped in 2026; weaker than Hailuo. |
| **Luma Ray 2** | Tested, not used | Beautiful but doesn't respect image refs well. |
| **Runway Gen-4** | Tested, not used | Best paid model. Excluded for free constraint. |
| **Wan 2.1** (open source) | Tested, not used | Promising. Needs local GPU; not worth setup for 4 reels. |
| **ElevenLabs** | Voiceover | Industry standard. Free tier covers 4 reels comfortably. |
| **Suno v4** | Music | AI-generated original music. Used as backup; CapCut library covered most needs. |
| **CapCut Desktop** | Editing | Free, no watermarks, auto-captions are state-of-art. |
| **Submagic** | Captions (rejected) | Better captions than CapCut, but paid trial only. |

**The non-obvious winner: Hailuo AI.** Most candidates won't have heard of it. It's a Chinese-built free video model that, in my testing, beats both Pika and Luma on character consistency. It's not in the brief's list. Surfacing it is part of the "tools beyond what's suggested" criterion.

---

## 6. The agentic pipeline — how this scales to bulk

The brief asks how this workflow becomes an *automated agentic system*. Here's the architecture I'd build:

```
                          ┌─────────────────────┐
                          │   Story Library     │
                          │  (Notion / Airtable)│
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Story Analyzer     │  → extracts narrative beats,
                          │  Agent              │     character arc, viral moments
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Hook Generator     │  → outputs 5 candidate
                          │  Agent              │     hook variants (A/B/C/D/E)
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Storyboard Agent   │  → 6–7 scenes per hook,
                          │                     │     visual + VO per scene
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Style Director     │  → picks aesthetic
                          │  Agent              │     (Pixar / Ghibli / noir…)
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Character Lock     │  ← maintains reference
                          │  Service            │     embedding (LoRA / refs)
                          └──────────┬──────────┘
                                     │
            ┌────────────────────────┼────────────────────────┐
            │                        │                        │
   ┌────────▼──────┐      ┌──────────▼──────────┐    ┌────────▼────────┐
   │ Still Workers │      │  Video Workers      │    │ Voice Synthesizer│
   │ (parallel ×7) │      │  (parallel ×7)      │    │  (ElevenLabs)    │
   │ Gemini 2.5    │      │  Flow → Hailuo →    │    │                  │
   │ ↓ QA reject   │      │  Kling fallback     │    │                  │
   └────────┬──────┘      └──────────┬──────────┘    └────────┬─────────┘
            │                        │                        │
            └────────────────────────┼────────────────────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Editor Agent       │  → ffmpeg / Remotion
                          │  (timeline assembly)│     auto-captions, music,
                          │                     │     beat-matching
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Distribution Agent │  → uploads to
                          │                     │     TikTok / Reels / Shorts
                          │                     │     with platform-tuned
                          │                     │     captions + hashtags
                          └──────────┬──────────┘
                                     │
                          ┌──────────▼──────────┐
                          │  Performance Tracker│  → 24h watch-time data
                          │  Agent              │     feeds back to
                          │                     │     Hook Generator (RLHF)
                          └─────────────────────┘
```

### Key design decisions, defended

**1. Hook Generator outputs 5 variants, not 1.**
This is the most important agent. Hooks are where reels live or die. The variants get A/B-tested on platforms and the winners train the next generation. Without this feedback loop, the system never improves — it just produces volume.

**2. Character Lock is a service, not an agent.**
It's stateless infrastructure used by every visual-producing agent. Treat it like a database — one source of truth for character identity. When Bob updates his reference photos, every downstream agent sees it immediately.

**3. Still Workers have a QA-reject loop.**
Each generated still is scored by a vision model on character similarity to the reference. If similarity < 0.85, regenerate. This is the single biggest quality-improvement lever — and it's automatable in 2026 with Gemini's vision API.

**4. Video Workers run a fallback chain, not a single tool.**
Google Flow → Hailuo → Kling → Static-fallback. If a tool fails or queues, the next one tries. This avoids the single-tool-failure bottleneck that kills brittle pipelines.

**5. Distribution Agent tunes per platform.**
TikTok captions ≠ Reels captions ≠ Shorts descriptions. Each platform's algorithm rewards different signals (hashtags, hook timing, length tolerance). The agent applies platform-specific transformations to one source asset.

**6. Performance Tracker closes the loop.**
This is what makes it agentic and not just an automated pipeline. The system learns which hook patterns hit, which voiceover tones convert, which visual styles retain. That data flows back to the Hook Generator and Style Director. After 100 reels, the system is producing better hooks than a human content strategist on cold start.

### Where humans stay in the loop (v1)

- **Story selection:** Bob (or his team) picks which stories to develop.
- **Hook approval:** A human picks 1 of 5 hook variants per story.
- **Final QA:** A human watches the assembled reel before distribution.

By v3 of the system, the QA step gets automated, and humans only review the *strategy* (which authors to onboard, which platforms to expand to). Story selection itself becomes data-driven from past performance.

### Cost model (rough, at scale)

For ~40 reels/month per author:
- Image gen: free (Gemini quota) → ~$30/mo if scaled past quota
- Video gen: ~$0–50/mo if mostly free tools, ~$200/mo on Veo paid
- Voice: ~$11/mo ElevenLabs Starter
- Editing infra: ~$50/mo Remotion render server
- LLM agents: ~$30/mo at Claude API prices
- **Total: $120–320/mo/author**

At a $1,500/mo SaaS price per author, this has 80%+ gross margin. The moat is the Hook Generator's accumulated learning, not the video gen.

---

## 7. What I'd do differently with more time

- **Test character LoRA training.** For Bob specifically, train a small LoRA on his face for use in any base model. Removes the prompt-side reference dependency entirely. Worth ~4 hours of setup for a 10-reel client engagement.
- **A/B-test 3 different aesthetics on Reel 1** (Pixar vs Ghibli vs photoreal) and let early platform metrics pick the winner. Currently I picked Pixar based on taste; data should pick it long-term.
- **Add Bob's actual voice via voice cloning.** ElevenLabs can clone Bob's voice from 3 minutes of audio. Massively raises authenticity. Free tier supports it.
- **Build the actual agent stack as a working demo,** even with 2–3 reels through a real pipeline. This would be the strongest signal in a Round 3 — moving from "I've designed it" to "I've shipped it."

---

## 8. Honest limitations

- **Visual consistency is 85% solved, not 100%.** Faces will drift slightly between models. I have not seen a 2026 free tool that fully matches human-grade character continuity. The Pixar-style choice is a deliberate hedge against this.
- **60s reels are an awkward length.** TikTok rewards <30s; YouTube Shorts rewards 45–60s; Instagram Reels works both. If the goal is single-platform dominance, length should be platform-tuned.
- **Bob's stories are long-form gold but short-form difficult.** The richest moments (Tony Robbins firewalk, Mormon Temple negotiation) lose nuance in 60s. The real product might be: short-form *as funnels to long-form* (a YouTube channel, a book, a newsletter). The reels' job is to drive subscription, not deliver the full lesson.

---

## 9. What I'd want to discuss in the interview

1. What does Bob actually want this content to *do*? Sell a book? Build a personal brand? Drive a course? The optimal hook strategy depends on the conversion target, and I made assumptions.
2. How many reels per week is the long-term cadence? That determines whether v1 is a pipeline or an agent.
3. What's the appetite for slight creative liberties (e.g., dramatizing dialogue Bob didn't actually say)? This dramatically changes hook strength.
4. Who reviews before publish? Bob himself, a manager, or fully automated by month 6?
