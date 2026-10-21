# gelerpixcube — Project Spec

> Source of truth for **what** we build, and the log of how the project evolves.
>
> Leo designs the creature, the cube and the setting. Claude writes the code that puts them together.
> Items marked **(proposed)** are suggestions from Claude that still need a yes/no from Leo.
> Unresolved choices are listed in [Open questions](#open-questions). When one is settled, update this file and log it in [Progress log](#progress-log).

## 1. The brief

School project **"Press to feel"** (Devine — Digital Design & Development, 2026–2027).

- Create an experience, digital or hybrid, that a person interacts with through **exactly one button**, and that reliably makes them feel a targeted emotion.
- Outputs can be text, sound, images, movement / motion and light.
- AI is allowed: human-first, AI in the loop.
- Three phases: **Idea** (2 weeks) → **Experiment** (5 weeks) → **Build** (4 weeks, over the winter break). Document the process (template on Leho).

## 2. Concept

**Emotion: anticipation.** The user waits for an outcome they expect, and gets one they don't.

The user sits on a chair at a desk in a dark room, seen in first person. Across the desk, a creepy but intriguing creature sits with a Rubik's cube. The user presses a button: the cube is shuffled, and the creature starts solving it. The user can't control the solve, only disturb it, so all they can do is watch the faces come together and wait. When the creature is done, it scratches a tally mark on the wall.

The ending is **unexpected** and comes from the solve itself: the cube can't be solved, or something strange happens at the moment all faces should be complete. Finding the right ending is part of the experiment phase (§7).

The experience should feel like it has a **narrative**, and the creature should feel **alive**: no words, only sounds (groans, anger, a "ta-da"…).

### 2.1 Answers to the pitch feedback

The teachers' questions, to answer during the experiment phase:

| Question | Current answer |
| --- | --- |
| What is the creature, and why? | _to write_ (the creature designs are still being tested, see §4.1) |
| What links the creature to the cube? | _to write_ |
| What exactly are we waiting for? | Watching the faces come together, without being able to influence the solve. |
| Why would I press the button again? | _to write_ |
| How does the user know they can press? | _to write_ |
| Is the creature busy when nobody is there? | _to write_ |
| Does it change over time? | _to write_ (the tally marks could carry this) |

## 3. The button

One **physical button**, built into a Rubik's cube placed in front of the user, so the real cube mirrors the one on screen.

| Input | Effect |
| --- | --- |
| Press | Shuffle the cube; the creature starts solving. |
| Long press (hold) | A longer shuffle. |
| Press during a solve | The creature reacts at random: it speeds up, or groans in anger. |
| Double press | The creature gets mad and throws the cube at the user. |

Hardware **(proposed)**: an arcade button or microswitch inside a hollowed-out cube, wired to a board that acts as a USB keyboard (Arduino Leonardo / Pro Micro or Raspberry Pi Pico). The browser just receives a key press, and the experience also works with the keyboard for testing.

## 4. The creature

- Living, creepy and intriguing. No words, only sounds.
- Reacts with some randomness, so it never feels scripted.
- **2.5D (proposed, to test):** the body and head are flat 2D cut-outs (layered PNGs: head, jaw, eyes, torso…), and the **arms are 3D** and handle the 3D cube. The seam between the 2D and 3D parts is the collage effect. Facial expressions are swapped images, like stop-motion replacement faces.
- Behaviours: idle (fidget, sleep, stare at the user), notice a press, shuffle, solve, solve fast, angry groan, throw the cube, celebrate, scratch a tally mark, the ending(s).
- The code keeps the creature's look separate from its behaviour, so different designs can be swapped in and compared **(proposed)**.

### 4.1 Creature designs to test

The design isn't decided yet. Leo will try several and pick during the experiment phase:

| Design | Idea | Reference |
| --- | --- | --- |
| Bones | A creature made of bones, in the spirit of Švankmajer's stop-motion. | _to add_ |
| Busó | Carved wooden mask, horns, shaggy sheepskin, human hands. From Leo's culture, so it could be a personal connection. | `docs/references/buso.png` |
| _more to come_ | | |

## 5. The cube

- A real 3×3 cube in code: 27 pieces with real face turns, so shuffles and solves are genuine.
- Leo designs its look (stickers, wear, materials).

## 6. Art direction

- **PS1 / low poly**: low resolution, small crunchy textures, wobbly vertices, low frame-rate animation (around 12 fps, stop-motion feel).
- **Digital collage**: 2D and 3D mixed.
- Inspiration: Geoffrey Lillemon, Jan Švankmajer, Inscryption, Buckshot Roulette, the Busó. Inspiration only: no assets taken from them.

Reference screenshots are in `docs/references/`. That folder stays on Leo's computer only (see `.gitignore`), because the repo is public and the images are other people's work.

### 6.1 From Inscryption (`inscryption-*.png`)

- First-person seat at a wooden table. The table is the stage and leads the eye to the creature.
- Darkness does most of the work: the creature is barely visible, often just **glowing eyes** and the parts the light touches.
- Warm candle light, crushed blacks, a red/orange tint, grain.
- The creature's hands come **towards the camera**, big in frame. A cube thrown at the user should feel like this.

### 6.2 From Lillemon (`lillemon-*.png`)

- Photo cut-outs with hard, slightly jagged edges, layered at clashing scales.
- Saturated colour, sparkles and particles, retro web / OS frames (address bar, window chrome, small inset videos).
- Creatures with animal heads and **long, stretchy, textured limbs**. In *Possession of Chess*, two creatures play a game across a table, which is very close to this project. Its stretched pink arms are a good model for 3D arms on a 2D body.

### 6.3 Combining the two (proposed)

The two references pull in opposite directions: Inscryption is dark and warm, Lillemon is bright and saturated. A way to use both:

- The room is Inscryption-dark. Only what the light touches (the creature, the cube) is in full Lillemon collage colour.
- The **unexpected ending** could break the mood: the dark room tears open into a Lillemon collage (a "WTF" moment the teachers would like).

## 7. Experiments

Things to try during the experiment phase:

- [ ] Endings: the cube can't be solved / something unexpected happens when it's "solved" / _more to add_
- [ ] Roulette wheel instead of (or alongside) the cube: the anticipation of landing on your own result
- [ ] Creature designs: bones (Švankmajer), Busó, others (§4.1)
- [ ] 2D creature with 3D arms (§4)
- [ ] Physical button inside a real cube
- [ ] Idle behaviour: what the creature does when nobody presses

## 8. Assets checklist

Made by Leo. 3D models exported from Blender as `.glb`; sounds as `.wav`.

- [ ] Creature body: layered 2D cut-outs (PNG with transparency)
- [ ] Creature face swaps: eyes, mouths, expressions
- [ ] Creature arms: 3D, rigged
- [ ] Cube look: sticker textures, materials
- [ ] Room: table, wall for tally marks, light source
- [ ] 2D collage elements (scans, photos, drawings)
- [ ] Sounds: groans, anger, "ta-da", breathing, real cube clicks and turns, tally scratch, throw and impact, room tone (several versions of each). Each creature design may need its own voice.
- [x] Reference images: Inscryption, Lillemon, Busó (`docs/references/`)
- [ ] Reference images: Švankmajer, bones

## 9. Tech (proposed)

- Runs in the browser: Vite + three.js (WebGL).
- Placeholder shapes and sounds until Leo's assets are ready, so each one can be swapped in as it arrives.
- Endings and creature reactions written so they're easy to swap and test.

## 10. Roadmap

1. Project setup, PS1-look scene with placeholders
2. The cube: real turns, shuffle, solve
3. Button input: press, hold, double press, interrupt
4. The creature's behaviours and mood (placeholders)
5. Sound
6. Leo's assets swapped in
7. Endings to test
8. Physical button
9. Polish for the presentation

## Open questions

1. What is the ending? (§7)
2. Cube or roulette wheel, or both?
3. Answers to the pitch feedback (§2.1).
4. Is the creature fully 2.5D, or are other parts 3D too?

## Progress log

Newest first. One entry per session or decision: what changed, what was learned, what's next.

### 2026-10-21

- Viewpoint decided: the user sits on a chair at a desk in a dark room, in first person.
- Reference screenshots gathered (Inscryption, Lillemon, Busó) and notes written (§6).
- Creature designs to test: bones (Švankmajer) and Busó (from Leo's culture). Nothing chosen yet (§4.1).
- Idea to test: the dark room breaking into a Lillemon-style collage as the unexpected ending (§6.3).
- Pitch presented. It was hard to explain the idea clearly. Teacher feedback: "waiting for an outcome that you do not expect" is a good starting point, and the creature is a personal approach, but many questions stay open (§2.1). They're curious to see it evolve and think it could succeed as a weird "WTF" experience.
- Repo created (`mce221/gelerpixcube`) and this spec written.
- Decided: physical button inside a Rubik's cube; the unexpected ending comes from the solve; interrupting makes the creature react at random.
- Idea to test: 2D creature with 3D arms (2.5D collage).
