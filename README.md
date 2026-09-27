# Moby Dick, scene by scene

A single printed risograph sheet holding fifteen cut-away dollhouse dioramas of *Moby-Dick*, packed into one stepped isometric block. Everything is drawn in code on one Canvas 2D element. There are no images, fonts, libraries or external scripts, and the page makes exactly one network request (itself).

- File: `index.html`, **137,596 bytes** (about 134 KB), unminified.
- Open it in any modern browser. It prints itself onto the sheet one ink at a time, then tours the scenes.

## Controls

The tour runs on its own. Any input pauses it, and it picks up again from the nearest scene after 14 seconds of no input.

- Drag to pan (with inertia). Pinch or scroll wheel to zoom toward the cursor.
- Double-click or double-tap a scene to fly to it.
- Arrow keys pan, `+` and `-` zoom, `0` fits the whole sheet.
- `C` shows or hides the chapter card.

## The scenes

Chapter numbers and every quote come from the Project Gutenberg text of *Moby-Dick; or, The Whale* (ebook #2701). Each quote was checked word for word against that text, including Melville's spelling ("centre", "panelled") and curly apostrophes. The white whale appears in every scene; where it shows up is noted in brackets.

1. **Chapter I, Loomings.** Ishmael on the Manhattan wharves. [a hanging whale shop sign]
   "Posted like silent sentinels all around the town, stand thousands upon thousands of mortal men fixed in ocean reveries."
2. **Chapter III, The Spouter-Inn.** The besmoked painting and the whale-jaw bar. [the painting]
   "But what most puzzled and confounded you was a long, limber, portentous, black mass of something hovering in the centre of the picture over three blue, dim, perpendicular lines floating in a nameless yeast."
3. **Chapter VIII, The Pulpit.** Father Mapple climbs to his ship's-bow pulpit. [carved on the pulpit front]
   "Its panelled front was in the likeness of a ship’s bluff bows, and the Holy Bible rested on a projecting piece of scroll work, fashioned after a ship’s fiddle-headed beak."
4. **Chapter X, A Bosom Friend.** Queequeg and Ishmael by the fire. [a patch in the counterpane]
   "I felt a melting in me. No more my splintered heart and maddened hand were turned against the wolfish world. This soothing savage had redeemed it."
5. **Chapter XVI, The Ship.** The Pequod fitting out, with Peleg in his wigwam. [the whalebone tiller]
   "She was a ship of the old school, rather small if anything; with an old-fashioned claw-footed look about her."
6. **Chapter XXXV, The Mast-Head.** Ishmael on the lookout high above the deck. [under the sea, in the cut face]
   "There you stand, lost in the infinite series of the sea, with nothing ruffled but the waves."
7. **Chapter XXXVI, The Quarter-Deck.** Ahab and the gold doubloon nailed to the mast. [struck on the doubloon]
   "Talk not to me of blasphemy, man; I’d strike the sun if it insulted me."
8. **Chapter XLIV, The Chart.** Ahab tracing courses under the swinging pewter lamp. [drawn on the chart]
   "While thus employed, the heavy pewter lamp suspended in chains over his head, continually rocked with the motion of the ship, and for ever threw shifting gleams and shadows of lines upon his wrinkled brow, till it almost seemed that while he himself was marking out lines and courses on the wrinkled charts, some invisible pencil was also tracing lines and courses upon the deeply marked chart of his forehead."
9. **Chapter LXXXVII, The Grand Armada.** A boat in the still heart of the herd, with mothers and calves below. [spouting at the far edge of the herd]
   "But far beneath this wondrous world upon the surface, another and still stranger world met our eyes as we gazed over the side."
10. **Chapter XCVI, The Try-Works.** The fires at night on a dark sea. [a shape in the smoke]
    "Look not too long in the face of the fire, O man! Never dream with thy hand on the helm!"
11. **Chapter CX, Queequeg in His Coffin.** The carpenter, the coffin and Pip. [carved on the coffin lid]
    "How he wasted and wasted away in those few long-lingering days, till there seemed but little left of him but his frame and tattooing."
12. **Chapter CXIX, The Candles.** Corposants burning on the yard-arms over a storm sea. [swimming under the storm, in the cut face]
    "All the yard-arms were tipped with a pallid fire; and touched at each tri-pointed lightning-rod-end with three tapering white flames, each of the three tall masts was silently burning in that sulphurous air, like three gigantic wax tapers before an altar."
13. **Chapter CXXXIII, The Chase, First Day.** The whale bites Ahab's boat in two. [in full]
    "Like noiseless nautilus shells, their light prows sped through the sea; but only slowly they neared the foe."
14. **Chapter CXXXV, The Chase, Third Day.** Ahab's last dart as the Pequod is struck. [in full]
    "Towards thee I roll, thou all-destroying but unconquering whale; to the last I grapple with thee; from hell’s heart I stab at thee; for hate’s sake I spit my last breath at thee."
15. **Epilogue.** Ishmael adrift on Queequeg's coffin, the Rachel coming. [swimming deep in the cut face]
    "Buoyed up by that coffin, for almost one whole day and night, I floated on a soft and dirgelike main."

## The layout

All fifteen dioramas share one isometric grid and one scale, so a person is the same size in every room. They are packed into a single block, the way a printed map would be. The tiles come in different sizes, from the big halls to the small ship and sea slabs. An even strip of paper runs between neighbouring tiles, and the block fills most of the sheet. Each of the four rows is centred on the others, so the outside edge steps out into a rough diamond instead of a clean rectangle.

The rooms sit on thin floors, while the sea scenes are thick teal blocks. The four ship scenes float in blocks of sea cut flush with the hull, so the hold shows in section below the waterline. Where a room is a little shallower than the rest of its row, a strip of paving in front of it evens the row up.

Seen from far off, walls and masts hide part of the tile behind them, the way they would in a real dollhouse. The tiles always draw back to front, so nothing ever jumps in front of something that should cover it. When you zoom into a scene, or the tour stops at one, whatever stands in front of it (a neighbour's wall, the masts of a ship) fades to a faint ghost over it, so the scene you are looking at is never blocked.

## The four inks

| Ink | Hex | Screen angle |
|---|---|---|
| Midnight | `#283654` | 45° |
| Sea Teal | `#008088` | 15° |
| Scarlet | `#E8463A` | 75° |
| Sunflower | `#FFD630` | 0° |

The stock is cream, `#F4ECD8`. Every colour on the sheet comes from these four inks overprinting each other. Browns are Scarlet over Sunflower with a little Midnight, greens are Teal over Sunflower, the night seas are heavy Midnight with some Teal, and so on. Each chapter card picks up one of the inks as its accent.

## How the print simulation works

Each scene is drawn twice over, conceptually. First, the drawing code paints **ink density** rather than colour: every shape says how much of each of the four inks it wants, from 0 to 1. Those densities go into offscreen canvases, one channel per ink, plus a separate set of channels for linework and one for knock-outs. When a shape is filled it clears the inks underneath it (a knock-out, as a real separation would), and glazes and glows add on top instead.

Then a halftone pass turns density into dots. For each ink the page lays a square grid of cells rotated to that ink's screen angle, 3.2 sheet units apart. Each cell samples the density at its centre and draws a round dot whose area matches it, so 20% ink covers about 20% of the cell. Past about 50% the dots merge and turn into holes, like a real screen. Every cell gets a little seeded jitter in position and size, and each ink plate is shifted by its own small misregistration offset, so edges never line up perfectly and you see thin slivers of paper and overlap along them.

Solids are not perfectly solid. Riso drums starve in patches, so a slow noise field thins the ink here and there, and a finer grain knocks out specks of paper inside flat areas. Linework is printed as solid ink on top of the screens rather than being screened itself.

The inks are combined by **multiply**, the way translucent soy ink stacks on paper: the paper colour is multiplied by each ink's colour in proportion to its coverage at that pixel. That is why Teal over Sunflower reads green and Scarlet over Midnight goes nearly black.

Light is done the same way. Lamps, fires, the moon and the corposants are drawn as stepped rings of Sunflower and Scarlet density, so they print as banded halftone halos instead of smooth gradients.

**Boiling lines.** Every scene and every figure is baked in three variants. Each variant runs the same drawing code with a different seed that wobbles the strokes slightly and changes their taper, and the display cycles through the three at about 3 Hz. All randomness is seeded, so the sheet prints identically every time.

**Print-in.** On load the first proof of each scene is also kept as four separate plates. The sheet then prints Sunflower first, then Scarlet, Sea Teal and Midnight, each pass rolling down the sheet over the last, before the tour starts.

**Staying fast.** The halftone is computed on the CPU in small row slices between frames, so the page never locks up. Scenes are baked at a few zoom levels and the right one is picked for the current zoom and screen density, so the dots stay crisp on a 4K display without holding every scene at full size in memory. People and boats are baked separately as small sprites at 12 poses per second and cached, which is why they can walk, row and haul while the rooms stay still. Phones get a lower memory budget and a lower top zoom.

## Notes

- The people share one jointed skeleton with keyframed clips (walking, rowing, hauling, climbing, praying, harpooning and about two dozen others). Clothing is per character: Ahab's whalebone leg and scar, Queequeg's tattoos, Mapple's black frock, and so on.
- The reference site linked in the brief could not be reached from the build environment, so the layout follows the written description rather than a side-by-side look.
