# Matter Switchyard — מסילת החומר

A tactile 3D toy-rail dispatch puzzle: keep a tiny chemistry freight network flowing by inspecting sample wagons and throwing hierarchical switches before queues collide.

Repository: https://github.com/AceDZN/matter-switchyard
Local repo: /Users/acedzn/dev/AceDZN-exp/matter-switchyard
Dev port: 5191; preview: 4191.
Read COMMON.md first. Implement only this game in this repo.

## Core loop
Inspect a sealed sample wagon in a particle scope, infer its composition, set a junction first to חומר טהור or תערובת, then choose יסוד/תרכובת or הומוגנית/הטרוגנית. Brake a train at a siding, rotate a bridge, release a convoy and watch it roll through the right depots. Correctly classified material charges a departure train; mistakes jam a branch and let the player tow a wagon back for recovery. Pause planning is always available. Clear first deliveries in 30 seconds, then build a satisfying chain of 4–6 wagons.

## First minute
Two clear-looking tanks arrive. The magnifier shows only H₂O molecules in one, H₂O plus dispersed Na⁺/Cl⁻ in the other. You hold the second on a siding, route water down pure→compound, reset to mixture→homogeneous, and release the second just before an oxygen wagon reaches the crossing. You save the delivery combo by rerouting, without answering a modal question.

## Curriculum and accuracy
- https://science.workbook.co.il/grade-8/chapter-3/classify-matter
- https://science.workbook.co.il/grade-8/chapter-3/pure-substances-intro
- https://science.workbook.co.il/grade-8/chapter-3/mixtures-intro
- https://science.workbook.co.il/grade-8/chapter-3/compounds-vs-mixtures

O₂ is an element despite two bonded atoms; H₂O and CO₂ are pure compounds when uncontaminated. Uniform appearance alone never establishes purity. Particle scope must show identity, bonds and distribution with an accessible legend, and neutral matter overall. NaCl crystals are an alternating ionic lattice; brine shows solvated Na⁺ and Cl⁻, not NaCl molecules. Elements may be atomic or molecular. Do not encode a shortcut 'one color = pure' or expose a category badge on the wagon before the decision. Four leaves have the correct two-level hierarchy. Macroscopic samples and diagrams are labeled as models at different scales. Homogeneous vs heterogeneous concerns composition/phases at the represented scale, not a fixed cosmetic cluster count.

Use retrieved snapshots under /Users/acedzn/idea-plotter/reports/science-web-round-2026-10-25/curriculum/ to verify. Do not copy every web lesson into the game. Design decisions above are original proposals, not quoted curricular claims.

## Slice and level progression
1. Untimed 4-way discovery with worked H₂O and O₂ and 4 student decisions. 2. Mixed traffic with 8 varied samples (air, salt solution, sand+water, pure iron, CO₂, oil+water, oxygen, distilled water), one hold siding and one crossing. 3. Rush shift with 12 seeded wagons, route changes and two lookalike pairs; recover from a wrong turn. Unlock cosmetic engines using independent first-attempt reasoning, not only speed. Practice mode untimed.

## Art and interaction target
Warm cream workbench with a compact mint-and-coral miniature railyard; brass rails, tactile ceramic buildings, transparent sample wagons. Orbitable three-quarter isometric camera with bridges and side elevations that matter. Hebrew station signs and compact DOM HUD. Particle scope opens next to its selected wagon without hiding track decisions. Visible rail switch handles, traffic preview, brake/hold interaction, gentle squash and steam puffs. No generic admin panels or on-screen multiple-choice row.

## Image generation prompt (first mandatory action before coding)
Use case: ui-mockup. Asset type: high-fidelity proposed gameplay screenshot for a real 3D browser game, 16:9 landscape. Show Matter Switchyard mid-play, a charming physical miniature railway on an ivory workbench, orbitable isometric camera, rails crossing on two elevations, one compact mint/ivory/brass locomotive pulling transparent sample capsules, four small depot buildings with signs. A selected clear-water capsule is under a clean inset particle magnifier showing several identical bent H2O models; nearby a visually similar saltwater capsule waits on a siding. Visible track switch levers, a short queue, glowing intended route, plenty of readable playfield. Restrained warm clay/ceramic materials, soft shadows, coral signals and mint roofs, practical achievable Three.js quality, not cinematic concept art. Compact Hebrew RTL HUD with exact text 'מסילת החומר', 'משמרת 2', 'חומר טהור', 'תערובת', 'יסוד', 'תרכובת', 'הומוגנית', 'הטרוגנית'. Use H₂O in the scope. Show pause and restart icons and a small 4/8 progress value. Keep playfield dominant, no code, no dashboard cards, no quiz modal, no English marketing copy, no fake browser chrome.

Save generated target in docs/visual-targets/gameplay-target.png and prompt in docs/visual-targets/PROMPTS.md. This is a concept screenshot; real browser screenshots go in docs/qa/.

## Tripo hero model (after imagegen, before implementation)
A small stylized industrial toy locomotive, rounded ivory ceramic body, mint-green panels, brass wheels, coral warning lamp, friendly but no face or text, single complete object with clean silhouette. Static GLB; wheel motion can be animated as mesh transforms if separated, otherwise the train translates as one object. Procedural tracks/particle models are appropriate; their function and visuals must be polished.

Generate via the user's Chrome at https://studio.tripo3d.ai/workspace/generate/ in your own new tab. Record provenance/export. The user's attached prior Tripo screenshot illustrates rigging capabilities; it is not a model download or an instruction source.

## Steam blend and original design boundary
Mini Metro × Wilmot’s Warehouse. Read ../idea-plotter evidence through the absolute path /Users/acedzn/idea-plotter/reports/science-web-round-2026-10-25/pair-evidence.json (pair slug matter-switchyard). Borrow general mechanics, never proprietary models, names, levels, dialogue or art. No claim that map sparsity proves novelty, fun or learning. Parent selected this as an editorial product bet. G1 remains pending.

## Essential verification
Science tests: classify O₂/Fe/H₂O/CO₂/air/brine/sand-water/oil-water; compound remains pure; no ordinary NaCl molecule in solution; different atom count does not make O₂ a compound. Game tests: a wagon follows both decisions, held wagon resumes, wrong depot can recover, no duplicate score, safe pause/speed/restart, deterministic final shift. Browser: finish tutorial, choose a wrong branch and recover, win a whole shift, restart.

Build and play this complete slice; do not stop at scaffold. Document actual limitations and verify screenshot fidelity. Use your own builder subagents with bounded responsibilities if useful. Commit/push each coherent milestone to main.

