# PolyOrganic: the radial material dial

> Study, added 2026-11-14. A full writeup of one shipping product and the interface ideas worth stealing from it.

*Every material. One dial. A Blender add-on that turns material picking into turning knobs on a wheel.*

## What it is

PolyOrganic (sold as "Poly Organic") is a commercial add-on for Blender by Poly Playground. It replaces node wrangling and texture hunting with a circular dial that sits in the viewport: pick a material family, pick a style, pick a layout, then turn knobs for detail, form, surface, life, colour, and depth, all while the object in front of you changes live. Every material is procedural Blender nodes, built from patterns like noise and cells, with zero image textures. The product page's line is "Real-world materials in seconds" and the demo tagline is "Every material. One dial."

Facts from the product page, opened 2026-11-14:

- Price $29.00 USD, in stock on Superhive (formerly Blender Market). Every update is free, and new materials are added regularly.
- Current version 1.46. New in 1.46: all 13 wood styles rebuilt from expert recipes and calibrated against real timber photos; roofing rebuilt with 11 layouts and true tile profiles (Double Roman, Marseille, Spanish barrel, slate, architectural shingles, cedar shakes, corrugated, box rib, standing seam), overlap shadows, lichen, and broken tiles; baking several materials on one object fixed; the dial resizes by dragging its corner grip.
- 200+ one-click styles, 20+ material types, 90+ layouts and patterns, 0 image textures.
- Blender 4.2 or newer (tested on 5.2 LTS). Renders the same in Cycles and EEVEE. Windows, macOS, Linux. Install by dragging the .zip into Blender, or Preferences, Get Extensions, Install from Disk.
- Materials are standard Blender nodes, so a file renders for anyone, with or without the add-on. No UVs needed. Patterns are projected at real-world size, and you can use your own UVs whenever you prefer.
- Launched September 22, 2026. The launch post is the same demo as the TikTok video preserved in the companion walkthrough. The launch discussion reports 35% off during early access with free updates.

## The dial

The dial is a dark circle in the lower viewport, in front of the work. It has three parts: an inner ring of pages, an outer ring of choices or knobs, and a center knob that shows the value of whatever you are touching.

- Inner ring, 10 pages: Material, Style, Layout, Detail, Form, Surface, Life, Colour, Depth, Saved. The active page lights up orange.
- Outer ring, changes with the page. On Material it holds family swatches (13 in the video: Blank, Wood, Marble, Stone, Concrete, Brick, Tile, Fabric, Twill, Carpet, Brushed, Leather, Ground). On Style it holds style swatches for the chosen family (15 wood species in the video). On Layout it holds layout icons (6 for wood, 6 for brick). On Detail, Form, Surface, Life, Colour, and Depth it holds that page's knobs.
- Center dial: shows the name and value of the control being dragged, with an orange arc for percentages. For Hue A it becomes a full hue wheel reading in degrees (34 degrees in the video). Seed reads 0.0. Ring Spacing reads 6.0 mm. Edge Width reads 9.8 mm. Scale reads x0.26.
- A breadcrumb pill above the dial names the full path: family, style, layout, separated by middle dots. "Wood · White Oak · Solid". "Brick · London Stock · Flemish". "Ground · Lawn and Mud". When the object has no PolyOrganic material, the pill names the object instead: "PolyOrganic · Plane", "PolyOrganic · Cube.002".
- A small knob sits above the breadcrumb. It appears to be the current page's first control (Ring Spacing on Detail, Structure on Form, Gloss on Surface, Edge Wear on Life, Hue A on Colour, Depth on Depth), while the center dial shows the control actually being dragged. The video never holds still long enough to prove this reading; it is the best fit for every frame checked.
- Three buttons under the dial: Surprise, Save, Close. Surprise is the randomize control (the product page calls the action Random: it morphs into a fresh material for instant ideas). Save stores the look in the library. Close dismisses the dial.
- From the product page: Simple mode shows only the controls that change the look most; Advanced shows everything. Drag the knob, scroll, or type to search any material. Resize and move it anywhere, or minimise it to a bar. Ctrl+click another object to paste the material onto it.
- Empty state: an object with no PolyOrganic material gets a dark circle reading "No PolyOrganic material here" with "Click to start" in orange, and a Close button below it. The pill above names the object. If the selection is not a mesh at all, the circle reads "Select a mesh to begin" instead (seen with an area light selected, pill reading "PolyOrganic · PolyStudio_Area_Light").

## How it works: Pick, Turn, Ship

The product page's three steps, all inside the viewport:

1. Pick. Select any mesh and open the dial. Choose a material family, then a style. Examples on the page: Cathedral oak, Old Red brick, Colorbond steel, Spanish barrel tiles.
2. Turn. Drag or scroll any knob: size, colour, wear, rust, moss, depth. Everything morphs live in Material Preview and renders the same in Cycles and EEVEE.
3. Ship. Render it as is, save it to your library, or bake it to game-ready texture maps in the background while you keep working.

## The material system

From the product page, unless noted:

- What is inside: Wood (solid, boards, parquet, cladding), Brick and concrete, Stone, marble and terrazzo, Tiles, Metal (brushed, rusted, galvanised, painted), Roofing (tiles, slate, shingles, shakes, sheet metal), Roads and gravel, Plastic and rubber, Fabric and leather, Ground, bark and foliage, Water and ice, Glass and gems, Paint and paper, Skin.
- Built from the real thing: every family is modelled on how the real material is made, and checked side by side against real photographs. Wood grows rings, pores, and knots from a real log. Roof tiles have true profiles and overlapping courses. Brick has mortar, chips, and kiln variation.
- Real-world scale: patterns are sized in metres, so a brick is a brick on any object. Modes named on the page: Real Size, Stretch with Object, World Space, or your own UV map. In the video, scaling the cube into a plank stretches the wood grain with it, and ring spacing reads in millimetres.
- Grain follows the shape: wood grain runs along chair legs, rails, and branches automatically. Roof courses follow the slope, whichever way the roof faces.
- Weather and age: edge wear, chips, scratches, dirt, dust, grime, rust, moss, lichen, and wet surfaces, placed where they really gather: edges, cavities, and sky-facing faces. In the video the Life page carries Edge Wear, Edge Width, Exposed Metal, Dirt, Dust, Grime, and Wet.
- Layers: stack materials on top: render falling off brick, moss, grass, mud, puddles, snow, sand, leaves, paint, reflective bands. Placed by edges, top faces, undersides, zones, or natural patches. Product page only; the launch video does not show layers.
- Real Depth: one switch turns texture into true displacement: mortar joints recess, tiles overlap, weathered grain stands proud, clean silhouettes with no spikes. In the video the Depth page carries a Depth knob plus Smart Limits (Auto), Relief, Micro, a Real Geometry toggle, quality buttons (Draft, Balanced, Final), World and Obj projection buttons, and a 1:1 button.
- Add your own detail: drop in features on any material: veins, cracks, crystals, pores, grain, strata, clouds, dots, stripes. Each with its own colour and placement. Product page only.
- Fast when it matters: Draft, Balanced, and Final quality, plus node optimisation that strips everything a material does not use, so heavy scenes stay responsive.
- Your library: save any look with one click, reuse it across projects, and share it with your team as an asset.
- Bake to textures: Colour, roughness, metallic, normal, height, AO, and an ORM pack, at up to 8K. Bakes in the background, handles several materials on one object, never touches your UVs. The October 5 demo reel shows the bake exporting Base colour, Roughness, and Height maps for a Calacatta marble.

## The workflows the videos show

- The plank (launch video, Act 1): cube to White Oak to a long plank, then a tour of every page. Detail (Ring Spacing 6.0 mm, Figure 56%), Form (Structure 100%, Scale x0.26, Flow 2%), Surface (Gloss 23%, Coat 25%), Life (Grime 100%, Dirt 100%), Colour (Hue A 34 degrees), Depth (Depth 26%). Full frame-by-frame record in the companion walkthrough.
- The floor (Act 2): a fresh plane gets Wood, Oak, Boards, then Walnut Herringbone, then Life effects (Edge Width 9.8 mm, Grime 100%) that visibly age the floor pale.
- Rapid cycling (Act 3): a fresh cube takes 31 named looks in about 15 seconds (32 stops counting the opening Blank), one click per material, live. 30 of them are distinct (Linen appears twice). The full sequence is in the walkthrough.
- The table (October 5 reel, from the search-result summary): a coffee table demo. Wood Cathedral Boards, scale to x11.56, eyedropper copies the wood to the legs, legs switch to Metal Gunmetal Smooth, herringbone floor at board width 9 cm and length 76 cm, Fabric Shag Carpet Pile rug, Stone Slate Slab top, "Crack it" adds fissures at 40 cm spacing, Undo anything reverts to stone, then Marble Calacatta, then the PBR bake.
- The stack (September 29 reel, from the search-result summary): Wood Cathedral Solid, Size from x5.00 down to x2.54, plank duplicated into a staggered stack of five.

## What it teaches the library

- The nested-ring radial picker: two rings plus a center readout. The inner ring is navigation (pages), the outer ring is choice (swatches, layouts, knobs), the center is feedback (name plus value). One control, three jobs, no panels. See [016 Pie menus](../entries/016-pie-menus.md).
- The center dial as a live readout: the value you are changing is always in the middle, big, in the unit that fits the parameter (mm, cm, percent, degrees, x multiplier). See [061 Feedback loops](../entries/061-feedback-loops.md).
- Contextual knobs: the outer ring's controls change with the material. Wood gets Ring Spacing and Figure; brick gets bond layouts; leather gets Grain Size and Creases. Nothing on screen is dead for the current choice. See [022 Per-context profiles](../entries/022-per-context-profiles.md).
- See it before you commit: every pick and every knob drag changes the object live. There is no Apply button and no preview pane; the object is the preview. See [017 See it before you commit](../entries/017-see-it-before-you-commit.md).
- The breadcrumb that names the whole choice: family, style, layout, always visible, in plain words. It doubles as the state display and the shareable name of a look. See [071 Microcopy that earns its place](../entries/071-microcopy-that-earns-its-place.md).
- Real-world units in the UI: millimetres, centimetres, and metres instead of 0 to 1 sliders. A board is 9 cm wide because boards are 9 cm wide.
- Surprise as a first-class verb: randomize sits beside Save and Close, not buried in a menu. One click, a fresh material, for instant ideas. See [066 Playground mode](../entries/066-playground-mode.md).
- The empty state that starts the flow: "No PolyOrganic material here. Click to start." names the object, names the problem, and offers the one next step. And when the selection is not a mesh at all, it says so instead: "Select a mesh to begin." See [031 Empty states and error states done well](../entries/031-empty-states-and-error-states-done-well.md).
- Weather and age as controls, not afterthoughts: dirt, grime, edge wear, and wetness get their own page (Life), with the same knob treatment as colour and form.
- Copy by clicking the source: Ctrl+click another object pastes the material onto it; the October demo shows an eyedropper doing the same to the table legs.
- Forgiving by default: the October demo shows "Undo anything" reverting a material swap. Nothing is final until you save or bake it. See [033 Forgiving UI](../entries/033-forgiving-ui.md).
- Simple and Advanced on the same dial: the same control shows a few knobs or all of them, instead of two different interfaces. See [012 Progressive disclosure](../entries/012-progressive-disclosure.md).

## What it does not give us

- It is paid ($29) and Blender-only, with no public repo and no code to take. Everything reusable here is ideas and interaction patterns, rebuilt from scratch.
- The rendering fidelity does not transfer: PolyOrganic renders through Cycles and EEVEE node graphs. A PBR-lite renderer on weak hardware gets simpler patterns and a Reblend-grade look, not photoreal wood.
- True displacement needs a displacement pipeline; the Real Depth switch has no cheap equivalent without one.
- Layers (stacked materials) are a second material system. The common cases are covered by the Life page's weathering; full layering is a bigger build.
- The 200 styles and 90 layouts are a catalog built over time. A first version ships a small registry (a dozen or so styles, a handful of layouts) and grows it.
- The dial's cost on weak hardware is unproven: the video runs on the creator's machine, and the library's bar (cheap motion, 8 GB, no GPU) still applies to anything built from this.

## The creator

Poly Playground, @polyplaygroundhub: 55K followers on Instagram, 10K on Facebook (as observed November 2026). PolyOrganic is the newest of several Blender add-ons from the same creator. The others, from search-result summaries of the creator's reels (secondary sources): Poly Render Pro (render optimization; November 2024 reel), Polyphantom (render queue and background rendering, via a PolySuite pro subscription; July 2025 reel), Poly Focus (real-time auto-focus, bake focus into animations; October 2025 reel; PolySuite.app). The launch video's narration says the creator prefers to build the system himself rather than use AI generation, and the launch discussion confirms the materials are Blender node-based, not AI-generated.

## Open questions

- Polyhertz: an October 2, 2026 reel summary names the tool "Polyhertz" while showing the same dial UI and table demo as the October 5 PolyOrganic reel. Whether that was an earlier name, a separate product, or a mislabel is unresolved.
- The TikTok post date for the launch video is unconfirmed; the same demo was posted to Instagram on September 22, 2026.
- The knob above the breadcrumb is read here as the current page's first control; the video never holds still long enough to prove it.
- The "Blank · Oak" breadcrumb at 1.0s (Blank selected, cursor hovering Wood) suggests the breadcrumb previews the hovered family's first style. Unproven; noted, not asserted.

## See also

- [PolyOrganic launch video, frame by frame](polyorganic-video-walkthrough.md)
- [016 Pie menus](../entries/016-pie-menus.md)
- [017 See it before you commit](../entries/017-see-it-before-you-commit.md)
- [031 Empty states and error states done well](../entries/031-empty-states-and-error-states-done-well.md)
- [033 Forgiving UI](../entries/033-forgiving-ui.md)
- [061 Feedback loops](../entries/061-feedback-loops.md)
- [066 Playground mode](../entries/066-playground-mode.md)
- [071 Microcopy that earns its place](../entries/071-microcopy-that-earns-its-place.md)

## Sources

- Poly Organic, The Ultimate Procedural Material Tool, Superhive, opened 2026-11-14 — https://superhivemarket.com/products/poly-organic---the-ultimate-procedural-material-tool
- PolyOrganic launch video, TikTok @polyplaygroundhub, post date unconfirmed (same demo as the September 22, 2026 Instagram reel below) — frames extracted from the uploaded video and read individually; half-second sampling through Act 3
- Poly Playground launch reel, Instagram @polyplaygroundhub, 2026-09-22 — https://www.instagram.com/reel/Ddkr3WOPePW/ (secondary source; search-result summary)
- Poly Playground narrated demo reel, Instagram @polyplaygroundhub, 2026-09-25 — https://www.instagram.com/reel/DdtfoDGP_W5/ (secondary source; search-result summary)
- Poly Playground plank-stack reel, Instagram @polyplaygroundhub, 2026-09-29 — https://www.instagram.com/reel/Dd3P6uayJOw/ (secondary source; search-result summary)
- Poly Playground table demo reel, Instagram @polyplaygroundhub, 2026-10-05 — https://www.instagram.com/reel/DeGj9HjPFmh/ (secondary source; search-result summary)
- Poly Playground table demo reel ("Polyhertz" naming), Instagram @polyplaygroundhub, 2026-10-02 — https://www.instagram.com/reel/Dd_Iag7ytNs/ (secondary source; search-result summary)
- Poly Focus reel, Instagram @polyplaygroundhub, 2025-10-19 — https://www.instagram.com/reel/DQAORjqCHIM/ (secondary source; search-result summary)
- Poly Render Pro reel, Instagram @polyplaygroundhub, 2024-11-17 — https://www.instagram.com/reel/DCd4-hlPYuX/ (secondary source; search-result summary)
- Polyphantom reel, Instagram @polyplaygroundhub, 2025-07-29 — https://www.instagram.com/reel/DMscGBjKoXP/ (secondary source; search-result summary)
