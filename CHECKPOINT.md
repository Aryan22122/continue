# Project Checkpoint

## Goal
Generate the complete, runnable Blender Python (bpy) production pipeline for the 60-second short film "The Snowman's Daughter". 

## Rules for the AI
1. Do NOT try to install or run Blender. You are only writing the text files.
2. Create the following files in the root of this repository: `make_film.py`, `shotlist.md`, `render_all.sh`, and `ffmpeg_commands.txt`.
3. Commit and push after creating each file so progress is saved.
4. If you finish all files, update this CHECKPOINT.md to say "ALL DONE".

## Next step
Execute the following prompt to generate the files:

---
You are a senior Blender technical director. Produce a complete, runnable Blender Python (bpy) production pipeline for a 60-second stylized short film.

TARGET: Blender 4.2+, EEVEE Next, 1920x1080, 24fps, 1440 frames.
Hardware: mid-range laptop GPU. Optimize aggressively for render speed.

FILM BEAT SHEET (frame ranges at 24fps):
  Shot 1  1–192    Dusk, empty yard, heavy snow. Lone snowman, faceless.
                   Slow low-angle push-in. Cold blue palette.
  Shot 2  193–432  A little girl in a red coat walks in. She presses coal
                   eyes and a smile into his face, ties her red scarf on him.
                   Medium two-shot. His head tilts slightly toward her.
  Shot 3  433–912  Night montage: snowball fight, sledding, spinning in snow,
                   sitting side-by-side looking at a lit window.
                   Warm amber grade. 6–8 quick cuts.
  Shot 4  913–1104 She falls asleep against his leg. He removes his own scarf
                   and drapes it over her. Close on his hand.
  Shot 5  1105–1248 Dawn breaks. Sunlight hits. THE GIRL MELTS into a puddle.
                   She was made of snow all along. The snowman does not melt.
                   Slow reveal. Warm key light, long shadows.
  Shot 6  1249–1440 He bends, picks up the red scarf, lays it over the puddle,
                   turns, and walks out of frame into the trees. Fade to black.

BUILD REQUIREMENTS:
1. ONE file, make_film.py, organized as: clear_scene(), build_environment(),
   build_snowman(), build_girl(), build_props(), setup_lighting(),
   setup_cameras(), animate_shot_01()...animate_shot_06(), setup_render(), main().
2. Idempotent. Runs headless: blender -b -P make_film.py
3. LOW-POLY / STYLIZED. Primitives + subdivision only. NO external assets
   required to run. Where a nicer asset would help (rigged girl, cloth sim),
   insert a clearly marked # TODO: SWAP ASSET comment with the exact slot.
4. Materials: Principled BSDF. Snow = procedural noise + bump. Night palette
   cool blue; dawn palette warm amber. Use a single ColorRamp driver or
   scene custom property so I can shift the grade globally.
5. Snowfall: geometry nodes, instanced, seeded, looping. Include a density
   control and a "heavy/light" toggle.
6. Cameras: one camera object PER SHOT, bound to timeline markers so
   "Render All" works out of the box. Print the shot list to console.
7. Lighting: night = cool moon key + warm practical from a house window.
   Dawn = warm sun, low angle, long shadows. Add low-density volumetric fog
   for mood (cheap settings only).
8. Render: EEVEE Next, PNG sequence to //render/frames/. Samples 32, motion
   blur on. Include a CONFIG dict at the top with PREVIEW = True (renders
   480x270, 8 samples, every 4th frame, for fast iteration).
9. Also output: render_all.sh (headless render), and an ffmpeg command file
   producing film.mp4 (H.264) AND film_vertical.mp4 (1080x1920 reframed).
10. Wrap risky operations in try/except with clear console messages.
    Print progress per shot.
11. End of script prints a MANUAL POLISH CHECKLIST (rigging, facial
    expression, sound design, color grade pass).

DELIVERABLES IN YOUR RESPONSE:
  - make_film.py (complete, no placeholders left unimplemented)
  - shotlist.md (frame ranges, camera, action, notes)
  - render_all.sh
  - ffmpeg_commands.txt
  - A "How to Run" section, 5 steps max.

Do not ask me questions. Make reasonable assumptions and flag each one in a
comment starting with # ASSUMPTION:. Keep the code runnable end to end.
---
