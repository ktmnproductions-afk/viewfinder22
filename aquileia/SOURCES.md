# Aquileia — source, geometry and accuracy notes

## What this version actually renders

The main view is a live Three.js 3D scene. Its terrain, road surfaces, individual building meshes, forum colonnades, river-port warehouse, ships, amphitheatre, circus, Christian basilica, Late Antique wall segments, smoke/fire and present-day buildings are generated as 3D geometry in the browser. The five-stage timeline changes those objects in place; it does not use a slideshow as the scene.

This is a **procedural reconstruction based on a published archaeological plan**, not an excavation-grade digital twin. It is a first-party model authored for this page, not the original editable model from the Foundation's Antica Aquileia 3D project.

## Primary archaeological sources

- **Fondazione Aquileia — Aquileia 3D**: https://www.fondazioneaquileia.it/en/aquileia-3d  
  The Foundation describes ten films created with archaeologists and 60 virtual reconstructions covering the forum, river port, markets, houses, necropolis, amphitheatre, Republican walls, civilian basilica and circus. The original project informs site selection and architectural interpretation; its original scene meshes were not imported.
- **Fondazione Aquileia — Aquileia: A Border City** (PDF): https://www.fondazioneaquileia.it/files/allegati/aquileia_a_border_city_eng.pdf  
  Page 5 includes a citywide plan gathering archaeological structures and infrastructure discovered to date, credited to C. Tiussi based on L. Bertacchi, *Nuova pianta archeologica di Aquileia*, Udine, 2003. The 3D scene's simplified road grid, broad urban outline and landmark arrangement were transcribed from this plan as a spatial scaffold.
- **IKON — Ancient Aquileia 3D**: https://www.ikon.it/en/projects/ancient-aquileia-3d  
  Project producer's overview.
- **UNESCO World Heritage — Archaeological Area and the Patriarchal Basilica of Aquileia**: https://whc.unesco.org/en/list/825/
- **Fondazione Aquileia — Roman Forum**: https://www.fondazioneaquileia.it/en/must-see/roman-forum  
  The square's published dimensions are about 141 × 55 metres.
- **Fondazione Aquileia — River Port**: https://www.fondazioneaquileia.it/en/must-see/river-port  
  The Foundation describes a port-side structure over 300 metres long and an ancient waterway nearly 50 metres wide in this area.
- **Fondazione Aquileia — Basilica**: https://www.fondazioneaquileia.it/en/must-see/basilica
- **Fondazione Aquileia — Fondo Pasqualis markets**: https://www.fondazioneaquileia.it/en/must-see/fondo-pasqualis-markets
- **Fondazione Aquileia — Domus of Titus Macro**: https://www.fondazioneaquileia.it/en/must-see/titus-macers-house

## What is evidence-based and what is interpretive

- **Published-plan scaffold:** the rough orthogonal street network, approximate city extent and relative arrangement of major civic and entertainment complexes follow the published archaeological plan. The plan combines discoveries made over multiple excavation periods; it is not one complete preserved Roman city surface. The 3D scene's road grid is a simplified, rotated alignment—not a pixel-traced digitization—and its broad urban outline remains interpretive.
- **Landmark locations:** the forum, river port, basilica, Titus Macro house and market complex use mapped geographic reference points and a shared local projection anchored on the forum (approximately 10 m per scene unit). The 3D city grid is rotated to its schematic archaeological street axis. Amphitheatre and circus placement remain plan-derived approximations. The whole city is not a georeferenced, parcel-by-parcel archaeological survey.
- **Measured dimensions:** the forum model uses its published 141 × 55 m overall dimensions as a scale reference. The river-port warehouse is shown as a long narrow structure based on the published length description. Its precise shape and placement in the 3D scene remain simplified.
- **Representative structures:** houses, roofs, courtyards, forum columns, warehouses, amphitheatre seating, circus track, basilica elevations and defensive-wall modules are newly generated procedural meshes. They show the type and broad scale of structures; they are not claimed to reproduce every excavated footprint or the original project's proprietary models.
- **452 CE:** a subset of buildings darkens and collapses while fire/smoke particles appear. This is a visual interpretation of the documented sack, not a verified building-by-building fire map.
- **Present day:** modern houses, a basilica tower, fields and archaeological traces are contextual scene geometry, not a surveyed digital twin of modern Aquileia.
- **Old city boundaries and ancient river alignment:** outlines are interpretive aids, not surveyed cadastral or hydrological boundaries.
- **Phase-specific visibility:** the timeline controls which structures are rendered, not only their height. Early-colony buildings, developed Roman housing, Late Antique walls, fire effects and modern/archaeological traces are assigned to the relevant eras rather than leaving flattened building footprints visible in unrelated periods.

## Rendering and map stack

- Three.js generates the interactive 3D terrain and architectural geometry in the browser. The terrain's field texture and roof-tile texture are generated procedurally.
- Leaflet displays a separate real map view. Satellite tiles are served by Esri World Imagery; street-map tiles use OpenStreetMap. Attribution appears in the interface.
- The site loads external browser libraries and map tiles from their public CDNs/services, so an internet connection is required.
- The 3D model is orbitable, zoomable and has a landmark-focused camera. The era slider animates actual scene objects between historical states.

## Remaining work for archaeological-grade accuracy

1. Obtain/relicense original model geometry from Fondazione Aquileia/IKON, or digitize surveyed excavation plans and elevations into meshes.
2. Register the plan against the modern coordinate system and georeference individual monuments, street alignments, river courses and excavated structures.
3. Replace representative house blocks with phase-specific meshes based on excavated house plans and documented architectural reconstructions.
4. Have an archaeologist review building phases, wall segments and the visual treatment of the 452 CE destruction.

Until those steps are done, this is a deliberately labelled procedural visualization, not an archaeological authority.
