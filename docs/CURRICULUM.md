# Matter Switchyard — curriculum and science decisions

Audit date: 25 October 2026. Audience: Hebrew-speaking grade 8 students.

This is an original game design and modelling log. It aligns the dispatch decisions with the four requested Workbook modules; it is not a reproduction of the lessons, a claim of Ministry approval, or evidence of learning effectiveness. Classification in this slice is based on explicitly specified idealised samples, not an assay of a real-world product.

## Canonical curriculum

| Module | Canonical link | Use in the game |
| --- | --- | --- |
| סיווג חומר | [classify-matter](https://science.workbook.co.il/grade-8/chapter-3/classify-matter) | The first switch separates pure substance from mixture; each branch then has its own two leaves. |
| חומרים טהורים: יסודות ותרכובות | [pure-substances-intro](https://science.workbook.co.il/grade-8/chapter-3/pure-substances-intro) | A pure element can contain single atoms or molecules of one element; pure compounds contain chemically combined elements in a definite composition. |
| מהן תערובות? | [mixtures-intro](https://science.workbook.co.il/grade-8/chapter-3/mixtures-intro) | Mixtures contain more than one substance. Compare uniform composition with distinguishable phases or regions at the represented scale. |
| תרכובות מול תערובות: השוואה מעמיקה | [compounds-vs-mixtures](https://science.workbook.co.il/grade-8/chapter-3/compounds-vs-mixtures) | Contrast a pure compound with a mixture containing compounds; use particle identity and arrangement as evidence. |

The full local Markdown snapshots of all four modules were read from `/Users/acedzn/idea-plotter/reports/science-web-round-2026-10-25/curriculum/`. The existing `BUILD_HANDOFF.md` and `COMMON.md` supply additional scientific safeguards and define the game scope. These local reference files were read only; this audit does not modify them.

## Learning decisions that operate the railway

The visible rail hierarchy must be exactly:

```text
חומר
├── חומר טהור
│   ├── יסוד
│   └── תרכובת
└── תערובת
    ├── הומוגנית
    └── הטרוגנית
```

1. Inspect the sample model to decide whether the wagon contains a single chemical substance or a mixture.
2. For a pure sample, distinguish one element from a compound containing more than one element. Count **element identities**, not the number of atoms in a molecule.
3. For a mixture, inspect composition and phases at the scale shown. Uniform molecular mixing and separate material regions are different evidence.
4. Set both switches, hold or release the wagon, and see the consequence at the depot. A wrong route produces a recoverable rail problem and brief evidence-based feedback.

An element and a compound are both under `חומר טהור`. The four final depots must never appear as four unrelated categories. The junction state and actual travelled route must match; selecting a correct leaf in the wrong parent branch is not a correct classification.

## Proposed sample roster

The first eight samples are the required slice roster. Internal IDs are suggestions for deterministic data and tests, not player-facing answer badges. Formulas below must use LTR isolation inside the Hebrew interface.

| Suggested ID | Sample shown after inspection | Required route | Evidence the scope must show | Macroscopic / modelling safeguard |
| --- | --- | --- | --- | --- |
| `water` | מים מזוקקים — H₂O | חומר טהור → תרכובת | Several identical bent H₂O molecules. Every molecule has two labelled H atoms bonded to one labelled O atom. | Clear liquid. Caption specifies an idealised pure-water sample. Do not classify every real bottle labelled “water” as pure. |
| `oxygen` | חמצן — O₂ | חומר טהור → יסוד | Identical O–O pairs, with O labels on both atoms. | Clear gas. Two atoms per molecule do not make it a compound. |
| `iron` | ברזל טהור — Fe | חומר טהור → יסוד | Repeated Fe atoms in a simplified solid lattice, all identified as Fe. | The selected specimen is pure iron, not steel, a rusty object, or an unspecified household metal. Fe is not depicted as little Fe₂ molecules. |
| `carbon-dioxide` | פחמן דו־חמצני טהור — CO₂ | חומר טהור → תרכובת | Identical O–C–O molecules with one C and two O atoms per molecule. | Clear gas. The model shows a pure sample, not exhaled air. Do not call CO₂ an oxidising gas. |
| `air` | אוויר נקי ויבש | תערובת → הומוגנית | Interspersed N₂ and O₂ molecules, with a small number of Ar atoms / CO₂ molecules if supported. Existing molecules keep their bonds. | This is a simplified model of clean, dry, well-mixed air, with no droplets, dust or smoke. The tiny display is not a claim of exact atmospheric percentages. |
| `brine` | מלח מומס במים | תערובת → הומוגנית | H₂O molecules and dispersed Na⁺ and Cl⁻ ions. Equal Na⁺ and Cl⁻ counts make the depicted sample electrically neutral. Show surrounding water or a clear “יונים במים” legend. | Clear liquid, deliberately similar to pure water. The specified salt amount is fully dissolved, with no salt crystals at the bottom. No ordinary NaCl molecule is drawn in solution. |
| `sand-water` | חול במים | תערובת → הטרוגנית | Water and distinct solid sand grains / solid regions. Water molecules and grains are different representation levels and must be labelled accordingly. | Visible solid–liquid regions, including sediment. A grain is a macroscopic aggregate, not a large atom or a “sand molecule.” Do not claim that all natural sand is pure SiO₂. |
| `oil-water` | שמן ומים | תערובת → הטרוגנית | A water-rich region and a separate oil-rich layer or droplets. Clearly label the separate material regions. | Use a two-region material model, without inventing one universal formula for oil. Oil itself contains multiple substances; the water–oil separation is sufficient evidence here. |

Optional only if needed for a later challenge: `salt-crystal`, מלח נתרן כלורי טהור — NaCl, is `חומר טהור → תרכובת`. Render a balanced alternating Na⁺/Cl⁻ ionic lattice with a repeating 1:1 ratio and a caption identifying it as a lattice. Do not render isolated Na–Cl dumbbells or teach that every compound is made of discrete molecules. This optional sample is not needed to finish the required eight-sample slice.

## Science decision log

| Decision | Implementation consequence and reason |
| --- | --- |
| Purity means a single chemical substance in the specified model. | Identical H₂O molecules constitute a pure compound despite containing two element types. A pure ionic solid can contain different ions in a fixed lattice. “One colour” and “one kind of sphere” are never the purity algorithm. |
| Element identity is separate from atom count. | O₂ is an element and Fe is an element. The scope legend must support both molecular and atomic / lattice representations. The O₂ feedback explicitly names the one element, oxygen. |
| Particle connectivity is evidence, not a universal “any bonds = compound” shortcut. | Mixtures such as air and brine contain molecules with internal bonds. The question is whether multiple substances coexist, not whether any bond appears anywhere. Hydrogen-bond networks and solvation are outside the scoring rule. |
| Ionic compounds require a lattice / ion model. | The handoff corrects the molecular shorthand in the source material. NaCl solid is a lattice; brine contains solvated ions. The game does not pretend that dissolving NaCl creates loose neutral Na and Cl atoms or ordinary NaCl molecules. |
| Homogeneity is not cosmetic spacing. | Random particle motion, slight local fluctuations, or a camera angle cannot change a sample's category. Homogeneous samples have a deliberately mixed model; heterogeneous examples show meaningful separate phases or material regions. Never classify by a fixed cluster count or pixel-colour variance. |
| Appearance alone does not establish purity. | Pure water and brine share a clear-liquid wagon appearance. Pure O₂ and clean air share a clear-gas appearance. The scope supplies the missing compositional evidence. A clear vessel is not a “pure” hint. |
| Scale and representation are visible. | The wagon is a sample-scale toy vessel. The scope says `מודל חלקיקים — לא בקנה מידה`. Water molecules, ions, metal atoms, sand grains and oil layers receive the appropriate legend; their drawn sizes and counts are illustrative. |
| Models are chemically neutral overall. | Molecular examples are neutral. Brine and an optional salt lattice use equal positive and negative charges. Particle labels and charges remain readable at the supported classroom viewport. |
| Variable mixture composition has limits. | The mixture examples use specified compositions. Do not repeat “any amount of salt dissolves” or imply that a saturated solution with excess crystals remains one homogeneous phase. Solubility and saturation are outside this slice. |
| Physical separation is contextual, not a new action system. | If feedback mentions separation, ordinary filtration separates suspended sand, not dissolved salt. Evaporation can leave salt behind; collecting water requires an appropriate condensation process. No filter animation may turn brine into pure water. |
| Source simplifications are not copied as absolute laws. | Avoid “every compound is a molecule,” “there are no chemical bonds in mixtures,” “all mixtures are easy to separate,” “mixing never changes energy,” and “heat can never decompose compounds.” These are not needed for the four-way task. |
| Avoid unrelated unsafe or inaccurate source examples. | No tasting samples, practical mixing instructions, claims that pure chemicals are inherently safe, or general advice to put water on fires. Do not use the snapshot's CO₂ oxidiser description, boiling-point claims, or HCl-as-a-pure-liquid shorthand as game rules. The game has no temperature or reaction puzzle. |
| Explanation follows an action. | Before a decision, the scope reveals evidence but never a category badge or correct destination. After a delivery or wrong turn, one short sentence explains the relevant observation. Corrective feedback never silently changes the sample or gives points twice. |
| Reward independent classification. | Record first-attempt success separately from a corrected delivery. Recovery remains available without erasing the misconception history. Cosmetics can reward first-attempt reasoning; speed alone does not represent science mastery. |

## Hebrew feedback bank

These are original microcopy proposals. Display only the sentence relevant to the sample and mistake, with the observed model still available.

| Situation | Suggested feedback |
| --- | --- |
| Pure water delivered | `כל המולקולות כאן הן H₂O. זהו חומר טהור מסוג תרכובת.` |
| O₂ sent to compound | `בכל זוג יש רק אטומי חמצן. O₂ הוא יסוד, גם כשיש שני אטומים במולקולה.` |
| Pure CO₂ sent to mixture | `כל המולקולות זהות: CO₂. כמה סוגי אטומים קשורים יכולים ליצור תרכובת טהורה.` |
| Brine sent to pure | `יש כאן מים וגם יוני נתרן וכלור. המראה השקוף אינו מעיד על טוהר.` |
| Brine sent to heterogeneous | `היונים מפוזרים בתוך המים בלי שכבה נפרדת. זו תערובת הומוגנית.` |
| Air sent to element | `נראות כאן מולקולות של כמה גזים. אוויר נקי ויבש הוא תערובת הומוגנית.` |
| Iron delivered | `הדגימה הזו מכילה רק ברזל. יסוד יכול להופיע גם כמוצק של אטומים.` |
| Sand–water sent to homogeneous | `גרגרי החול נשארים אזור מוצק נפרד מהמים. זו תערובת הטרוגנית.` |
| Oil–water sent to homogeneous | `נראות שתי שכבות שונות. השמן והמים יוצרים כאן תערובת הטרוגנית.` |
| Recovery prompt | `אפשר לגרור את הקרון חזרה, לבדוק שוב ולשנות את המסילה.` |

Use text labels / formulas, charge signs and different atom sizes or patterns alongside colour. Chemical formulas belong in isolated LTR spans; surrounding explanations, switch controls and progress remain RTL. Sound is supplementary, never the only feedback.

## Proposed science sequence

These are integration suggestions; the lead owns the final deterministic level data.

- **Discovery:** worked H₂O and O₂, then four independent decisions covering all leaves: brine, sand–water, pure CO₂ and pure Fe. The first clear-water / brine pair introduces the need to inspect while a held wagon keeps the rail action manageable. Worked deliveries must not masquerade as independent reasoning in the result.
- **Mixed traffic:** the eight required samples, including both clear-liquid and clear-gas lookalike pairs. Use the hold siding to inspect rather than forcing guesswork under a clock.
- **Rush shift:** 12 seeded wagons from the same roster, repeat both lookalike pairs, change routes, and permit wrong-depot recovery. A suitable roster is H₂O, brine, O₂, air, CO₂, oil–water, Fe, sand–water, brine, H₂O, air, O₂. Shuffling / arrival timing may vary deterministically; the scientific identities do not.
- **Practice:** untimed replay with pause planning and the same evidence. Category feedback comes after a route commitment; the scope itself does not contain the answer label.

## Integration audit and tests

Required automated domain cases:

1. Classify O₂ and Fe as pure elements; H₂O and CO₂ as pure compounds; air and brine as homogeneous mixtures; sand–water and oil–water as heterogeneous mixtures.
2. Both parent and leaf are required. A route under the wrong parent cannot be accepted because its leaf index coincidentally matches.
3. H₂O / CO₂ do not become mixtures because their atom identities or atom counts differ. O₂ does not become a compound because it has two atoms.
4. The sample specification, scope legend and delivered answer refer to the same ID. A lookalike liquid or gas cannot inherit another wagon's scope or stale feedback after selection changes.
5. Brine data has H₂O plus Na⁺ and Cl⁻, balanced charges, no neutral free sodium / chlorine atoms, and no ordinary NaCl molecular pair. Optional solid NaCl uses lattice data and remains a pure compound.
6. Classification does not change when particle positions, illustrative counts, colours, camera angle, seed or animation time change.
7. Holding, pausing, recovering and retrying do not mutate scientific identity. A corrected delivery scores once and is recorded separately from first-attempt success.

Required human browser / visual checks:

- Finish the first minute by using the scope for pure water and brine; confirm that the vessels alone do not reveal the answer.
- Send O₂ to the compound route once, read the explanation, tow it back, and deliver it as an element.
- Compare pure O₂ with air: clearly distinguish atom labels and molecular identities while both are colourless bulk samples.
- Inspect every required sample. Check bent water geometry, linear CO₂ connectivity, O–O pairing, repeated Fe lattice, dispersed ions, and separate sand / oil regions.
- Ensure the legend and model-scale caption remain legible without hover, including at a common classroom resolution and with muted sound.
- Check that no pre-decision wagon label, scope subtitle, glow, colour key or accessibility label leaks a category / correct route. An atom legend is evidence, not a category answer.
- Check that an inspected or paused wagon does not hide the switches; Hebrew names and chemical formulas stay readable in RTL layout.
- Record actual automated and browser results in `docs/QA.md`; this document is an audit plan until those tests are run. Do not report these planned checks as passed evidence.

## Limits of this slice

The models deliberately omit electron structure, isotope mixtures, transient ion association, exact particle concentrations, real atmospheric proportions, oil chemistry, crystallographic detail, and changes of state. Samples are sealed, already specified and nonreacting. The player classifies and dispatches material; the railway does not perform reactions or purification. These limits keep the central distinction testable without turning a stylised scope into a claim of a literal microscope image.
