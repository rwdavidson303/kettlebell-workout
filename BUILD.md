# Kettlebell Workout — Build Reference

**Created:** March 2026
**Live URL:** https://rwdavidson303.github.io/kettlebell-workout/
**GitHub Repo:** https://github.com/rwdavidson303/kettlebell-workout
**Hosting:** GitHub Pages (free, auto-deploys from `main` branch)

---

## What This Is

A science-based kettlebell workout program published as a static website. Richard's existing 12-exercise routine was optimized for exercise order, set structure, and MWF variation based on peer-reviewed research. The site serves as a phone-friendly workout reference with illustrated form guides.

### Goals
- **Endurance** — Wednesday density training
- **Conditioning** — high-rep structure across all days
- **Toned body** — Friday heavier loads + Monday balanced volume

---

## Project Structure

```
kettlebell-workout/
├── index.html              # Home — program overview, exercise order, weekly overview
├── monday.html             # Monday "Standard Day" — balanced baseline workout
├── wednesday.html          # Wednesday "Density Day" — short rest, max metabolic burn
├── friday.html             # Friday "Power Day" — heavier bells, explosive intent
├── exercises.html          # Exercise Library — 12 exercises with SVG illustrations + form cues
├── progression.html        # 12-week progressive overload plan + superset option
├── css/
│   └── style.css           # Full site styling (687 lines)
├── js/
│   └── main.js             # Mobile nav hamburger toggle (17 lines)
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Pages deployment workflow
├── .gitignore
├── BUILD.md                # This file
└── kettlebell-workout-plan.md  # Source workout plan in markdown
```

Also stored in `~/Documents/`:
- `kettlebell-workout-plan.md` — original markdown workout plan
- `Kettlebell_Workout_Plan.docx` — Word document version
- `build_kettlebell_doc.py` — Python script to regenerate the Word doc

---

## Tech Stack

- **Pure HTML/CSS/JS** — no framework, no build step, no dependencies
- **Google Fonts:** Inter (400/500/600/700/800)
- **Deployment:** GitHub Actions → `actions/deploy-pages@v4` (pushes to `main` trigger auto-deploy)
- **No server-side code** — entirely static

---

## Design System

### Colors (CSS Custom Properties in `:root`)
| Variable | Value | Use |
|----------|-------|-----|
| `--navy` | `#1a3c6e` | Headers, nav, primary text |
| `--navy-light` | `#2a5298` | Hero gradients |
| `--orange` | `#e8632b` | Accent, buttons, active states, badges |
| `--orange-hover` | `#d4551f` | Button hover |
| `--bg` | `#f8f9fa` | Page background |
| `--white` | `#ffffff` | Cards |
| `--gray-50` | `#f0f2f5` | Alt section backgrounds |
| `--gray-600` | `#6b7280` | Body text, secondary |
| `--gray-800` | `#333333` | Primary text |

### Typography
- Font: Inter
- Weights: 400 (body), 500 (nav links), 600 (buttons, labels), 700 (headings), 800 (hero titles)

### Layout
- Max-width: 1200px container
- Fixed top nav (60px height)
- Responsive breakpoints: 768px (tablet), 480px (phone)
- Mobile: hamburger nav, single-column cards

### Day Color Scheme
- **Monday:** Navy gradient (`#1a3c6e → #2a5298`)
- **Wednesday:** Orange gradient (`#b45309 → #e8632b`)
- **Friday:** Green gradient (`#065f46 → #059669`)

---

## The 12 Exercises (Optimized Order)

The order follows exercise science principles:

| # | Exercise | Phase | Set Structure (Mon/Wed/Fri) |
|---|----------|-------|-----------------------------|
| 1 | Kettlebell Swings | Power | 10x10 / 5x20 / 10x10 |
| 2 | High Pulls | Power | 10x10 / 5x20 / 10x10 |
| 3 | Side (Golf) Swings | Power | 5x20 / 4x25 / 10x10 |
| 4 | Bent-Over Rows | Compound Pull | 5x20 / 4x25 / 5x20 |
| 5 | Push Outs | Compound Push | 5x20 / 4x25 / 5x20 |
| 6 | Overhead Press | Compound Push | 5x20 / 4x25 / 5x20 |
| 7 | Low Chest Flys | Accessory | 4x25 / 4x25 / 5x20 |
| 8 | Bicep Curls + Press | Accessory | 4x25 / 4x25 / 5x20 |
| 9 | Tricep Extensions | Isolation | 4x25 / 4x25 / 5x20 |
| 10 | Side Extensions | Core | 4x25 / 4x25 / 5x20 |
| 11 | Waist Halos | Mobility | 4x25 / 2x50 / 4x25 |
| 12 | Head Halos | Mobility | 4x25 / 2x50 / 4x25 |

**Total per session:** 1,200 reps (100 per exercise)

### Ordering Principles
1. **Ballistic/power first** (exercises 1-3) — highest CNS demand when freshest
2. **Compound multi-joint next** (exercises 4-6) — push/pull alternation to reduce local fatigue
3. **Accessory/isolation** (exercises 7-9) — pre-warmed muscles get deeper stimulus
4. **Core + mobility last** (exercises 10-12) — don't pre-fatigue stabilizers needed earlier

### MWF Variation
- **Monday Standard:** Balanced sets, ~30 sec rest (HR to 140-145 bpm), 55-65 min
- **Wednesday Density:** Minimal rest 15-20 sec (HR stays 150+), 45-55 min
- **Friday Power:** Heavier bells, longer rest 45-60 sec (HR to 130-135), 60-70 min

---

## Exercise Library (exercises.html)

Each exercise has:
1. **SVG stick-figure illustration** — shows start/end positions with orange movement arrows
2. **Form cues** — 6 bullet points each
3. **Usage row** — sets/reps/bell for each day
4. **Tutorial link** — button linking to external video/tutorial

### SVG Illustration Pattern
All 12 exercises use inline SVGs with consistent style:
- `viewBox="0 0 280 220"` (or 340x220 for 3-phase exercises like Curls+Press)
- Stick figures: `stroke="#1a3c6e"`, `stroke-width="2.5"`
- Start position: `opacity="0.4"` (ghosted)
- End position: full opacity
- Kettlebell: `<rect>` with `fill="#e8632b"`, `rx="3"`
- Movement arrow: dashed orange path (`stroke-dasharray="4"`) with arrowhead polygon
- Labels: `font-size="11"`, `fill="#6b7280"` under each figure
- Caption: `font-size="10"`, `fill="#b0b8c4"` at bottom

### Exercise Anchor IDs
Used for linking from workout day pages (`exercises.html#swings`, etc.):
```
#swings, #high-pulls, #golf-swings, #rows, #push-outs,
#overhead-press, #chest-flys, #curls-press, #tricep-ext,
#side-ext, #waist-halos, #head-halos
```

### Tutorial Links
| Exercise | Source |
|----------|--------|
| Swings | youtube.com/watch?v=-Kf5mKayV3E (Cavemantraining) |
| High Pulls | kettlebellsworkouts.com |
| Golf Swings | youtube.com/watch?v=iHQjOK3igfU (Cavemantraining) |
| Rows | youtube.com/watch?v=kgFPqVbYSm8 (Cavemantraining) |
| Push Outs | strongandfit.com |
| Overhead Press | youtube.com/watch?v=He8TyCcK0sc (Eric Leija) |
| Chest Flys | liftmanual.com |
| Curls + Press | strongandfit.com |
| Tricep Extensions | strongandfit.com |
| Side Extensions | youtube.com/watch?v=okOIfmvv-lo (Cavemantraining) |
| Waist Halos | youtube.com/watch?v=N4mMVG8S5Kg (Onnit) |
| Head Halos | kettlebellkings.com + liveleantv.com |

---

## Progression Plan (progression.html)

### 12-Week Cycle
- **Weeks 1-4:** Adapt to new exercise order and set structures
- **Weeks 5-8:** Increase density (shorten rest, beat session times)
- **Weeks 9-12:** Increase load (heavier bells across all days)
- **Every 5th week:** Deload (lighter bells, 75 reps/exercise, focus on form)

### Superset Option (Advanced)
After 4 weeks, pair exercises 4-9:
- SS1: Rows + Push Outs
- SS2: Chest Flys + Overhead Press
- SS3: Curls+Press + Tricep Extensions

### Equipment
- Current: Light 10-15 lb, Medium 15-20 lb, Heavy 20-25 lb
- Recommended next: 35 lb (16 kg) for swings, rows, farmer's carries
- Future: 53 lb (24 kg) when 35 lb swings feel routine

---

## Research Sources

- McGill & Marshall (2012) — Swing EMG analysis, JSCR
- ACE Kettlebell Study (2010) — Porcari & Schnettler
- Farrar et al. (2010) — Oxygen cost of kettlebell swings
- PMC9022701 (2022) — Periodized vs non-periodized KB training
- PMC9026020 (2022) — BELL pragmatic controlled trial (MWF protocol)
- PMC11349676 (2024) — Inter-set rest interval meta-analysis
- PMC7927075 (2021) — Repetition continuum re-examination
- PMC4831858 (2016) — Tabata vs traditional KB swing protocols
- Jay et al. (2011) — Kettlebell swing and low back pain, JSCR
- PMC10910645 (2024) — Comprehensive kettlebell training review

---

## Build History

### Session 1 — March 9, 2026
1. Created optimized workout plan (markdown + Word doc) from Richard's 12-exercise routine
2. Built 6-page static site with clean & modern design
3. Set up GitHub repo (`rwdavidson303/kettlebell-workout`) and GitHub Pages deployment
4. Added YouTube video embeds for exercises — discovered Error 153 (creators disabled embedding)
5. Replaced broken iframes with clickable YouTube thumbnails + SVG illustrations for exercises without videos
6. User liked SVG illustrations — replaced ALL YouTube thumbnails with consistent SVG stick-figure illustrations for all 12 exercises
7. Cleaned up unused YouTube CSS styles
8. Site live at https://rwdavidson303.github.io/kettlebell-workout/

### Key Decisions
- **Pure HTML/CSS/JS** chosen over frameworks — simple static site doesn't need React/Vue
- **SVG illustrations over YouTube embeds** — more reliable, consistent look, no third-party embedding issues
- **GitHub Pages over Railway** — free hosting, no server needed for static content
- **Multi-page over single-page** — cleaner navigation, each workout day has its own page
- **HR-guided rest** — rest periods defined by heart rate targets rather than fixed timers
