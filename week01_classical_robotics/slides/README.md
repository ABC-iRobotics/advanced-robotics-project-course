# Week 1 slides — editable Beamer package

Advanced Robotics Project (NBVHR1HBNF), Obuda University / iRob.

## Files
- `week01_classical_robotics.tex` — the deck. This is the file you edit.
- `beamerthemebark169.sty` — the iRob BARK theme, 16:9 version (from github.com/ABC-iRobotics/Beamer-template).
- `src/` — theme assets: the OE/BARK header logos, plus `animate.sty`.
- `img/UR5animation/` — 36 frames of the pseudo-inverse IK solver. The "Solving IK by nudging" slide plays them as an animation.
- `img/sim/` — figures generated with matplotlib for the "chain of frames" and IK slides. The `.gif` files are the animated versions, for a browser tab (a PDF cannot play them).
- `img/web/` — openly licensed photos from Wikimedia Commons, resized or cropped. `img/web/CREDITS.md` lists author, licence and source; the last slide of the deck carries the same credits.

## Build
```
pdflatex week01_classical_robotics.tex
```
Run it **twice**: the footer shows the slide number out of the total, and LaTeX only knows the total on the second pass (after one run every slide reads "n/1"). Overleaf reruns automatically: upload the whole folder, set the main file, compiler pdfLaTeX.
Locally (MiKTeX) the `cm-super` package must be installed, otherwise the text fonts come out as blurry bitmaps.

## How the deck is organised
Every slide is one `\begin{frame}` block, in the order they are presented. Two custom macros:

- `\takeaway{...}` — the grey "In one sentence" box at the bottom of a concept slide.
- `\wordsframe{...}` — a whole "Words to keep" vocabulary slide. One call = one slide.

Sections (`\section{...}`) drive the progress bar in the footer, nothing else.

Everything after `\thankyouforattentionframe` is **backup**, shown only if there is time: the recorded-sensor-data
demo, the humanoid-in-the-browser demo, grasping and fleet management. The sources slide and the image
credits close the deck.

## Common edits
- Reorder a block: cut and paste the whole `\begin{frame}...\end{frame}`.
- Add a slide: copy an existing frame and edit it.
- Animations: the "chain of frames", inverse kinematics and "Solving IK by nudging" slides use
  `\animategraphics` (frames in `img/sim/*_frames/` and `img/UR5animation/`). They play in Adobe
  Acrobat Reader; other PDF viewers show a still poster frame, and each of these slides links to the
  matching GIF online ("play in the browser").
- Colours used in the TikZ figures: `orange!80!black` (x axis, robot), `blue!70!black` (y axis),
  `green!50!black` (targets), `gray`.
