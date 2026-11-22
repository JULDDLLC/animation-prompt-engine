---
name: animation-prompt-engine
description: Build headless character sheets, creature sheets, prop sheets, animated Nano Banana Pro stills and Seedance 2.5 multi-shot animation prompts in one shared style (Pixar-style 3D by default).
---

# Animation Prompt Engine — Sheets, Animated Stills, Animated Video

One skill, three outputs that share one look:

1. **Character, creature & prop sheets**: clean reference renders on grey, in the chosen style. Character sheets ALWAYS use the fixed three-view headless framework in Step 4.
2. **Animated image prompts**: a Nano Banana Pro content paragraph with a **style module** appended.
3. **Animated video prompts**: a Seedance 2.5 multi-shot prompt that opens with a short **cast & world block** (every character, prop, location and key frame tagged once), then continuity locks, then shots that refer to everything by name only, then the style module and audio.

**Default style: Pixar-style 3D feature animation.** Use another module only when the user names or implies one.

Deliver only what the user asks for. If the request is ambiguous about which output they want, ask one short question. If they ask for "the full package", the order is: sheets → stills → video prompt.

---

## The golden rule: content vs style

The same scene should be renderable in any style by swapping one module.

**The base prompt owns CONTENT.** The style module never adds, removes or alters any of it:
- the character: identity, the likeness lock features, wardrobe and its condition
- performance, expression, gaze, pose, gesture
- props, environment, set dressing
- action, blocking, timing and dialogue
- the light sources present in the scene (sun, fire, a glowing object)

**The style module owns LOOK only:**
- the medium and render (3D CG, 2D cel, clay, felt, vector)
- how proportions are stylised
- how surfaces and materials resolve (subsurface skin, fingerprinted clay, felt fibres, flat fills)
- how light is rendered (soft bounce, cel shading, practical miniature lighting)
- in video: the motion language (smooth 24fps arcs, animating on twos, stepped stop-motion, smear frames)

Write modules **generically** ("the characters", "all surfaces") so they append to any base prompt unchanged. Keep scene-specific light colours in the base prompt or the continuity locks, not in the module.

---

## Step 1 — Pick a style module (shared across sheets, stills and video)

Choose one module per project and use it everywhere, so sheets, start frames and footage match. Each module has one **anchor trait**: the single signature that pulls the whole image into that medium. Lead with it.

| Module | Anchor trait | Surfaces & light | Motion language |
|---|---|---|---|
| **Pixar-style 3D (default)** | Appealing stylised proportions with expressive eyes | Soft subsurface skin, rich textured materials, warm key with soft bounce, volumetric atmosphere, cinematic depth of field | Smooth 24fps, clear arcs, squash and stretch, anticipation, overlapping action |
| **Painterly stylised 3D** | Hand-painted textures over 3D forms | Visible brushwork on surfaces, graphic shadow shapes, rim-lit silhouettes | Smooth, with occasional held poses and punchy timing |
| **Claymation / stop-motion** | Hand-sculpted clay with fingerprints and tool marks | Miniature practical sets, real tabletop lighting, slight surface flicker between frames | Stepped motion on twos, tiny boiling of surfaces, weighty physical timing |
| **Anime 2D (shōnen action)** | Clean ink line art with cel shading | Flat colour with hard shadow shapes, painted backgrounds, dramatic sky gradients | Animated on twos and threes, speed lines, impact frames, smear frames, held dramatic poses |
| **Classic 2D hand-drawn** | Hand-inked line with soft painted colour | Watercolour or gouache backgrounds, gentle shading | Fluid full animation, squash and stretch, secondary motion |
| **Needle-felt** | Fuzzy wool fibres on every surface | Soft miniature lighting, felt-textured sets | Gentle stop-motion steps, fibres shimmering slightly |
| **Low-poly 3D** | Faceted geometric forms with flat-shaded polygons | Simple gradient lighting, solid colour facets | Smooth, simple, slightly mechanical |
| **Flat vector** | Flat colour shapes with no outlines | Clean geometric shadows, limited palette | Snappy, graphic, eased motion |
| **Chibi** | Oversized heads, tiny bodies, huge eyes | Bright soft shading, candy palette | Bouncy, exaggerated, comic timing |

Rules:
- **Name the style plainly** ("Pixar-style 3D feature animation", "Aardman-style claymation") — naming a studio look anchors harder than describing one. Never name or imitate a specific copyrighted character.
- **Techniques must suit the medium.** No fingerprints on vector, no speed lines in claymation, no subsurface skin in flat 2D.
- **Mixed media** (e.g. 3D characters on painted backgrounds) is allowed only when the user asks; state both halves in the Style line.

### Style lines (paste into the Style metadata and the image style paragraph)

- **Pixar-style 3D:** `Style: Pixar-style 3D feature animation. Stylised, appealing proportions, expressive faces and eyes, soft subsurface skin, richly textured materials, volumetric atmosphere, warm key light with soft bounce, cinematic depth of field, feature-film polish.`
- **Painterly stylised 3D:** `Style: Painterly stylised 3D animation. Hand-painted textures with visible brushwork over sculpted 3D forms, graphic shadow shapes, strong rim light, bold colour.`
- **Claymation:** `Style: Aardman-style claymation stop-motion. Hand-sculpted clay characters with visible fingerprints and tool marks, miniature handmade sets, practical tabletop lighting, stepped stop-motion movement.`
- **Anime 2D:** `Style: 2D anime with shōnen action intensity. Clean ink line art, cel shading with hard shadow shapes, painted backgrounds, speed lines and impact frames on big hits.`
- **Classic 2D:** `Style: Classic hand-drawn 2D animation. Hand-inked linework, soft painted colour, watercolour backgrounds, fluid full animation.`
- **Needle-felt:** `Style: Needle-felt stop-motion. Every character and set made of soft fuzzy wool fibres, miniature practical lighting, gentle stepped movement.`
- **Low-poly:** `Style: Low-poly 3D animation. Faceted geometric forms, flat-shaded polygons, simple gradient lighting, solid colour palette.`
- **Flat vector:** `Style: Flat vector animation. Flat colour shapes with no outlines, clean geometric shadows, limited palette, snappy eased motion.`
- **Chibi:** `Style: Chibi animation. Oversized heads, tiny bodies, huge expressive eyes, bright soft shading, bouncy exaggerated motion.`

---

## Step 2 — Likeness lock (stylising a real person)

When the character is based on a real person or a supplied reference, pick the **three features that make them read as themselves** (e.g. backwards cap + gold wire glasses + full auburn-toned beard) and state them in every sheet and still. In video, they go in the continuity locks.

Rules:
- **Stylise proportions, never identity.** Larger eyes and softer forms are the style's job; hair colour and cut, facial hair, glasses, signature clothing and build stay as given.
- **Keep build honest.** Many styles default to bulky heroes. If the person isn't heavily built, say "slim, average build" explicitly.
- **State eye colour plainly** ("dark brown eyes"). Elaborate iris or catchlight wording makes stylised eyes glow.
- **Masks, helmets and hoods**: name which lock features stay visible (e.g. eyes through the lenses) so identity survives the covering.
- **Caps worn backwards drift forwards.** Say "grey cap worn backwards, its brim pointing back toward the camera" whenever the back of the head faces camera.

---

## Step 3 — Animated image prompt (Nano Banana Pro)

Write two paragraphs (or more content paragraphs for complex compositions, then the style paragraph last).

**Paragraph 1 — content.** Flowing natural-language prose that reads like a story-artist's brief: subject, the likeness lock, action and pose, expression, setting, and the light sources present, exactly as the user gave them. Fill gaps only where the user left them open. If references are supplied, open with "Using the attached references." and refer to characters by their project names.

**Final paragraph — style module.** The module's Style line, plus one sentence on how the scene's light renders in that medium.

Rules:
- **Pose for silhouette.** Animated stills read through clear, exaggerated poses. Describe a pose that reads as a black silhouette (leaning hard forward, arm fully outstretched) rather than a neutral stance.
- **Video start frames:** keep motion blur, speed lines and smear effects **out** of the still. Baked-in motion effects smear once they move. Put them in the video shots instead.
- **Settings override the prompt.** Aspect ratio comes from the generation settings; tell the user to match the video (usually 16:9).

### Multi-character action stills

- **Name similar characters with colour + shape** ("Vexees the green dragon, a round, chunky dragon"; "Naxx the grey dragon, a long, slender dragon") and use the same phrase every time.
- **State who does the action and who doesn't.** "Only Naxx the grey dragon breathes fire." Keep the target's mouth "firmly closed". This stops attacks swapping between characters.
- **Place characters by frame position** ("on the left of frame", "in the bottom right", "in the upper centre-right").
- **Cause and effect reads best side-on.** A wide, side-on shot with attacker on one side and target on the other reads left to right without ambiguity.
- **Complex body orientation: describe body parts nearest to furthest.** E.g. "its tail is closest to the camera, then its hindquarters, then its back with Pyra in the saddle; its shoulders are furthest away. Its neck curves back around the left side of its body so its head faces the camera." Add "its body still flying away from camera, only its neck and head turned back" if the model turns the whole body.
- **Effects aimed at the camera rarely work.** Models default to side-on fire streams. Instead of describing fire coming at the lens, describe the target "flying directly into the trail of fire, the flames rushing straight at them, about to engulf them both", or use a reverse angle where the effect travels away from camera into the target.
- **Simple wording often beats elaborate wording** for spatial relationships. If a detailed description keeps failing, try one plain sentence.
- **Define expressions by features, not labels.** "Scared: eyes wide, brow raised high, mouth clamped shut in a tense, downturned line. He is not smiling." Friendly creature designs smile by default; say "not smiling" whenever the moment is tense. "Angry, deadly serious, not smiling: brows drawn down hard, eyes narrowed, lips pressed into a thin, hard line."
- **The moment before an action** (charging fire, about to leap) often reads better than the action itself: glowing throat, smoke curling from the jaws, chest swelled, neck drawn back. State "The fire has not been released yet."
- **If one element is right and another is wrong, edit the render** instead of regenerating, changing only the wrong element.

### Image example (Pixar-style 3D)

```
Using the attached references. High in a violent thunderstorm, in heavy slanting rain, a wide, side-on shot of both dragons, so the attacker and the target are both clearly visible. On the left of frame, Naxx the grey dragon, a long, slender bone-grey dragon with jagged dark red stripes, flies toward the left of frame, its body level and its long dark red wings spread. Pyra rides on its back, glaring back over her shoulder. She looks angry and deadly serious, not smiling: brows drawn down hard, eyes narrowed, lips pressed into a thin, hard line. Naxx the grey dragon has twisted its long neck back over its own shoulder toward the right of frame, jaws wide open, and a huge, roaring torrent of orange fire blasts from its own mouth across the centre of the frame toward the right.

In the bottom right of frame, Jack and Vexees the green dragon have just swerved out of the fire's path, swooping down and away beneath the flames. Vexees looks scared: eyes wide, brow raised high in fright, mouth clamped shut in a tense, downturned line. He is not smiling. Jack clings on low over the saddle, gripping the saddle horn with both hands, his grey cap worn backwards, eyes wide, mouth open in a gasp. The fire passes just above them, missing them by inches. Only Naxx the grey dragon breathes fire.

Pixar-style 3D feature animation. Stylised, appealing proportions, expressive faces and eyes, soft subsurface skin, richly textured wet leather, scales and fabric, volumetric storm clouds and billowing fire, rain streaks catching the light, cold blue-grey storm fill with the fire as the only bright source, cinematic depth of field, feature-film polish.
```

---

## Step 4 — Character, creature & prop sheets

Sheets are clean references rendered in the chosen style module, on neutral grey, with even lighting and no scene grade. The style must match the project's module exactly, or downstream generations drift between looks.

### Character sheet — ALWAYS the three-view headless framework

**This is the only character sheet layout.** Whenever the user asks for a character sheet, character reference sheet, turnaround or reference sheet for a character, use this exact template. Never fall back to any other layout: no four- or five-view sheets, no reordering, no extra panels, even when the request is one short line. Copy the template word for word and fill in only the bracketed parts.

```
Character reference sheet — three views on a neutral grey studio background, arranged left to right, rendered in [STYLE NAME]:
[VIEW 1 — FULL BODY, FRONT, HEADLESS] Full-body front-facing view of this character's costume and body, standing straight-on, arms slightly away from the sides. Full body visible from neck to feet — no head, the costume shown as if worn on an invisible/absent head. Focus on how the garments hang, layer, and fit.
[VIEW 2 — FULL BODY, REAR] Full-body rear view of the same character, directly from behind, standing in the same neutral pose. Full body visible head to feet, including the back of the head, and the rear of every garment. [HEADWEAR LINE]
[VIEW 3 — FRONT CLOSE-UP] Head-and-shoulders extreme close-up, straight-on front view. Sharp, detailed focus on facial features, expression range and [STYLE SURFACE DETAIL].
Character: [CHARACTER DESCRIPTION]
Style: [STYLE LINE]
Lighting & presentation: Clean, even studio lighting — soft key light from the upper left, gentle fill from the right. Consistent character identity, proportions, and costume details across all three views. Even, neutral grey seamless backdrop.
Constraints: No text, no watermarks, no extra figures, no background environment.
```

**Filling the template:**
- **[STYLE NAME] / [STYLE LINE]**: from the project's module in Step 1. Drop scene-specific light (fire, storm, golden hour) from the Style line on sheets; keep only the medium, proportions and surface treatment.
- **[STYLE SURFACE DETAIL]**: how surfaces resolve in this medium — "soft subsurface skin and fine stylised texture" (Pixar), "fingerprints and tool marks in the clay" (claymation), "clean ink line and cel shadow shapes" (anime), "visible wool fibres" (needle-felt).
- **[CHARACTER DESCRIPTION]**: the character exactly as the user gave it, including the likeness lock, build, wardrobe and its condition. Fill gaps only where the user left them open, and say in the note which details you filled.
- **[HEADWEAR LINE]**: if the character wears a cap, hat or helmet, add a line confirming its rear detail is visible (e.g. "Brim of the cap visible."). Otherwise leave the line out.
- **View 1 garment wording** may be made specific to the costume (e.g. "Focus on how the leather flight suit, open collar, chest harness and belt sit, layer and fit") without changing anything else.
- **Reference supplied**: open the Character line with "Using the attached reference — the same man/woman, same face, same [lock features]."
- **Rider and mount palettes**: when designing a rider and their creature, keep their main colours distinct so the rider doesn't vanish into the creature (e.g. a crimson coat on a bone-grey dragon), and tie them together with one shared accent (e.g. red wing membranes, matching black leather tack).

### Layered versions (edit prompts on an existing sheet)

When a costume state changes (a mask added, a collar popped, a cap moved), write a **minimal edit prompt** on the existing sheet rather than a new sheet:

```
Using the attached character reference sheet. This is a minimal edit. Keep everything exactly as it is: the same character, the same three-view layout, the same pose, proportions and build, the same [costume pieces] with all their stitching, buckles and details unchanged, the same lighting, grey backdrop and [STYLE NAME] rendering. Make only these [N] changes and nothing else:

1. [Change]: [description]. Apply this in [which views].
2. [Change]: [description]. Apply this in [which views].

The headless front view stays headless. [What it shows of the changes.]

Every other detail of the sheet stays identical to the attached reference.

Constraints: No text, no watermarks, no extra figures, no background environment.
```

Rules: number each change and say which views it applies to. A head covering appears only in the rear view and close-up. If the model still changes other details, run the changes as separate edits.

### Creature sheets

Keep the three-panel structure, lighting, backdrop and constraints, and adapt the views. Say in one line which adaptation you made.
- **Creature with no costume**: View 1 becomes a full-body front view with the head included.
- **Quadruped or winged creature**: View 2 becomes a full-body 90-degree side profile from snout to tail, because a rear view hides the silhouette, limbs, wings and tail.
- **Flying creatures (preferred for dragons)**: render both full-body views in the same level flying pose. Describe exactly where every limb goes, or the model stands it on a floor: "airborne, suspended high in mid-air, wings fully spread and level at full span, all four legs folded up tight against the belly, front claws curled in under the chest, back feet drawn up beneath, tail trailing behind, with open grey space all around". Change the presentation line to "The dragon floats in mid-air in every full-body view, against an even, neutral grey backdrop that fills the whole frame." and add "no floor, no ground shadow" to Constraints.
- **Pale creatures on grey**: if the silhouette disappears, use "a mid-to-dark neutral grey" backdrop for that sheet only.
- **Good vs evil reads**: large round eyes with big dark pupils, blunt rounded teeth and rounded horns read friendly; narrow slit pupils, sharp teeth, swept-back horns, spines and angular forms read menacing.

### Filled example — flying creature (Pixar-style 3D)

```
Character reference sheet — three views on a neutral grey studio background, arranged left to right, rendered in Pixar-style 3D feature animation:
[VIEW 1 — FULL BODY, FRONT, FLYING] Full-body front-facing view of this creature airborne, suspended high in mid-air, flying straight toward the camera, head included. Wings fully spread and level at full span. All four stubby legs folded up tight against his barrel-shaped belly, front claws curled in under his chest, back feet drawn up beneath him. Short rounded tail trailing behind and slightly down. Full body visible from horns to wingtips, with open grey space all around him. Focus on the belly, the chest strap, and the full width of both wings head-on.
[VIEW 2 — FULL BODY, SIDE PROFILE, FLYING] Full-body 90-degree side profile of the same creature airborne in the same flying pose, from snout to tail, body stretched horizontal and leaning slightly forward into the flight. Wings spread wide and raised. Front legs tucked back along his chest, back legs drawn up and folded against his belly, claws curled in. Tail extended straight out behind. Full silhouette visible, with open grey space beneath him, including the horns, the saddle on his back, the wing membranes and struts, and the short rounded tail.
[VIEW 3 — FRONT CLOSE-UP] Head-and-shoulders extreme close-up, straight-on front view. Sharp, detailed focus on facial features, an expression range from a warm, gentle half-smile to a mild, lovable frown, and fine stylised scale texture with soft subsurface highlights on the snout and throat.
Character: A chunky, round-bodied dragon with a heavy, barrel-shaped belly and a kind, loyal, good-natured face. His scales are blue-teal with fine darker speckles, fading to a smooth pale cream belly and throat. Broad, rounded snout, two small blunt rounded teeth, large round bright yellow eyes with big dark pupils, two small rounded dark horns. Broad bat-like wings with tan membranes, short stubby legs with dark blunt claws, a short rounded tail. A simple brown leather chest strap and a small worn leather saddle with a saddle horn.
Style: Pixar-style 3D feature animation. Stylised, appealing proportions, expressive faces and eyes, soft subsurface skin, richly textured materials, feature-film polish.
Lighting & presentation: Clean, even studio lighting — soft key light from the upper left, gentle fill from the right. Consistent character identity, proportions, and costume details across all three views. The dragon floats in mid-air in every full-body view, against an even, neutral grey backdrop that fills the whole frame.
Constraints: No text, no watermarks, no extra figures, no background environment, no floor, no ground shadow.
```

### Prop sheet

Props use their own four-view layout:

```
Prop reference sheet — four views on a neutral grey studio background, arranged left to right, rendered in [STYLE NAME]:
[VIEW 1 — FRONT] Straight-on front view of the whole prop. [What to focus on.]
[VIEW 2 — REAR] Straight-on rear view of the same prop, showing [rear details].
[VIEW 3 — 3/4 DETAIL] Close-up three-quarter view, angled to show depth, materials and fine detail.
[VIEW 4 — 90° PROFILE] Side profile showing thickness and how parts connect.
Prop: [PROP DESCRIPTION, including glow colour for emissive props]
Style: [STYLE LINE]
Lighting & presentation: Clean, even studio lighting — soft key light from the upper left, gentle fill from the right. Consistent design, proportions and details across all four views. Even, neutral grey seamless backdrop.
Constraints: No text, no watermarks, no hands, no figures, no background environment.
```

For glowing or emissive props, state the glow colour in the description so it carries into every shot. For long chains or straps, add "fully visible from top to bottom" to View 1.

### Location plates

Environment as subject, no characters, rendered in the project's module with the scene's time of day and weather. Leave a clear path through the space (a corridor between cloud walls, a road) for characters to travel through in later shots. When attaching a plate to Seedance, define it in the LOCATIONS section of the cast block as an environment reference only, so it isn't cloned as a start frame.

---

## Step 5 — Animated video prompt (Seedance 2.5)

### Prompt order

Every video prompt runs in this order, all inside one fenced code block:

1. **CAST & WORLD** — characters, props, locations and key frames, each tagged **once**, with a short name entry.
2. **CONTINUITY LOCKS** — the rules that hold across every shot, with shot numbers for anything that changes.
3. **SHOTS** — the timecoded sequence, referring to everything **by name only**.
4. **Style** — the module's Style line with the scene's light added.
5. **Audio** — the fixed diegetic line, always last, word for word.

The model gets its context first, then the action, then the look and sound.

### 1. CAST & WORLD block

The attached reference images define what everyone looks like. The cast block's job is to **bind each tag to a name** and state anything the image can't (role, behaviour, what the character never does). Keep entries short.

```
CAST & WORLD
CHARACTERS
@Jack is Jack.
@Vexees is Vexees the green dragon, Jack's round, chunky dragon. Vexees the green dragon does not breathe fire at any point.
@Pyra is Pyra.
@Naxx is Naxx the grey dragon, Pyra's long, slender dragon. Naxx the grey dragon is the only dragon that breathes fire.
PROPS
@Amulet is the amulet, glowing warm amber, on a long gold chain.
LOCATIONS
@Storm is the storm. Environment reference only.
KEY FRAME
@KeyFrame is the key frame: [one-sentence composition]. [Use as the start frame of shot N only. / Shot N passes through the key frame. / Shot N ends on the key frame.]
```

Rules:
- **Tag once, name everywhere else.** The `@tag` appears only in the cast block. In the shots and locks, use the plain name exactly as defined. Never introduce a new name or nickname mid-prompt.
- **Short entries by default.** "@Pyra is Pyra." is enough when a reference sheet is attached. Add a one-line description only when no reference is attached, or when a character drifts between shots (then add their three lock features).
- **Similar characters get a colour + shape name.** Two dragons, two riders or two robots get a descriptor built into the name ("Vexees the green dragon", "Naxx the grey dragon") and that full phrase is used **every time** in the shots, not just the first. This is the strongest fix for the model swapping who does what.
- **Behaviour rules live in the cast entry too.** "Naxx the grey dragon is the only dragon that breathes fire." / "Vexees the green dragon does not breathe fire at any point."
- **Costume states as separate references.** When a character's look changes mid-project (masked vs unmasked), tag the version as its own reference and limit it to specific shots: "@JackMasked is Jack in his brown leather mask, flight suit zipped to the top, collar popped. Reference for shots 1 to 6 only."
- **Props that must move a certain way** get their material behaviour in the cast entry, because the reference sheet will otherwise make them rigid: "The leather is soft, thin and supple, and it moves like fabric: it bunches, folds, stretches and creases as it is pulled on, then settles snugly."
- **Key frames.** When the user has a still of a key moment, tag it under KEY FRAME with a one-sentence description of the composition and say exactly which shot it belongs to (start frame, passes through, or ends on). Never let it apply to the whole video.
- **Every tag matches an attached reference** where one exists. With no references attached, write full descriptions in the cast entries instead.

### 2. CONTINUITY LOCKS

One paragraph, only the locks the scene needs. Refer to shots by number.

- **Who rides what**: "Jack rides Vexees the green dragon. Pyra rides on the back of Naxx the grey dragon, seated in its saddle, in every shot she appears in."
- **Roles in an attack**: "Naxx the grey dragon is the attacker. Vexees the green dragon is the target."
- **Who does the action, and when**: "Fire: only Naxx the grey dragon breathes fire, and only in shots 4 and 5. Vexees the green dragon never breathes fire and is never hit by the fire."
- **Flying creatures never hover**: "Vexees the green dragon and Naxx the grey dragon are always flying forward at speed with powerful wingbeats in every shot, never hovering or stationary, even in slow motion." Include this in every scene with flying creatures.
- **Direction of travel**, with every exception named by shot number: "Both dragons fly screen right to left until shot 4, when Naxx the grey dragon turns to face screen right."
- **Weather** that persists in every shot, including final holds: "Heavy, driving rain and violent, howling wind in every moment of the shot, from the first frame through the final hold."
- **Light**: key colour, warm/cold accents, which source is brightest.
- **Prop states and hands**: who holds what, in which hand, how it's held, and from which shot it changes. Give each hand one job: "The amulet is only ever in the palm of Jack's right gloved hand. His left hand grabs the saddle horn, removes the mask and puts the cap on." For loose parts: "its long gold chain hangs loose from her hand, flapping and whipping freely in the wind."
- **Costume states by shot**: "He wears the mask from shot 1 until he pulls it off in shot 6. His grey cap hangs clipped to his belt until shot 8, when he puts it back on, worn backwards."
- **Poses that repeat**: "Freefall in shots 1 to 4: belly down, arms and legs spread wide in a classic skydiving freefall pose."
- **Expressions that must hold**: "Vexees the green dragon never smiles." / "Pyra never smiles."
- **Safety for family tone**: "Jack is fully engulfed in fire in shots 5 and 6 and comes through completely unharmed, protected by his special leather suit."
- **Off-screen sources**: "In shot 1, a torrent of fire roars in from off-screen left, breathed by an unseen dragon outside the frame; only Jack and Vexees the green dragon are in frame."
- **Likeness**: the lock features that stay visible in every shot the character appears in.

### 3. SHOTS

- Total is **exactly 30 seconds** unless the user asks for another length. Shots run **2–5 seconds**, each opening with a `[MM:SS - MM:SS]` stamp; the last ends at the total.
- Each shot specifies **shot size, lens, angle and movement**, varied between consecutive shots.
- One paragraph per shot, separated by blank lines.
- **Use full names every time** for similar characters ("Naxx the grey dragon", never "the dragon" or "it" at the start of a sentence where two dragons share the shot).
- **Assert wanted traits positively** where possible ("he passes through completely unharmed"). Direct negatives are fine for rules the model keeps breaking ("never breathes fire", "not smiling").
- Hard maximum of **7,500 characters** for the whole prompt. Count it before delivering.

#### Splitting cause and effect

When the model keeps assigning an action to the wrong character, give each side of the action its own shot:
- **Attacker shot**: only the attacker in frame. "The attacker: Naxx the grey dragon whips around and blasts fire from its own mouth toward screen right."
- **Target shot**: only the target in frame, with the effect arriving from off-screen. "The target: Jack and Vexees the green dragon, mouth closed, eyes wide, dive out of the bottom right of frame as the fire from Naxx the grey dragon roars just above them."

Label them "the attacker:" and "the target:" at the start of each shot.

#### Virtual camera (animation)

Animation has no physical camera, so the full vocabulary is available: orbits, cranes, impossible fly-throughs, whip pans, POV from inside a mask, a camera that falls with a character. Use that freedom deliberately.
- **Handheld with shake** is a stylistic choice in animation; reserve it for chaos, speed and impacts ("pronounced shake", "violent shake"), and keep calm beats steady so the contrast lands.
- **Direction of travel** is the biggest continuity risk in flying or chase scenes. Lock it and call out any shot that breaks it on purpose.
- **Frame positions** make relationships clear: "in the foreground on the left of frame, in sharp focus" / "on the right of frame, soft in the background".
- **POV shots** need framing anchors: "Both round glass lenses fill the frame side by side, ringed in brass, with the dark stitched leather of the mask's interior between and around them." For chaos: "the view spins, tumbles and lurches wildly, the horizon flipping over and over".
- **Exits and holds**: "swoops down and out of the bottom left of frame", then "the camera holds on the empty storm" for a trailer-style button.

#### Performance (animation principles in the shots)

Write performance the way an animation director would brief it:
- **Anticipation before big actions** (two wingbeats then a dive, a glowing throat before fire).
- **Held beats for comedy, tension and despair** ("a beat of stillness, just wingbeats and rain"; "a long, held beat: all hope is lost").
- **Expressions defined by features**: brows, eyes, mouth shape. Build emotional changes within a shot ("from concentration into deep-seated anger: an intense, menacing frown, not smiling").
- **Creature acting**: give creatures a clear reaction (a head tilt as if listening, eyes softening as it calms).
- **Speed changes**: open the shot with "Slow motion." and the next with "Normal speed." so the ramp is unambiguous. Give slow-motion money shots 4–5 seconds. A big hero moment can run across two consecutive slow-motion shots (the leap in, then inside the effect).
- **Last-second reversals**: build despair over 7–8 seconds, then make the turn "right at the last second, in a sudden flash", with the rescue and the follow-through action in one fluid shot.
- **Hand actions**: be precise about grips and movements. "Pinches the small metal zip pull between his gloved finger and thumb and draws it up in one smooth, firm motion." "Holding it by the brim, puts it back on backwards, the brim swinging round to the back of his head."
- **Off-camera actions**: "His left hand moves the mask down out of frame, and a slight motion of his arm and shoulder suggests he's tucking it into his back pocket off camera."
- **Soft materials**: "pulls it down over his head like a hood; the supple leather bunches and creases as it slides down, then stretches and smooths out."

#### Dialogue

- One line per shot at most, in quotes, attributed by name, with delivery and accent ("muffled through the mask, calm, British accent").
- Off-screen lines are fine: "Jack, off-screen, pleading, British accent: '...'"
- Add "ensure the voice matches @[tag]" in the cast entry when a voice reference is attached.
- Give dialogue shots 3–4 seconds and calm framing so the line lands.
- If lip sync matters and the face is covered, say so in the delivery note; if the model garbles a line, suggest recording it separately.

#### Pacing guide

- Calm or comedic: 6–8 shots, longer holds.
- Action: 9–12 shots, faster cutting, with one longer money shot.
- In medias res: open on a tight, intense close-up, end on a cliffhanger or a clear button.

### 4–5. Style and Audio

```
Style: [the module's Style line, with the scene's light added]
Audio: Diegetic sound only — realistic, high-fidelity foley and natural ambience. Grounded, physical sound effects with real weight and texture — impacts, footsteps, cloth, breath — recorded-quality environmental sound. No music, no score, no soundtrack.
```

The Audio line is fixed and always comes **last**, word for word.

### Video example (Pixar-style 3D, action)

```
CAST & WORLD
CHARACTERS
@Jack is Jack, in his brown leather mask and oversized brown leather gloves.
@Vexees is Vexees the green dragon, Jack's round, chunky dragon. Vexees the green dragon does not breathe fire at any point.
@Pyra is Pyra.
@Naxx is Naxx the grey dragon, Pyra's long, slender dragon. Naxx the grey dragon is the only dragon that breathes fire.
PROPS
@Amulet is the amulet, glowing warm amber, on a long gold chain.
LOCATIONS
@Storm is the storm. Environment reference only.

CONTINUITY LOCKS
Jack rides Vexees the green dragon. Pyra rides on the back of Naxx the grey dragon in every shot she appears in. Naxx the grey dragon is the attacker. Fire: only Naxx the grey dragon breathes fire, and only in shots 3, 4 and 5. Vexees the green dragon never breathes fire and is never hit; in shot 4 he looks scared and dives out of the bottom right of frame. Both dragons are always flying forward at speed with powerful wingbeats in every shot, never hovering or stationary, even in slow motion. Direction of travel: both dragons fly screen right to left until shot 3, when Naxx the grey dragon turns to face screen right. Heavy rain in every shot. Light: cold blue-grey storm light; Naxx the grey dragon's fire is the brightest source, the amulet's amber glow the only other warm light. Amulet: until shot 6 it rests in the palm of Pyra's right hand, its long gold chain loose and flailing in the wind. From shot 6 it is only ever in Jack's right fist, its chain trailing. Freefall in shots 7 and 8: belly down, arms and legs spread wide. Jack is fully engulfed in fire in shots 4 and 5 and comes through completely unharmed, protected by his leather suit. Pyra never smiles.

[00:00 - 00:04] Rear tracking shot, 35mm, from just behind and slightly above Vexees the green dragon — Vexees fills the upper centre-right of frame, seen from behind, wings spread wide, Jack seated upright on his back. Far below in the lower left, Pyra riding Naxx the grey dragon is a single tiny silhouette among the clouds. Vexees the green dragon gives two powerful wingbeats, then folds his wings and dives toward them.

[00:04 - 00:07] Close-up, 50mm, eye-level, tracking — in the foreground on the left, in sharp focus, Pyra rides Naxx the grey dragon, the amulet in her palm, its chain flailing. Behind them on the right, soft in the background, Jack and Vexees the green dragon swoop in. Without turning, Pyra's expression hardens from concentration into an intense, menacing frown, not smiling.

[00:07 - 00:10] Wide, 24mm, eye-level, handheld with pronounced shake — the attacker: Naxx the grey dragon whips its whole body around to face Jack and Vexees the green dragon and blasts a huge torrent of orange fire from its own mouth straight at Jack.

[00:10 - 00:14] Slow motion. Wide, 35mm, eye-level, tracking — the fire from Naxx the grey dragon streams straight at Jack and Vexees the green dragon's head. Jack launches forward off Vexees' back, diving headfirst into the fire, and it swallows him completely, as if he has sacrificed himself. Vexees the green dragon, eyes wide with fear, mouth clamped shut, dives down and out of the bottom right of frame, untouched.

[00:14 - 00:17] Slow motion. Medium, 50mm, tracking alongside Jack — inside the fire, Jack is completely engulfed, a dark silhouette moving steadily forward, flames streaming off his leather suit and mask, his eyes calm behind the lenses. He is completely unharmed.

[00:17 - 00:19] Normal speed. Medium close-up, 50mm, whip pan — Jack bursts out of the fire, carried by his leap's momentum, reaches out with his right arm, grabs the amulet's flailing chain and yanks it free from Pyra's palm in one smooth, fast motion.

[00:19 - 00:23] Wide, 24mm, low angle, static — Jack free-falls past Pyra and Naxx the grey dragon, belly down, arms and legs spread wide, the amulet gripped in his right fist, before either can react.

[00:23 - 00:26] Wide, 35mm, high angle, tilt down — Jack plummets into a thick blanket of cloud fifty feet below and vanishes with a soft puff of vapour.

[00:26 - 00:30] Medium close-up, 50mm, tracking — Pyra, still seated on Naxx the grey dragon, frozen in stunned disbelief, eyes darting to her empty palm. Naxx the grey dragon flies steadily onward, barely noticing.

Style: Pixar-style 3D feature animation. Stylised, appealing proportions, expressive faces and eyes, soft subsurface skin, richly textured wet leather, scales and fabric, volumetric storm clouds and roaring fire, rain streaks and suspended embers catching the light, dramatic high-contrast lighting with cold blue-grey fill, blazing orange firelight and the amulet's warm amber glow, cinematic depth of field, feature-film polish.
Audio: Diegetic sound only — realistic, high-fidelity foley and natural ambience. Grounded, physical sound effects with real weight and texture — impacts, footsteps, cloth, breath — recorded-quality environmental sound. No music, no score, no soundtrack.
```

---

## Delivery

- Each prompt goes in its **own fenced code block** with a short label line above it (e.g. `CHARACTER SHEET — Jack, flight suit, Pixar-style 3D` or `VIDEO PROMPT: Generation 3, the leap (v2)`).
- **Revisions: always output the complete updated prompt**, never a fragment to paste in, unless the user asks for only the changed line. Increment the version number in the label.
- After the prompts, a **companion note of 2–4 sentences**: the module used, the shot structure and why, the aspect ratio to generate at, and one or two specific tweaks if a shot misses (re-roll a single failing shot rather than the whole sequence; name the riskiest shot).
- If you filled gaps in the user's content (a detail they didn't specify) or followed a reference sheet over the user's wording (e.g. a colour), say so in one line.
- Don't otherwise describe changes to the user's characters, story or dialogue in the note. There shouldn't be any.

## Diagnosing a miss

- **Looks like the wrong style or drifts to photoreal:** the anchor trait didn't land. Lead the Style line with the style name, check the sheets were rendered in the same module, remove realism words ("photoreal", "live action", "real skin pores").
- **Character doesn't read as the person:** a lock feature is missing, or the build was bulked up. Add the three lock features and "slim, average build" to the cast entry.
- **Wrong character does the action (e.g. the wrong dragon breathes fire):** use colour + shape names every time, state "only X does it" in the cast entry and the locks, label the attacker and target, and split the action into an attacker-only shot and a target-only shot.
- **Model confuses who is who:** a name in the shots doesn't exactly match the cast block, or a pronoun is ambiguous in a two-character shot. Use the full defined names every time.
- **A short cast entry drifts:** add one line of lock features back to that entry only.
- **Prop handling changes between shots:** state exactly where it sits ("only ever in the palm of her right hand"), how loose parts behave ("chain flapping freely"), which hand does what, and the shot where it changes hands.
- **Flying creature hovers or stands still:** add the "always flying forward, never hovering or stationary, even in slow motion" lock.
- **Creature or body orientation is wrong:** describe body parts nearest to furthest, and say which parts turn and which stay ("its body still flying away from camera, only its neck and head turned back").
- **Effect aimed at camera goes sideways:** rephrase as the target flying directly into it, or change to a side-on or reverse angle.
- **Friendly character smiles in a tense moment:** define the expression by features and add "not smiling"; fix any key frame showing a smile before tagging it, because the video model copies it.
- **Eyes glowing or uncanny:** simplify eye wording to the plain colour.
- **Creature design drifting between cuts:** attach the creature sheet as the tagged reference and add colour, head shape, horns and wing type to its cast entry.
- **Characters swap direction mid-chase:** add or tighten the direction-of-travel lock and reduce shots that break it.
- **Key frame overrides the whole video:** state which shot it belongs to; if it still leaks, generate that shot as a separate clip with the key frame as its start frame.
- **Soft costume pieces move rigidly (masks, hoods):** describe the material behaviour in the cast entry and the shot; if a reference sheet makes it rigid, drop that reference from the shot and let the description lead.
- **Weather calms down in a final hold:** restate the weather in the hold itself and in the locks ("through the final hold").
- **Action reads as violent or harmful in a family style:** rewrite the beat so the danger is clearly survived ("passes through completely unharmed", "tumbles out drenched") and the comeuppance is comic.
- **Character sheet came out in a different layout:** the template wasn't copied word for word. Regenerate from the exact three-view headless template in Step 4.
- **Creature sheet shows it standing on a floor:** describe where each leg goes in the flying pose, and add "no floor, no ground shadow".
