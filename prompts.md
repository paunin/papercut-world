# How the images were prompted

Every image in Papercut World came from one text prompt, built the same way
each time so the whole set looks as if one artist made it. This page gives
the recipe: the fixed blocks word for word, the rules for writing the part
that changes, and a few real scenes. With it, an image can be regenerated, or
a new place added in the same style.

## Model and settings

| | |
| --- | --- |
| Model | Nano Banana 2 (text to image, no reference images) |
| Aspect ratio | `21:9` |
| Resolution | `1K`, which returns a 1584 × 672 PNG |
| Seed | not set, so every run differs |

The model doesn't return the same image twice, so expect to regenerate a
few. See [Reviewing an image](#reviewing-an-image).

## The four blocks

Every prompt is four blocks joined by single spaces, always in this order:

```
{HEADER} {STYLE} Scene: {SCENE} {COMPOSITION}
```

| Block | Changes per place? |
| --- | --- |
| Header | Yes: names the place |
| Style | No, except one phrase for the sun's shape |
| Scene | Yes: written to a fixed grammar |
| Composition | No |

Only the header and the scene name the place. The style and composition text
is identical for every image. Copy those blocks exactly: rewording even one
adjective shifts the look.

### Header

For a country or territory:

```
Wide panoramic travel destination banner illustration of {PLACE}.
```

`{PLACE}` is the name in capitals, with "the" where English uses it
(`the BALTIC STATES`, `the ISLE OF MAN`). A city or island can follow in
brackets when the scene centres on it, for example `CURAÇAO (Netherlands
Antilles)` or `BONAIRE (Netherlands Antilles)`.

For a region:

```
Wide panoramic travel destination banner illustration of {REGION} — one continuous landscape that joins icons from several of its countries.
```

For the global scene:

```
Wide panoramic travel destination banner illustration of THE WHOLE WORLD — one continuous landscape that joins famous icons from several continents.
```

For the default scene, the place is deliberately nowhere:

```
Wide panoramic travel destination banner illustration of NOWHERE IN PARTICULAR — a generic travel scene that suggests no specific country.
```

### Style

```
Style: layered paper-cut diorama — the scene is built from stacked layers of coloured cardstock with visible paper fibre texture and soft drop shadows between layers, handcrafted and tactile, bright clean colours, with rich, intricate detail at every depth: many thin layers, and windows, roof tiles, leaves, ripples and rock faces each cut as separate small pieces of card, as finely made as a premium pop-up book — never sparse, never large empty flat shapes. Every piece is flat-coloured card with no gradients anywhere: no airbrushed sky, no light washing across the scene; tone and depth come only from stacking layers and their soft shadows. It is an open landscape whose sky, hills and ground layers carry straight on past every edge of the image, as if the picture were cropped from a wider scene — not a shadow box: no white card border, no frame, no mat, no inner frame or raised paper rim around the picture, no paper strip or cloud bank laid along the top edge, and no arch of trees or leaves closing the scene in like curtains. The sun is cut from paper like everything else, with a crisp edge and a soft drop shadow: {SUN}; no glow, halo, beams of light, thin drawn rays, lens flare or bright bloom around it, and the sky is flat paper layers, each a single colour — never a burst of light.
```

`{SUN}` is one of two phrases, so that half the set has a plain sun and half
a star-shaped one:

| Shape | `{SUN}` |
| --- | --- |
| Disc | `a flat disc of yellow card, one or two stacked circles` |
| Star | `a star-shaped paper sun: a yellow disc ringed with short pointed rays cut from the same card` |

Asking for "either" doesn't work, because the model then draws a disc almost
every time. Each prompt names one shape, chosen by a rule that always gives
the same answer for a given file name. Add up the letters of the name (a = 1 …
z = 26, ignoring `_`): an even total gets the star, an odd total the disc.
For example, `jp` is 10 + 16 = 26, a star.

### Scene

```
Scene: [exclusions;] {LANDMARKS} in the central band, {SETTING}, {PLANTS} rising from the bottom corners up the left and right edges, stopping below the top quarter of the frame, {ANIMAL} in the lower-{left|right} third, standing just above the bottom 12% of the frame.
```

| Slot | What goes in it |
| --- | --- |
| Exclusions | Optional. Anything the model tends to add that the image must not have. See below |
| `{LANDMARKS}` | One or two landmarks or natural features that people recognise at a glance, in daylight |
| `{SETTING}` | One or two more features, placed with "behind", "to one side" or "on the far side" |
| `{PLANTS}` | Native trees or plants. In polar scenes this slot holds ice ridges, mossy rocks or tussock grass instead |
| `{ANIMAL}` | One native animal. Alternate left and right between places so a grid of images doesn't lean one way |

Rules that came out of testing:

- **Name five things at most.** With more, the model drops some and shrinks
  the rest.
- **Put exclusions first.** A "no flags" buried mid-sentence is ignored, but
  the same words opening the scene ("there are no flags in this picture;") are
  followed. The same goes for unwanted landmarks: the model adds famous
  buildings nobody asked for unless the scene rules them out up front.
- **Exclude flags almost everywhere.** Harbours, castles and boats draw flags
  by default. Most scenes open with "there are no flags in this picture;".
- **Sensitive places get landscape and heritage only.** Their scenes open by
  excluding flags, portraits, soldiers, weapons and damaged buildings, and
  where relevant walls, fences, maps, religious buildings and lettering.
- **Regions** take icons from several different member countries, and avoid
  icons another region already uses.
- **The default scene** names nothing identifiable: a hot-air balloon, a
  small plane with a dashed trail, a bay with a sailboat and rolling hills.

### Composition

```
Composition rules: daylight, with the sun high in the upper-left sky but well away from the corner; the top 15% of the frame is open sky only and the top-left corner stays empty — no sun, branches or leaves there; the bottom 12% is simple foreground only, with animals, vehicles and people standing above it, never in it; landmarks sit in the central band and are recognisable at a glance. No text, no letters, no signage, no flags, no logos, no watermark, no border, no frame, no close-up human faces. Full bleed edge to edge.
```

This block keeps every image croppable the same way: sky across the top 15%,
plain foreground across the bottom 12%, and the subject in the middle.

## A complete prompt

Malawi, exactly as it was sent:

```
Wide panoramic travel destination banner illustration of MALAWI. Style: layered paper-cut diorama — the scene is built from stacked layers of coloured cardstock with visible paper fibre texture and soft drop shadows between layers, handcrafted and tactile, bright clean colours, with rich, intricate detail at every depth: many thin layers, and windows, roof tiles, leaves, ripples and rock faces each cut as separate small pieces of card, as finely made as a premium pop-up book — never sparse, never large empty flat shapes. Every piece is flat-coloured card with no gradients anywhere: no airbrushed sky, no light washing across the scene; tone and depth come only from stacking layers and their soft shadows. It is an open landscape whose sky, hills and ground layers carry straight on past every edge of the image, as if the picture were cropped from a wider scene — not a shadow box: no white card border, no frame, no mat, no inner frame or raised paper rim around the picture, no paper strip or cloud bank laid along the top edge, and no arch of trees or leaves closing the scene in like curtains. The sun is cut from paper like everything else, with a crisp edge and a soft drop shadow: a star-shaped paper sun: a yellow disc ringed with short pointed rays cut from the same card; no glow, halo, beams of light, thin drawn rays, lens flare or bright bloom around it, and the sky is flat paper layers, each a single colour — never a burst of light. Scene: the clear blue Lake Malawi with rocky granite islands and wooden dugout canoes in the central band, colourful cichlid fish visible in the clear shallows, the great granite massif of Mount Mulanje behind, a fishing village of thatched huts on a golden beach to one side, baobab and mango trees rising from the bottom corners up the left and right edges, stopping below the top quarter of the frame, a lilac-breasted roller on a branch in the lower-left third, standing just above the bottom 12% of the frame. Composition rules: daylight, with the sun high in the upper-left sky but well away from the corner; the top 15% of the frame is open sky only and the top-left corner stays empty — no sun, branches or leaves there; the bottom 12% is simple foreground only, with animals, vehicles and people standing above it, never in it; landmarks sit in the central band and are recognisable at a glance. No text, no letters, no signage, no flags, no logos, no watermark, no border, no frame, no close-up human faces. Full bleed edge to edge.
```

## Example scenes

A few scenes as written, after "Scene: ". "(rising…)" stands for "rising
from the bottom corners up the left and right edges, stopping below the top
quarter of the frame", and each animal also ends "standing just above the
bottom 12% of the frame".

| File | `{PLACE}` | Kind | Scene |
| --- | --- | --- | --- |
| `mw` | `MALAWI` | country | the clear blue Lake Malawi with rocky granite islands and wooden dugout canoes in the central band, colourful cichlid fish visible in the clear shallows, the great granite massif of Mount Mulanje behind, a fishing village of thatched huts on a golden beach to one side, baobab and mango trees (rising…), a lilac-breasted roller on a branch in the lower-left third. |
| `ir` | `IRAN` | sensitive place | there are no flags, no portraits, no domes, no mosques and no lettering in this picture; the long two-storey rows of arches of the Si-o-se-pol bridge across the Zayandeh river in Isfahan in the central band, the mud-brick old town of Yazd with its tall windcatcher towers to one side, the snowy cone of Mount Damavand behind, the ancient stone columns and stairways of Persepolis on the far side, pomegranate and cypress trees (rising…), an Asiatic cheetah in the lower-right third. |
| `sj` | `SVALBARD` | territory | there are no flags in this picture; jagged snowy mountains and a wide blue-and-white glacier front meeting a calm Arctic fjord in the central band, floating ice with a small expedition ship to one side, the colourful wooden houses of Longyearbyen on a bare valley slope on the far side, low tufts of white arctic cotton grass and moss (rising…), a polar bear on the ice in the lower-right third. |
| `aq` | `ANTARCTICA` | uninhabited | there are no flags, no research stations and no buildings in this picture; huge white and pale-blue icebergs drifting in a calm dark-blue channel between snowy mountain peaks of the Antarctic Peninsula in the central band, a small white expedition ship with no flags among the ice to one side, the tail of a humpback whale rising from the water on the far side, sculpted ice ridges and snow-covered rocks (rising…), an emperor penguin on the ice in the lower-left third. |
| `caribbean` | `the CARIBBEAN` | region | there are no flags and no cruise ships in this picture; a chain of green volcanic islands across a bright turquoise sea in the central band, two steep green peaks rising straight from the water, a pastel colonial harbour town below an old stone fort to one side, a white sand beach with a little wooden beach bar and a sailing yacht on the far side, coconut palms and red hibiscus (rising…), a pink flamingo in the lower-left third. |
| `global` | — | global | the Eiffel Tower, the Statue of Liberty, the Pyramids of Giza, the Taj Mahal and Mount Fuji arranged left to right across the central band, a calm sea in front, a small plane with a dashed trail in the upper-middle sky, palm and pine trees (rising…), no animals. |
| `default` | — | default | a colourful hot-air balloon drifting in the central band, a small plane with a dashed trail in the upper-middle sky, a calm bay with a white sailboat, rolling green hills and a generic coast behind, leafy trees (rising…), no recognisable landmarks and no animals. |

## Reviewing an image

Each image was checked by hand and regenerated if any of these failed:

- It fills the frame edge to edge, with no border and no frame inside the
  picture: no raised rim, no strip along the top, no foliage closing in like
  curtains.
- There's no text, letters, numbers, flags or logos anywhere. Zoom in on
  buildings, boats and vehicles.
- There are no landmarks the scene didn't ask for.
- The top 15% is sky, and the top-left corner is empty.
- The bottom 12% is plain foreground, with the animal standing above it.
- The main landmark is recognisable at 400 px wide.
- The sun is cut from paper, a disc or a star, with no glow, halo, beams or
  bloom of light around it, and it sits in the upper-left sky.
- There are no gradients: every piece and every band of sky is one flat
  colour, and only the drop shadows are soft.
- It is as finely detailed as the rest of the set, not sparse or flat.

The most common failures were a soft glow around the sun, a flag on a
building or boat, and lettering on a vehicle. A plain rerun with the same
prompt usually fixes the glow. Flags and lettering need an exclusion added
to the start of the scene.
