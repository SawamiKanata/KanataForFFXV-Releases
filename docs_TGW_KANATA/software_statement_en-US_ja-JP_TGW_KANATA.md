# KanataForFFXV — Introduction, User Guide, and Terms

[English](#english) · [日本語](#japanese)

<a id="english"></a>

# English

This document introduces the team, the software's purpose, supported resources, basic operations, disclaimers, prohibited activities, and contact information. The software is still in development. Some resources support only structural inspection or preview, and some edits have not been fully tested in the game. Being able to save, being able to build, and having verified in-game results are separate stages.

## 1. Team and Main Contributors

### 1.1 The Kanata Team

The Kanata team was founded by **Sawami Kanata**, a player from Russia who enjoys FINAL FANTASY VII, FINAL FANTASY XIII, and Wuthering Waves. Her interest in Wuthering Waves led her to study Unreal Engine and gradually inspired her to create game editing tools.

Over the following six months of learning and exploration, inspiration from Unreal Engine led her to invite friends to develop editors for FINAL FANTASY XIII and FINAL FANTASY XV. **Everscape**, from Finland, and **Odddice**, from Japan, joined the team, working with Kanata on **TGWForFFXIII** and **KanataForFFXV**, respectively.

Alongside these editors, Kanata is developing an independent engine, provisionally named **Resentia Axiom**. Drawing on features of Unreal Engine and the FINAL FANTASY XV engine, the project explores her own tools and approach to game development. She may also use this engine to create an independent game in the future.

### 1.2 Main Members and Contributions

| Member | Role and contribution |
| --- | --- |
| **Sawami Kanata** | Founder from Russia; leads the team and collaborates on both TGWForFFXIII and KanataForFFXV. |
| **Everscape** | Member from Finland; develops the FINAL FANTASY XIII editor **TGWForFFXIII** in collaboration with Kanata. |
| **Odddice** | Member from Japan; develops the FINAL FANTASY XV editor **KanataForFFXV** in collaboration with Kanata. |

Team email: **sawamikanatarip@gmail.com**.

**Public activity and identity verification**

Everscape's public role is limited to publishing Mods on **Nexus Mods**. Odddice is active only on **X**. Neither member proactively contacts other people to ask questions. If you encounter an account or contact impersonating a member, please contact the team at **sawamikanatarip@gmail.com** to verify their identity.

### 1.3 Relationship with Rights Holders

This is a tool developed by a player team. It is not a SQUARE ENIX product or an official support channel. The FINAL FANTASY names, trademarks, game programs, and related assets belong to their respective rights holders. The ability to read a resource does not mean that the team can grant permission to use, copy, or distribute it.

Third-party components and assets remain subject to their own licenses and permissions. Please refer to the license and attribution notices included with the release.

### 1.4 Development Languages and Distribution

KanataForFFXV is developed primarily in **Python**, together with **C/C++**. It is publicly distributed as **closed-source software**; project source code is not provided.

## 2. Purpose and Usage Limitations

### 2.1 Purpose

KanataForFFXV supports local resource research, content inspection, and Mod creation within its supported scope for FINAL FANTASY XV. Its functions include browsing archives, inspecting resources and dependencies, editing materials, models, levels, and supported configuration, blueprint, and text resources, previewing HUD/UI, and building supported native edits into packages loaded through this software.

The availability of this tool does not authorize unrestricted modification, commercial use, or distribution of game assets. Users must consider their game version, applicable software licenses, and asset permissions. For the game itself, consult the agreement for your region and version, such as the [FINAL FANTASY XV WINDOWS EDITION software license agreement (Japanese)](https://www.jp.square-enix.com/ff15/PC/product-eula/jp/). The team cannot replace or amend that agreement through this document.

### 2.2 System and Resource Requirements

1. The current implementation targets **Windows desktop systems**. Other operating systems and console versions are outside the confirmed support scope.
2. Most editing and building operations require readable local original game resources, a valid index, and complete dependencies. A project or Mod package may not contain everything needed to use it independently of the original game.
3. The retail game and Platinum Demo (**PD**) are separate resource sources. Select the correct source using Resource Source at the top right. Support for some PD resources does not imply that all Demo gameplay, weather, lighting, or assets can be transferred to the retail game.
4. Tests in the development environment do not establish compatibility with every storefront version, update, DLC, graphics card, or driver. Missing resources, source changes, unknown formats, and dependency conflicts may prevent opening or building content.
5. The game installation is used as an original resource source. Save edits outside that installation. Some standalone exporters require `TGW` or `KANATA` in the output filename; retain their default naming.
6. The public package includes its runtime. Users do not need to install Python or compilation tools separately. Keep the release files and their relative locations intact.
7. The public release provides **Japanese and English interfaces only**, with Japanese selected by default. Change the language on the initial directory selection screen or through **Project → Preferences…** in the top-left dropdown menu.

### 2.3 Source Restrictions and Current Feature Boundaries

Original game inputs undergo source and format checks. Content that does not satisfy the current rules may be refused for reading or building; follow the application's messages. Related prohibited activities are described in Section 6. A user-selected project or package output folder may be named Mods; that does not disable checks on original resource sources.

The current release does not provide arbitrary script execution, general-purpose Shader source compilation, full model topology editing, navigation baking for arbitrary new ground, or complete runtime reconstruction of every VFX resource.

### 2.4 Licensing and Distribution

The software is **publicly distributed under a proprietary, closed-source license**. Public availability does not make it open source or grant unrestricted permission to modify, translate, port, redistribute, or charge for it. See Section 6 for restrictions. Third-party components and imported assets retain their own licenses; the project's proprietary terms do not restrict rights already granted by those third-party licenses.

### 2.5 Connectivity and Regional Availability

Under the team's distribution scope and usage policy, the public release is available only in selected regions. Availability is determined by the application's verification results and messages. An internet connection must be maintained during use; offline operation is not provided.

The team values exchanges that respect creative work and attribution. Sharing in good faith does not create an obligation to continue accommodating the appropriation of others' work, denial of their contributions, or demands based on double standards.

If verification cannot be completed or regional requirements are not met, access may be paused or the application may close. Unsaved changes may be lost; save your project regularly.

Online verification does not require account registration and does not upload game files or project content through that process.

### 2.6 Known Issues

1. **HUD/UI:** Currently recommended for preview only. Editing is unstable and is not recommended at this time.
2. **Build, loading, and startup times:** Building Mods, loading resources, or starting the game may take some time. Please be patient and follow the displayed progress and messages.

## 3. Features, File Types, and Limitations

### 3.1 File Entry Points and Formats

Opening a resource in the resource browser means accessing it through the selected game directory, an archive, or the index. It does not mean that the main Open Project command accepts every extension. The project entry point accepts **`.kanataproject`** only; import read-only **`.kanata`** packages through Mod Manager.

Some game resources use logical references such as `.gmdl`, `.gmtl`, or `.tif`, while their actual payloads may be `.gmdl.gfxbin`, `.gmtl.gfxbin`, or BTEX. The actual payload format determines support; renaming an extension does not convert it. Files ending in `.exml`, `.ebex`, or `.prefab` may contain XMB2 binary data and must not simply be overwritten as plain text.

### 3.2 Supported Resource Scope

| Feature | File types and extensions | Supported operations | Main limitations |
| --- | --- | --- | --- |
| Complete project | `.kanataproject` | Open, continue editing, save, and save as; retain multiple levels and supported resource edits. | Not a directly deployable game package; source, dependency, and build checks still apply. |
| Build and Mod management | `.kanata` | Build a read-only package; import, enable, order, inspect, and launch the game through Kanata. | Not an editable project backup. Renaming cannot convert it to a project. Older packages depend on compatibility support. |
| Game archive browsing | `.earc` | Inspect virtual directories and supported payloads and references. | Unknown archive versions, some patch layers, and special entries may be unsupported. Listing an archive does not imply all members are editable. |
| Models and geometry | `.gmdl.gfxbin` and associated `.gpubin`; logical `.gmdl` | Preview, select, move, rotate, delete, or restore parts; edit and apply materials. Supported changes can participate in native builds. | GPU data requires its model description. No general OBJ/FBX import/export or vertex/edge/face topology editing. Part edits do not necessarily update collision. |
| Standalone model document | `.kmodel` | Save and reopen models with supported part and material edits. | Not a native game model. Rebuilding some material previews still requires original dependencies. |
| Materials | `.gmtl.gfxbin`; logical `.gmtl` | Edit supported constants and texture references; load material/Shader templates; apply to models or levels; export native-format copies. | Not all material families or visual effects are implemented. |
| Shader inspection | `.sb` containing recognized DXBC data | Inspect chunks, signatures, and strings; change existing paired templates in the material window. | No general HLSL/GLSL source compilation, arbitrary bytecode rewriting, or execution of every native program. |
| Ordinary textures and images | Decodable `.btex`, `.dds`, `.png`, `.jpg`, `.jpeg`, `.tga`, `.bmp`, `.gif`, `.tif`, `.tiff` | Inspect channels and pixels; edit an independent RGBA copy; change exposure, dimensions, rotation, or orientation; export `.png`. | Decoder and payload limits apply. No BTEX re-encoding of ordinary pixel edits, complete array/mip editing, or automatic game replacement from PNG exports. |
| HDR textures | Supported BC6H BTEX, usually `.btex` | Inspect surfaces, mip levels, and display exposure in a dedicated window. | Not arbitrary HDR editing or native write-back. |
| Levels, prefabs, configurations, and lights | Supported XMB2 in `.exml`, `.ebex`, `.prefab`; plain `.xml` | Assemble level references; transform, delete, copy, and add supported instances; inspect and edit confirmed fields, including XML views. | One extension can contain different object types. Missing dependencies, unknown types, and runtime events limit editing and display. |
| Actor blueprint placement | Recognized actor definitions, including `.exml` XMB2 resources | Place supported enemies or NPCs; set transforms, uniform body scale, and supported activation ranges using original actor configurations. | A browser category, not a separate `.blueprint` format. Not all actors, story bosses, or online variants can run autonomously. |
| Character AI blueprints | Recognized `.exml`, `.ebex`; `.kai` documents | Inspect state machines and behavior trees; edit supported nested values, existing transitions, and branches; save and export copies. | Some strings, IDs, compiled expressions, and cross-layer targets remain read-only or unresolved. No complete AI execution. |
| Interaction/sequence blueprints | XMB2 `.exml`, `.ebex`, `.prefab` with explicit ports and connections | Inspect nodes, edit supported values, connect existing ports, disconnect links, and save scene copies. | Not a general visual scripting compiler. Some directions and port compatibility remain unverified. |
| Animation state graphs | `.anmgph`; `.kanimgraph` documents | Edit supported entries, existing transitions, transition values, and some local blend inputs; save and export copies. | Conditions, external keys, unknown nodes, and full pose blending remain limited. |
| Actor/environment animation preview | `.ani`, `.amdl`, and referenced dependencies | Play with matching models and skeletons; pause, loop, step, seek, change speed, and preview root motion. | No full animation authoring or keyframe editing. Resource, channel, assembly, and performance limitations remain. |
| Script-related configuration | `.xml` and supported `.exml`, `.ebex`, `.prefab` views | Edit supported configuration fields and some sequence/blueprint data; save native configurations or export XML text. | No general Lua, Python, JavaScript, or other scripting-language authoring, compilation, or execution. Text visibility does not imply executability. |
| VFX | `.vfx` and original dependencies | Inspect supported static appearances, texture slices, or implemented materials; place in maps, transform, save, and build instances. | No complete reconstruction of all particles, emitters, attachments, or procedural materials. PD VFX conversion and loose-file VFX game placement are unsupported. |
| UI/HUD | Supported `.swfb`; existing `.kui` document format; `.listb` atlas indexes | Preview supported UI layouts and related atlases. | Currently recommended for preview only. Editing is unstable and is not recommended, including using edits in the game. The complete UI runtime remains unfinished. |
| Fonts | `.fntbin`; `.kfont` documents | Inspect glyphs and atlases; edit supported glyph values, spacing, and character mapping; save documents and copies. | Not a complete font generator. Auxiliary fonts, out-of-bounds source glyphs, and runtime bindings have separate limits. |
| Messages and text | `.msgbin` | Find IDs, edit ordinary text and supported control units, export copies, and manually bind ordinary text to UI slots. | Full control semantics and automatic message/font/style bindings remain incomplete. |
| Audio inspection | `.wav`, `.sab`, `.mab` | Inspect parameters, library headers, and recognized embedded WAVs; audition supported PCM WAV. | No decoding of every compressed format, complete sound editing, or audio-library recompilation. |
| Navigation, video, and other text | `.nav`, `.bk2`, `.ini`, `.txt`, `.autoext`, and others | Inspect supported headers, binary data, references, or text. | Navigation inspection is not navigation baking. `.bk2` playback is unavailable; unknown formats are not promised to be editable. |

`.kmap`, `.kresource`, and similar containers are internal or historical formats, not current public whole-project save entry points. `.kanataasset` is a self-contained external asset package used by some resource workflows, distinct from a `.kanata` game package. Support for reading it does not imply a general external-package import command in the main project menu.

## 4. Operations

Because Kanata used Unreal Engine before developing this editor, its controls and interface layout follow the design she was familiar with and are, overall, almost identical to those of Unreal Engine.

### 4.1 General Settings and First Use

1. Extract the complete public release and run **`KanataForFFXV_Public.exe`**. After startup verification, the application opens initial setup or the editor. No separate Python or compiler installation is required.
2. Select the game directory when prompted. To change it, use **Project → Game Directory and Local Index…**, or the resource browser's local resource/index settings. Wait for indexing before selecting resources.
3. For PD resources, select PD at the top-right Resource Source control and provide the corresponding directory. Confirm the source when editing retail content.
4. The outline is on the left, viewport in the center, resource browser below, and Object Properties/Viewport Settings on the right. Single-click a resource for information; double-click to open its window.
5. In Viewport Settings, adjust navigation speed, rotation sensitivity, time, day/night playback, emission preview, sky/exposure, background, grid, perspective, LOD, VFX, HDR reflections, and map texture resolution. Scroll inside the sidebar for additional controls.
6. Right-drag to look around, middle-drag to pan, and use the wheel to zoom. Press **F** or use focus/frame tools for the selection. Use Restart Viewport if the displayed state becomes stale.
7. Use **Project → Reset Workspace Layout** to restore the interface layout.
8. Change Japanese/English on the initial directory screen or through **Project → Preferences…** in the top-left dropdown.

Viewport exposure, emission multipliers, resolution, and display switches are viewing settings. They do not automatically edit game weather, native material constants, or runtime resources. Edit the corresponding supported resource and pass build checks to affect the game.

### 4.2 Saving, Building, and Loading Mods

1. Open an editable project with **Project → Open .kanataproject…** or **Ctrl+O**.
2. Click **Save** or press **Ctrl+S** to save the whole project. Choose a `.kanataproject` path on first save; use **Save Kanata Project As…** for a separate copy.
3. Saving collects levels and resource windows integrated into the workspace. Changes retained after closing a resource window still need a disk save. Ordinary RGBA texture edits must be exported as PNG as described in 4.4; do not assume they are native texture replacements.
4. Click **Build** to create `.kanata`. Native write-back, resource identity, and dependencies are checked. Resolve any blocking errors and build again.
5. Open **Mod Manager**, import the package, set enabled status and order, review conflicts, and use its game launch command.
6. **Project → Test Entire Project (Temporary Build and Launch Game)** can test current edits. Save the project and back up game saves before this action.

After you edit and build a Mod with Kanata, the game will display Kanata theme colors and branding when launched. See Section 6 for the requirement to retain them.

**Saving a project and building a package are separate operations.** Building does not mark an unsaved project as saved. A read-only `.kanata` does not replace an editable `.kanataproject` backup. Rebuild from the project after relevant editor updates; existing packages do not update automatically.

Launch the game through Kanata to load enabled Mods. The public edition prepares archives before launch, backs up and temporarily replaces the corresponding game files, and restores originals after the game exits. Game files stay fixed during play. If the session is interrupted, exit FFXV and start Kanata again to recover originals. Mods can affect game behavior and saves; this recovery does not replace save backups.

### 4.3 Materials

1. Double-click `.gmtl.gfxbin`, or select a model part and open its material editor.
2. Search parameter or constant-block names in the parameter tab. Check the original type and component count. Click Apply or press Enter after entering values; separate vector components as instructed.
3. For supported materials, edit confirmed emission, color, metalness, roughness, or transparency values and compare day/night previews.
4. In texture slots, replace a supported reference with another readable original texture. Slots sharing one resource ID may change together; check the scope.
5. Apply to matching materials in the model or level using the relevant command. Level-wide application may affect several models.
6. Use undo, redo, or restore; save the whole project or export a `.gmtl.gfxbin` copy where available.

Viewport emission multipliers affect preview only; native emission constants are material edits. Replacing a slot reference does not convert arbitrary PNGs to BTEX. Unimplemented material programs may show only partial effects.

### 4.4 Textures

1. Double-click a decodable ordinary texture or image.
2. Inspect RGBA, RGB, R, G, B, or A channels; click the image to read pixel coordinates and color.
3. Enter coordinates and four integers from 0 to 255, then apply the pixel edit. Exposure, resize, 90-degree rotation, and horizontal flip are also available.
4. Review using undo/redo and export a **PNG copy** outside the game directory, retaining required filename markers.
5. HDR resources use a dedicated surface/mip/exposure window rather than this ordinary RGBA workflow.

The output is a PNG copy. BTEX re-encoding is not implemented, so this operation alone does not create a Mod replacing the game's compressed texture.

### 4.5 Shader Inspection and Templates

1. Open `.sb` to inspect recognized DXBC structures.
2. To change an existing material's Shader setup, open its material window and choose the material/Shader template command.
3. Select a supported metal/emission, glass, or water template, or provide a readable original GMTL logical URI and load it.
4. Templates replace the paired Shader reference, constant layout/values, and texture bindings. Adjust and apply them through the material workflow, then save or export a supported copy.
5. Undo or restore the original material if needed.

This primarily edits parameters and templates paired with existing Shaders. It is not a general Shader source editor/compiler; structural inspection does not mean every native program can be executed or recompiled.

### 4.6 Lights

1. Open a level and use Add to create a point, spot, or flickering light at the current viewport center.
2. Select it in the viewport or outline; its marker can be used to select and move it.
3. Edit supported position, rotation, color, intensity, exposure, range, radius, and active hours in Object Properties. Spotlights also expose cone/edge values; flickering lights use supported native noise parameters.
4. Apply changes and compare time settings. Copy, delete, undo, or redo as needed.
5. Save `.kanataproject`, build `.kanata`, and verify actual lighting and activation in the game.

Supported existing light fields can also be inspected through XML/EXML configuration editing. The editor does not fully simulate dynamic shadows, native flicker, all weather lights, GI, automatic exposure, or event switches. Setting a native shadow field does not mean an identical shadow is previewed.

### 4.7 Models

1. Double-click `.gmdl.gfxbin`, a model in the level, or its outline entry. Associated GPU data and available dependencies are loaded.
2. Click a surface to select a part; use box selection or Shift for multiple parts.
3. Move parts, rotate around their centers, delete/restore them, or edit selected materials.
4. Apply to same-source models in the level, checking the potentially shared scope.
5. Save the whole project, or save a standalone `.kmodel` through its dedicated entry point. Supported level-held model edits can participate in native builds.

Part edits change the model internally; instance transforms change one placement. Vertex/edge/face topology editing is unavailable. Deleting a part does not automatically remove its collision or game logic.

### 4.8 Levels

1. Open a recognized level configuration and wait for its references and models to assemble. The outline retains hierarchy and diagnostics for missing or excluded sources.
2. Select, move, rotate, or scale with tools or property fields; apply numeric transforms where required.
3. Shift-click adds selections; box selection can include occluded projected objects. Check the outline before batch edits.
4. In the level viewport, **Ctrl+D** duplicates and **Delete** removes the selection. Use toolbar undo/redo or supported **Ctrl+Z/Ctrl+Y** shortcuts.
5. Drag supported models from the resource browser onto viewport surfaces. Right-click or double-click add workflows may place them at the world origin; check coordinates.
6. To start with an empty target, right-click a level configuration and use the new-level-from-scratch command. This retains the game replacement target and clears original content, with the supported undo operation.
7. For supported static objects, configure collision generation, surface-fitting mode, and surface/footstep type, then inspect the output.
8. Save, build, and test visibility, collision, streaming, and runtime behavior in the game.

Force display affects some parsed enable/hidden flags; it does not execute story events or supply missing resources. New ground can have a model and collision yet lack navigation. Arbitrary new, moved, or scaled ground cannot currently have navigation rebaked.

### 4.9 Actor Blueprints and Character AI

1. Open a level and select the actor blueprint resource tab. Wait for initial organization, or run its organization command when needed.
2. Drag a recognized enemy/NPC onto a surface; right-click Add to Viewport or double-click places it at the world origin.
3. Set position, rotation, and uniform scale. A body-scale value of `0.5` means half size, `2` means double; apply or press Enter. Restore returns to `1`.
4. For supported enemies, set the proximity combat-AI activation radius. The red circle is the added activation area, not the actor's full sight or attack range.
5. For AI edits, open a recognized Character AI resource, select a state-machine or behavior-tree scope, and edit writable values, existing transitions, or supported branches. Save the project or supported copy.
6. Build and test spawning, facing, animation, targeting, movement, and combat. A reference pose in the editor does not demonstrate running AI.

Actors retain their original appearance, AI, animation, and physics definitions. Player, sequence-controlled, unresolved, and some story/online variants may not work as autonomous actors. Spawning does not guarantee combat; display does not guarantee movement on ground without navigation. Scale read-back does not verify all in-game collision and animation behavior.

### 4.10 Blueprints

1. Open the level's event list and double-click a supported interaction or volume to open its blueprint.
2. Select a node, inspect its source object, and apply values in supported writable fields using the original type.
3. Connect recognized existing ports with New Connection, or select and disconnect an existing link.
4. Drag nodes to arrange the inspection layout, middle-drag to pan, and use the selection-location command to return to a node.
5. Undo within the window. Save a scene copy to retain a standalone `.exml`; that copy is not automatically a verified game Mod.
6. If a map-preview command is available, note that it may affect all instances of that scene resource. Review before saving the whole project.

Character AI has its own editor. Double-click `.anmgph` for animation state graphs, then use state/node modes to edit supported existing transitions, entry keys, or local inputs and save/export.

This is not an unrestricted node-authoring and game-logic compiler. Some interaction directions and port compatibility are unverified; AI/animation conditions and runtime targets may remain read-only. Connections on a graph do not guarantee execution in the game.

### 4.11 Script-Related XML/EXML Configuration

1. Right-click a configuration and choose XML/EXML editing, or use the equivalent resource-inspection entry point.
2. XMB2 is expanded into XML retaining types and original field identities. Edit only supported strings, booleans, integers, floats, vectors, and fields; retain names, offsets, types, and hashes.
3. Import XML/EXML text through the dedicated command, which validates it. Renaming unrelated files does not convert them.
4. Write Back to Project retains edits in the workspace; Save Entire Project or **Ctrl+S** saves to disk. Export XML produces a text copy.
5. Build `.kanata` through the window or main toolbar. Resolve errors for unsupported native types or resource references.

This edits configuration and supported script-related data, not a general scripting language. There is no general script authoring, debugging, compiling, or execution environment. Importing XML does not execute commands; unknown native types are preserved or refused rather than guessed.

### 4.12 VFX

1. Double-click `.vfx` to open its static appearance window. The normal entry point shows supported visual content rather than substituting a node graph for the effect.
2. For supported resources, focus and adjust display exposure to inspect texture slices or implemented static materials. If no appearance is available, follow the diagnostic instead of assuming successful reconstruction.
3. With a map open, use Add to Map or drag a supported retail-archive VFX into the viewport.
4. Edit the instance's position, rotation, and scale; copy, delete, undo/redo, and save with the complete project.
5. Enable VFX in Viewport Settings to display supported original scene effects. It is off by default for new maps.
6. Build and verify placement and triggering in the game. The current build workflow adds repeated triggering after level load for newly placed VFX; preview exposure does not rewrite original effect assets.

Static slices are not complete spatial snapshots of original game frames. Full particles, emitter distributions, cinematic attachments, procedural materials, and sustained visibility require separate verification. Research-level node/curve parsing does not imply unrestricted ordinary-window node or particle editing. PD VFX and arbitrary loose VFX placement are unsupported.

### 4.13 UI, Fonts, Messages, and Animation Preview

1. **UI/HUD:** Open supported `.swfb` to preview readable layouts and content. Treat this as a preview feature for now: editing is unstable, and modifying HUD/UI or using those edits in the game is not recommended.
2. **Fonts:** Open `.fntbin`, select characters/glyphs/atlases, and edit supported parameters or mappings. Save `.kfont` or a native-format copy. Editable fonts do not automatically restore unresolved runtime bindings.
3. **Messages:** Open `.msgbin`, find IDs, edit ordinary text or supported control units, and save/export. Do not guess unknown control semantics.
4. **Animation preview:** Open `.ani`/`.amdl`, match a model and skeleton, select a clip, and use playback, pause, loop, speed, seek, and root-motion controls. State-graph editing is a separate advanced entry point.

Standalone documents do not replace whole-project backups. Editor display, saving, and structural checks alone do not prove correct in-game UI, text, font, or animation behavior.

### 4.14 Pedestrian Areas, Routes, and Warp Points

1. Add a pedestrian area/route and left-click points in order. Areas need at least three points, routes at least two. **Enter** finishes, **Backspace** removes one point, **Esc** cancels; the current limit is 256 points.
2. Set population, types, and applicable speed, width, side-by-side, and two-way options in properties. Green walls show editing boundaries and are not imported as that wall appearance.
3. Select numbered points to move them, or redraw. Correct self-intersections, density, and capacity issues following the messages.
4. Add a Noctis warp point and set position, direction, original preset, hanging/landing behavior, and supported distances. The blue sphere/arrow are editing markers; original auto-facing can affect the final direction.
5. Save, build, and test spawning, walking, avoidance, and warping.

Population limits describe input/export scope, not in-game performance guarantees. Ground without navigation may allow spawning but not walking. The editor does not bake arbitrary new navigation or automatically route around every obstacle.

## 5. Disclaimers

### 5.1 Development Status and Visual Differences

The software is provided in its current development state and supported scope. The team does not guarantee that all resources are readable, all edits build, all Mods are compatible, or editor output exactly matches the game.

Software/game updates, driver changes, missing dependencies, and Mod combinations may alter behavior. Historical samples and local performance measurements apply only to their test conditions and are not guarantees for other environments.

### 5.2 Data and Game Risks

Editing, building, or loading modifications may cause errors, visual defects, resource conflicts, crashes, or changes to save data. Back up projects and game saves, and test in a recoverable environment. Source checks, hashes, read-back validation, and backup/recovery measures reduce particular risks but cannot eliminate all risks or replace backups.

### 5.3 Third-Party Content and Rights

Users must have appropriate grounds to import, modify, display, and distribute content. The team cannot grant permissions on behalf of other rights holders, and a successful build does not establish that a package may be publicly distributed or commercially used.

Resource paths, names, trademarks, and assets identify the content being handled; they do not imply authorization, endorsement, or compatibility certification by their rights holders.

### 5.4 Support, Liability, and Applicable Rules

The team may adjust features and support scope as development progresses. Repair deadlines, ongoing services, and compatibility periods are not guaranteed unless expressly promised.

To the extent permitted by applicable law, the software is provided as is, without guarantees beyond express written commitments. Responsibility for losses is determined by the actual facts, applicable law, and valid agreements. This document does not exclude or limit liability that cannot lawfully be excluded or limited, or deprive users of statutory rights by treating use alone as agreement.

## 6. Prohibited Activities

Without explicit permission from the KanataForFFXV development and maintenance team, modifying this tool and publicly distributing the modified version is prohibited. Public availability does not grant an open-source license or unrestricted modification/redistribution rights. The following three restrictions are emphasized.

### 6.1 Modification, Translation, Porting, and Paid Redistribution

1. **Unauthorized translation or localization is prohibited.** Without team permission, do not translate/localize this tool into other languages or publish/distribute such versions, including interface changes, replacement language resources, or language patches.
2. **Unauthorized rewriting in C#/.NET for compatibility or integration with Flagrum is prohibited.** Do not modify, port, or redistribute this tool to create such a compatible or integrated derivative.
3. **Paid redistribution of this tool or Mods made with it is prohibited.** This includes paid downloads, paid bundles, member-only paid access, and disguised charges such as mandatory donations.

To help users in your region with translation, contact **sawamikanatarip@gmail.com** first to discuss localization and distribution. An application or discussion is not authorization; wait for the team's explicit approval.

If you prefer Flagrum, you may contact its developers about implementing `.kanata` import compatibility on their own tool's side, rather than modifying, porting, or redistributing KanataForFFXV. **When implementing compatibility and importing or displaying these Mods, clearly label their resource information “Made with Kanata.”** This statement does not imply existing cooperation, authorization, or a compatibility guarantee between the teams.

This section concerns modification and distribution of this tool. Independent implementation of third-party software is not treated as modification of this tool. Rights granted under third-party component licenses remain governed by those licenses.

**Retention of Kanata theme colors and branding:** After a Mod is edited and built with Kanata, the game will display Kanata theme colors and branding when launched. These identifying changes must be retained and must not be deleted, hidden, replaced, or removed. This requirement also applies if the Mod is later migrated for use with Flagrum: retain the theme colors and branding, together with the “Made with Kanata” resource attribution described above.

### 6.2 Other Prohibited Activities

1. **Infringing others' rights:** do not obtain, copy, sell, or distribute game programs, assets, personal information, or other content without the required rights.
2. **Malicious use:** do not embed malware, credential/data theft, or functions intended to damage devices or files in projects, Mods, packages, or purported repair tools.
3. **Impersonation:** do not impersonate the team, its members, or game officials to publish versions, charge fees, solicit funds, or request account information. Do not pass a modified release off as the team's original.
4. **False attribution or authorization claims:** do not fabricate contributors, remove notices required by law/license, or claim nonexistent authorization or security guarantees.
5. **Harming other players or services:** do not use the software for unauthorized online cheating, attacks, service disruption, or infringement of other players' rights.
6. **Treating technical capability as a distribution license:** export support, self-contained packages, or not needing original Demo data does not grant permission to publicly distribute assets.

## 7. Contact

Official team email: **sawamikanatarip@gmail.com**.

---

<a id="japanese"></a>

# 日本語

本書では、チーム、ソフトウェアの目的、対応リソース、基本操作、免責事項、禁止事項、お問い合わせ先を紹介します。本ソフトウェアは開発中です。構造の確認やプレビューのみに対応するリソースもあり、一部の編集結果はゲーム内で十分に検証されていません。「保存できること」「ビルドできること」「ゲーム内で動作を確認できていること」は、それぞれ異なる段階です。

## 1. チームと主な貢献者

### 1.1 Kanata チーム

Kanata チームは、ロシア出身の **Sawami Kanata** によって結成されました。彼女は FINAL FANTASY VII、FINAL FANTASY XIII、そして『鳴潮』を好んでプレイしています。『鳴潮』への関心をきっかけに Unreal Engine を学び始め、次第にゲーム編集ツールの制作を考えるようになりました。

その後、約半年間の学習と試行錯誤を通じて Unreal Engine から着想を得た彼女は、友人たちと FINAL FANTASY XIII および FINAL FANTASY XV のエディターを制作することを決めました。フィンランド出身の **Everscape** と日本出身の **Odddice** が加わり、それぞれ Kanata と協力して **TGWForFFXIII** と **KanataForFFXV** を開発しています。

この2つのエディターに加え、Kanata は **Resentia Axiom** という仮称の独自エンジンも開発しています。Unreal Engine と FINAL FANTASY XV のエンジンの特性を参考に、自身のゲーム開発ツールと制作手法を模索するプロジェクトです。将来は、このエンジンでインディーゲームを制作する可能性もあります。

### 1.2 主なメンバーと担当

| メンバー | 役割・貢献 |
| --- | --- |
| **Sawami Kanata** | ロシア出身の創設者。チームを率い、TGWForFFXIII と KanataForFFXV の両方に協力しています。 |
| **Everscape** | フィンランド出身。Kanata の協力のもと、FINAL FANTASY XIII 用エディター **TGWForFFXIII** の制作を担当しています。 |
| **Odddice** | 日本出身。Kanata の協力のもと、FINAL FANTASY XV 用エディター **KanataForFFXV** の制作を担当しています。 |

チーム連絡先：**sawamikanatarip@gmail.com**。

**公開活動と本人確認について**

Everscape の公開活動上の担当は **Nexus Mods** での Mod 公開のみで、Odddice は **X** のみで活動しています。両名が自ら他の方へ連絡して質問することはありません。メンバーを名乗る不審なアカウントや連絡に遭遇した場合は、チーム公式メール **sawamikanatarip@gmail.com** までご確認ください。

### 1.3 権利者との関係

本ソフトウェアはプレイヤーチームが開発するツールであり、SQUARE ENIX の公式製品や公式サポート窓口ではありません。FINAL FANTASY シリーズの名称、商標、ゲームプログラムおよび関連素材の権利は、それぞれの権利者に帰属します。リソースを読み取れることは、チームがその使用・複製・配布の許諾をユーザーに与えられることを意味しません。

第三者製コンポーネントや素材には、それぞれのライセンスおよび許諾条件が適用されます。配布版に同梱されたライセンス・クレジット表記をご確認ください。

### 1.4 開発言語と公開形態

KanataForFFXV は主に **Python** と **C／C++** を用いて開発されています。ソフトウェアは**クローズドソースとして一般公開**され、プロジェクトのソースコードは提供されません。

## 2. 目的と利用上の制限

### 2.1 ソフトウェアの目的

KanataForFFXV は、FINAL FANTASY XV のローカルリソースの研究、内容の確認、対応範囲内での Mod 制作を目的としています。アーカイブの閲覧、リソースと依存関係の確認、マテリアル・モデル・レベルおよび対応する設定・ブループリント・テキストの編集、HUD・UI のプレビュー、ネイティブ形式で出力可能な変更を本ソフトウェア経由で読み込むパッケージへのビルドを行えます。

本ツールの提供は、ゲーム素材の無制限な改変、商用利用、再配布を許可するものではありません。ゲームのバージョン、適用される利用許諾、素材について取得した許可に応じて利用範囲を判断してください。ゲーム自体については、[FINAL FANTASY XV WINDOWS EDITION ソフトウェア使用許諾契約](https://www.jp.square-enix.com/ff15/PC/product-eula/jp/)など、対象の地域・製品に適用される契約をご確認ください。本書によってチームがその契約を置き換えたり変更したりすることはできません。

### 2.2 動作環境とリソースの条件

1. 現在の実装は **Windows デスクトップ環境**を対象としています。他の OS や家庭用ゲーム機版は、確認済みの対応範囲に含まれません。
2. 多くの編集・ビルド操作には、読み取り可能なローカルのオリジナルゲームリソース、有効なインデックス、必要な依存リソースが必要です。プロジェクトや Mod パッケージに、元のゲームなしで利用するためのすべてのリソースが含まれるとは限りません。
3. 製品版と Platinum Demo（**PD**）は別のリソースソースです。右上のリソースソース選択で区別してください。一部の PD リソースに対応していても、Demo のすべてのゲームプレイ、天候、照明、素材を製品版に移植できるわけではありません。
4. 開発環境での検証は、すべての販売ストア版、更新、DLC、グラフィックスカード、ドライバーでの互換性を保証しません。リソース不足、ソースの変更、未知の形式、依存関係の競合によって、読み込みやビルドが拒否される場合があります。
5. ゲームのインストール先はオリジナルリソースの読み取り元として使用します。編集結果はゲームフォルダー外に保存してください。一部の単独エクスポーターはファイル名に `TGW` または `KANATA` を要求します。既定の命名を維持してください。
6. 公開パッケージには実行環境が含まれるため、Python やコンパイルツールを別途インストールする必要はありません。配布ファイルと相対的な配置を維持してください。
7. 公開版の表示言語は**日本語と英語のみ**で、既定は日本語です。初回のフォルダー選択画面、または左上の「プロジェクト」ドロップダウンメニューの「環境設定…」で変更できます。

### 2.3 ソース制限と現在の機能範囲

オリジナルゲームの入力にはソースおよび形式の検証が行われます。現在の規則に適合しない内容は読み取りやビルドが拒否される場合があるため、アプリ内の案内に従ってください。関連する禁止事項は第6章に記載しています。ユーザーが選ぶプロジェクトやパッケージの出力フォルダーを Mods と命名しても、元リソースのソース検証は無効になりません。

任意のスクリプト実行、汎用 Shader ソースコンパイル、完全なモデルのトポロジー編集、任意の新規地面に対するナビゲーションのベイク、すべての VFX の完全なランタイム再現は、現在提供していません。

### 2.4 ライセンスと配布

本ソフトウェアは**独自ライセンスのクローズドソース製品として一般公開**されます。ダウンロード可能であることは、オープンソース化や、自由な改変・翻訳・移植・再配布・有料配布の許可を意味しません。制限については第6章をご確認ください。第三者製コンポーネントや取り込んだ素材には各自のライセンスが適用され、本プロジェクトの独自ライセンスによって第三者のライセンスがすでに認めている権利が制限されることはありません。

### 2.5 インターネット接続と利用可能地域

チームの配布範囲および利用方針により、公開版は一部の地域にのみ提供されます。利用の可否は、ソフトウェアの検証結果と表示される案内に従います。使用中はインターネット接続を維持する必要があり、オフライン利用には対応していません。

チームは、創作とクレジットを尊重する交流を大切にしています。善意による公開は、成果の無断流用、他者の貢献の否定、二重基準による要求に対して、便宜を提供し続ける義務を意味しません。

検証を完了できない場合や利用地域の条件を満たさない場合、アクセスが一時停止されたり、ソフトウェアが終了したりすることがあります。未保存の変更が失われる可能性があるため、こまめに保存してください。

オンライン検証にアカウント登録は不要で、この処理を通じてゲームファイルやプロジェクト内容がアップロードされることはありません。

### 2.6 既知の問題

1. **HUD・UI：** 現時点ではプレビューのみを推奨します。編集は不安定なため、変更は当面推奨しません。
2. **ビルド・読み込み・起動時間：** Mod のビルド、リソースの読み込み、ゲームの起動に時間がかかる場合があります。画面の進捗や案内を確認し、しばらくお待ちください。

## 3. 機能・ファイル形式・制限

### 3.1 ファイルを開く入口と形式

「リソースブラウザーで開く」とは、選択したゲームフォルダー、アーカイブ、インデックスから対応ウィンドウにアクセスすることです。メインのプロジェクトを開く操作が、すべての拡張子に対応しているわけではありません。プロジェクトの入口は **`.kanataproject`** のみを受け付けます。読み取り専用の **`.kanata`** は Mod 管理からインポートしてください。

ゲーム内の論理参照名が `.gmdl`、`.gmtl`、`.tif` でも、実際のデータが `.gmdl.gfxbin`、`.gmtl.gfxbin`、BTEX である場合があります。対応可否は実際の形式によります。拡張子の変更だけでは変換されません。`.exml`、`.ebex`、`.prefab` に XMB2 バイナリが格納されている場合もあるため、通常のテキストとして上書きしないでください。

### 3.2 対応リソースの範囲

| 機能 | 形式・拡張子 | 対応する操作 | 主な制限 |
| --- | --- | --- | --- |
| プロジェクト全体 | `.kanataproject` | 開く、編集の継続、保存、名前を付けて保存。複数レベルと対応リソースの変更を保持。 | ゲームで直接使用するパッケージではありません。ソース、依存関係、ビルドの検証が必要です。 |
| ビルド・Mod 管理 | `.kanata` | 読み取り専用パッケージのビルド、インポート、有効化、順序変更、内容確認、Kanata 経由のゲーム起動。 | 編集用プロジェクトの代わりにはなりません。拡張子変更による相互変換はできず、旧パッケージの読み取りは互換対応の範囲によります。 |
| アーカイブ閲覧 | `.earc` | 仮想フォルダー、対応データ、参照の確認。 | 未知のバージョン、一部の差分・特殊エントリーは未対応です。一覧を表示できても全内容を編集できるとは限りません。 |
| モデル・ジオメトリ | `.gmdl.gfxbin`、対応する `.gpubin`。論理参照 `.gmdl` | プレビュー、パーツ選択・移動・回転・削除・復元、マテリアル編集と適用。対応する変更はネイティブビルドに使用可能。 | GPU データには対応するモデル記述が必要です。汎用 OBJ/FBX 入出力、頂点・辺・面のトポロジー編集はありません。パーツ変更でコリジョンが同期されるとは限りません。 |
| 単独モデル文書 | `.kmodel` | モデルと対応するパーツ・マテリアル変更の保存と再読み込み。 | ゲームのネイティブモデル形式ではありません。一部のマテリアルプレビューの再構築には元の依存リソースが必要です。 |
| マテリアル | `.gmtl.gfxbin`。論理参照 `.gmtl` | 対応定数やテクスチャ参照の変更、マテリアル／Shader テンプレートの読み込み、モデル・レベルへの適用、元形式のコピー出力。 | すべてのマテリアル系統や表示効果を実装しているわけではありません。 |
| Shader の確認 | 認識可能な DXBC を含む `.sb` | チャンク、シグネチャ、文字列の確認。マテリアル画面で既存の対応テンプレートを変更。 | 汎用 HLSL/GLSL ソースコンパイル、任意のバイトコード書き換え、全ネイティブプログラム実行は未対応です。 |
| 通常テクスチャ・画像 | デコード可能な `.btex`、`.dds`、`.png`、`.jpg`、`.jpeg`、`.tga`、`.bmp`、`.gif`、`.tif`、`.tiff` | チャンネル・ピクセル確認、独立した RGBA コピーの編集、露出・寸法・回転・反転、PNG 出力。 | 実際のデータとデコーダーの制限が適用されます。通常のピクセル編集結果の BTEX 再エンコード、配列・全 mip 編集、PNG からの自動ゲーム置換は未対応です。 |
| HDR テクスチャ | 対応 BC6H BTEX。通常 `.btex` | 専用画面でサーフェス、mip、表示露出を確認。 | 任意の HDR 編集やネイティブ書き戻しではありません。 |
| レベル・プレハブ・設定・ライト | 対応 XMB2 を含む `.exml`、`.ebex`、`.prefab`、通常の `.xml` | 参照を含むレベル構築、インスタンス変換・削除・複製・追加、確認済みフィールドや XML 表示の編集。 | 同一拡張子でも内容が異なります。不足依存、未知型、実行時イベントによって制限されます。 |
| キャラクターブループリント配置 | `.exml` などから認識されたキャラクター定義 | 対応する敵・NPC の配置、変換、等比体型、対応する起動範囲の設定。元のキャラクター設定を使用。 | ブラウザー上の分類であり、独立した `.blueprint` 形式ではありません。全キャラクター、ストーリーボス、オンライン派生版の自律動作は保証しません。 |
| Character AI ブループリント | 認識された `.exml`、`.ebex`、文書 `.kai` | ステートマシン・ビヘイビアツリーの確認、対応する入れ子パラメーター、既存遷移・分岐の変更、保存とコピー出力。 | 一部の文字列・ID・コンパイル済み式・階層間参照は読み取り専用または未解決です。完全な AI 実行は行いません。 |
| インタラクション・シーケンスのブループリント | 明示的なポート・接続を持つ `.exml`、`.ebex`、`.prefab` | ノード確認、対応パラメーター編集、既存ポートの接続・切断、シーンコピー保存。 | 汎用ビジュアルスクリプトコンパイラーではありません。一部の方向やポート互換性は未検証です。 |
| アニメーション状態グラフ | `.anmgph`、文書 `.kanimgraph` | 対応する入口キー、既存遷移、遷移値、一部ローカルブレンド入力の編集、保存とコピー出力。 | 条件、外部キー、未知ノード、完全なポーズブレンドには制限があります。 |
| キャラクター・環境アニメーション | `.ani`、`.amdl` と参照依存 | 対応モデル・スケルトンでの再生、一時停止、ループ、コマ送り、シーク、速度・ルートモーション確認。 | 完全なアニメーション制作・キーフレーム編集ではありません。リソース、チャンネル、組み立て、性能に未対応部分があります。 |
| スクリプト関連設定 | `.xml`、対応する `.exml`、`.ebex`、`.prefab` 表示 | 対応設定や一部シーケンス・ブループリントデータの編集、ネイティブ設定保存、XML テキスト出力。 | Lua、Python、JavaScript などの汎用スクリプト言語の編集・コンパイル・実行環境はありません。表示可能なテキストが実行可能とは限りません。 |
| VFX | `.vfx` と元の依存リソース | 対応する静的外観、テクスチャ断片、実装済みマテリアルの確認。マップへの配置、変換、保存、ビルド。 | 全パーティクル・エミッター・取り付け先・手続き型マテリアルの完全再現ではありません。PD VFX の変換や単独ファイル VFX のゲーム配置は未対応です。 |
| UI・HUD | 対応 `.swfb`、既存文書形式 `.kui`、アトラス索引 `.listb` | 対応する UI レイアウトや関連アトラスのプレビュー。 | 現時点ではプレビューのみを推奨します。編集は不安定なため、変更やゲームへの適用は推奨しません。完全な UI ランタイムは未完成です。 |
| フォント | `.fntbin`、文書 `.kfont` | 字形・アトラス確認、対応字形パラメーター・字間・文字マッピング編集、文書とコピーの保存。 | 完全なフォント生成ツールではありません。補助フォント、範囲外字形、実行時割り当てには個別制限があります。 |
| メッセージ・テキスト | `.msgbin` | ID 検索、通常テキストと対応制御単位の編集、コピー出力、UI スロットへの手動テキスト割り当て。 | 全制御意味や自動メッセージ・フォント・スタイル割り当ては未復元です。 |
| 音声の確認 | `.wav`、`.sab`、`.mab` | パラメーター、ライブラリヘッダー、認識できる埋め込み WAV の確認と、対応 PCM WAV の試聴。 | 全圧縮形式のデコード、完全な音声編集・ライブラリ再コンパイルは未対応です。 |
| ナビゲーション・動画・その他テキスト | `.nav`、`.bk2`、`.ini`、`.txt`、`.autoext` など | 対応範囲内のヘッダー、バイナリ、参照、テキストの確認。 | ナビゲーション確認はベイクではありません。`.bk2` は再生できず、未知形式の編集は保証しません。 |

`.kmap`、`.kresource` などは内部用または旧形式のコンテナーであり、現在のプロジェクト全体の公開保存形式ではありません。`.kanataasset` は一部のリソース操作で使う自己完結型の外部素材パッケージで、`.kanata` ゲームパッケージとは異なります。読み取り機能があっても、メインのプロジェクトメニューに汎用外部パッケージインポートがあることを意味しません。

## 4. 操作方法

Kanata は本エディターの開発前に Unreal Engine を使用していたため、操作方法と画面レイアウトにも使い慣れた設計を取り入れています。全体として、Unreal Engine とほぼ同じ操作方法・レイアウトになっています。

### 4.1 全体設定と初回利用

1. 公開パッケージ全体を展開し、**`KanataForFFXV_Public.exe`** を実行します。起動時の検証後に初回設定またはエディターが表示されます。Python やコンパイルツールの別途導入は不要です。
2. 案内に従ってゲームフォルダーを選びます。変更時は「プロジェクト → ゲームフォルダーとローカルインデックス…」、またはリソース欄のローカルリソース・インデックス設定を開きます。インデックス作成完了後にリソースを選択してください。
3. PD リソースを使う場合は、右上のリソースソースを PD に切り替え、対応するフォルダーを指定します。製品版を編集する際は現在のソースを確認してください。
4. 左側にアウトライン、中央にビューポート、下部にリソースブラウザー、右側に「オブジェクトのプロパティ」と「ビューポート設定」があります。クリックで説明を確認し、ダブルクリックで対応画面を開きます。
5. ビューポート設定では、移動速度、回転感度、時刻、昼夜再生、自己発光プレビュー、空と露出、背景、グリッド、透視、LOD、VFX、HDR 反射、マップテクスチャ解像度を変更します。右側の内容は内部スクロールで確認できます。
6. 右ドラッグで視点回転、中ドラッグで平行移動、ホイールでズームします。選択後に **F** またはフォーカス・範囲表示ツールを使います。表示が古い状態のままの場合は、上部のビューポート再起動を使用できます。
7. 配置を戻す場合は「プロジェクト → ワークスペースの配置をリセット」を使用します。
8. 日本語・英語の切り替えは、初回フォルダー選択画面、または左上の「プロジェクト」ドロップダウンの「環境設定…」から行います。

空の露出、プレビュー用発光倍率、表示解像度、表示切り替えは観察用設定です。ゲームの天候、ネイティブマテリアル定数、実行時リソースを自動的に変更するものではありません。ゲームに反映するには対応リソースを編集し、ビルド検証を通す必要があります。

### 4.2 保存・ビルド・Mod の読み込み

1. 「プロジェクト → .kanataproject を開く…」または **Ctrl+O** で編集用プロジェクトを開きます。
2. 「保存」または **Ctrl+S** で全体を保存します。初回は `.kanataproject` の保存先を指定し、別コピーには「Kanata プロジェクトに名前を付けて保存…」を使います。
3. 保存時にはワークスペースに統合されたレベルとリソース画面の内容を収集します。画面を閉じても保持されている変更は、ディスクへの保存が必要です。通常の RGBA テクスチャ編集は4.4の PNG 出力を行い、ネイティブテクスチャの変更になったと考えないでください。
4. 「ビルド」で `.kanata` を作成します。ネイティブ書き戻し、リソース同一性、依存関係の問題が出た場合は、原因を修正して再ビルドします。
5. 「Mod 管理」でパッケージをインポートし、有効状態と順序、競合を確認して、ゲーム起動操作を使用します。
6. 「プロジェクト → プロジェクト全体をテスト（一時ビルドしてゲームを起動）」も利用できます。実行前にプロジェクトを保存し、セーブデータをバックアップしてください。

Kanata で Mod を編集・ビルドした後にゲームを起動すると、Kanata のテーマカラーとロゴなどの識別表示が表示されます。保持に関する条件は第6章をご確認ください。

**プロジェクト保存とパッケージのビルドは別の操作です。** ビルドしても未保存のプロジェクトが保存済みになるわけではありません。読み取り専用 `.kanata` は編集用 `.kanataproject` のバックアップを代替しません。更新による修正を適用するには元のプロジェクトから再ビルドしてください。既存パッケージは自動更新されません。

有効な Mod を読み込むには Kanata 経由でゲームを起動してください。公開版では起動前にアーカイブを準備し、対応するゲームファイルをバックアップして一時的に置き換え、ゲーム終了後に元へ戻します。プレイ中はファイルを変更しません。処理が中断された場合は、FFXV を終了して Kanata を再起動すると復元します。Mod は動作やセーブデータに影響する場合があり、この復元はセーブデータのバックアップの代わりにはなりません。

### 4.3 マテリアル編集

1. `.gmtl.gfxbin` をダブルクリックするか、モデルのパーツを選んで対応するマテリアル編集を開きます。
2. パラメータータブで名前や定数ブロックを検索し、元の型と成分数を確認します。入力後に適用または Enter を使用し、ベクトルは案内どおりに区切ります。
3. 対応する自己発光、色、メタルネス、ラフネス、透明度などを変更し、昼夜プレビューで比較します。
4. テクスチャスロットでは、対応する参照を別の読み取り可能なオリジナルテクスチャに変更します。同じリソース ID を共用するスロットは同時に変わる場合があるため、範囲を確認してください。
5. モデルまたはレベル内の同名マテリアルに適用するコマンドを使用します。レベルへの適用は複数モデルに影響する場合があります。
6. 元に戻す・やり直し・復元を使って確認し、全体保存または対応画面の `.gmtl.gfxbin` コピー出力を行います。

ビューポートの発光倍率はプレビューのみで、元の発光定数がマテリアル変更に当たります。参照の変更で任意の PNG が BTEX に変換されるわけではありません。未実装のマテリアルは一部しか表示できない場合があります。

### 4.4 テクスチャ編集

1. デコード可能な通常テクスチャ・画像をダブルクリックします。
2. RGBA、RGB、R、G、B、A を切り替えて確認し、画像をクリックしてピクセル座標と色を読み取ります。
3. 座標と0～255の整数4成分を入力してピクセル変更を適用します。露出、リサイズ、90度回転、左右反転も使用できます。
4. 元に戻す・やり直しで確認し、必要な命名を維持してゲームフォルダー外へ **PNG コピー**を出力します。
5. HDR は専用のサーフェス・mip・露出画面を使用します。

出力は PNG コピーです。BTEX 再エンコードは未実装のため、この操作だけでゲームの圧縮テクスチャを置換する Mod にはなりません。

### 4.5 Shader の確認とテンプレート

1. `.sb` を開き、認識可能な DXBC 構造を確認します。
2. 既存マテリアルの Shader 構成を変えるには、マテリアル画面のテンプレート選択を開きます。
3. 対応する金属・自己発光、ガラス、水面テンプレート、または読み取り可能な元 GMTL の論理 URI を指定して読み込みます。
4. テンプレートは Shader 参照、定数レイアウトと値、テクスチャ割り当てを一式で変更します。マテリアル操作で調整・適用し、保存または対応コピーを出力します。
5. 必要に応じて元に戻すか、元のマテリアルを復元します。

主に既存 Shader に対応するパラメーターとテンプレートの調整です。汎用 Shader ソース編集・コンパイル機能ではなく、構造を確認できても全プログラムを実行・再コンパイルできるわけではありません。

### 4.6 ライト編集

1. レベルを開き、追加メニューからポイントライト、スポットライト、揺らぎのあるライトを選びます。現在のビューポート中心に配置されます。
2. ビューポートまたはアウトラインで選択し、編集マーカーを使って移動します。
3. プロパティで対応する位置、回転、色、強度、露出、範囲、半径、点灯時間を変更します。スポットライトには角度・境界の調整、揺らぎライトには対応する元のノイズ設定があります。
4. 適用して時刻を変え、必要に応じて複製、削除、元に戻す・やり直しを行います。
5. `.kanataproject` を保存し、`.kanata` をビルドしてゲーム内の照明と点灯条件を確認します。

既存ライトの対応フィールドは XML／EXML 編集でも確認できます。動的影、元の揺らぎ、全天候ライト、GI、自動露出、イベント切り替えを完全に再現しません。影の設定を変更できても同じ影がプレビューされるとは限りません。

### 4.7 モデル編集

1. `.gmdl.gfxbin`、レベル内モデル、対応アウトライン項目をダブルクリックします。対応 GPU データと利用可能な依存リソースが読み込まれます。
2. 表面をクリックしてパーツを選び、矩形選択や Shift で複数を選択します。
3. パーツ移動、中心を基準とする回転、削除・復元、マテリアル編集を行います。
4. レベル内の同一ソースモデルへ適用する際は、複数配置への影響範囲を確認してください。
5. 全体保存、または専用入口から `.kmodel` を保存します。レベルで保持する対応モデル変更はネイティブビルドに使用できます。

パーツ編集はモデル内部、インスタンス変換は特定の配置を変更します。頂点・辺・面の編集はなく、パーツ削除でコリジョンやゲームロジックが自動削除されるわけではありません。

### 4.8 レベル編集

1. 認識可能なレベル設定を開き、参照とモデルの構築を待ちます。不足・除外されたソースの診断もアウトラインに保持されます。
2. ツールまたは右側の数値で選択、移動、回転、拡縮を行い、必要に応じて変換を適用します。
3. Shift クリックで追加選択します。矩形選択は他の物体に隠れた投影範囲内の対象も含むため、一括編集前にアウトラインを確認してください。
4. レベルのビューポートで **Ctrl+D** は複製、**Delete** は削除です。ツールバーまたは対応する **Ctrl+Z／Ctrl+Y** で元に戻す・やり直しを行います。
5. リソースブラウザーから対応モデルを表面へドラッグします。右クリックやダブルクリックによる追加はワールド原点に配置される場合があるため、座標を確認してください。
6. 空の内容から作成する場合はレベル設定を右クリックし、ゼロから新規作成するコマンドを使用します。ゲーム内の置換対象を保って元内容を消去し、対応する取り消しが可能です。
7. 対応する静的物体では、コリジョン生成、表面に沿うモード、表面・足音の種類を設定し、結果を確認します。
8. 保存・ビルド後、ゲーム内で表示、コリジョン、ストリーミング、動作を確認します。

強制表示は解析済みの有効・非表示条件の一部に作用するだけで、ストーリー実行や不足リソースの補充はしません。モデルとコリジョンがある地面でもナビゲーションがない場合があります。任意の新設・移動・拡縮した地面の再ベイクは未対応です。

### 4.9 キャラクターブループリントと Character AI

1. レベルを開き、キャラクターブループリントのリソースタブを選びます。初回の整理を待つか、必要に応じて整理コマンドを実行します。
2. 認識された敵・NPC を表面へドラッグします。右クリックの追加やダブルクリックではワールド原点に配置されます。
3. 位置、回転、等比体型を設定します。倍率 `0.5` は半分、`2` は2倍です。適用または Enter で確定し、復元で `1` に戻します。
4. 対応する敵では、接近時の戦闘 AI 起動半径を設定します。赤い円は追加した起動範囲であり、元 AI の視界・攻撃範囲すべてを表しません。
5. AI を編集する場合は認識済み Character AI を開き、ステートマシンやビヘイビアツリーの範囲を選んで、書き込み可能な値・既存遷移・対応分岐を変更し、保存します。
6. ビルド後、ゲーム内で出現、向き、アニメーション、索敵、移動、戦闘を確認します。参照ポーズの表示は AI が実行された証拠ではありません。

元の外観・AI・アニメーション・物理定義を使用します。プレイヤー、シーケンス制御、依存不明、特定ストーリー・オンライン派生のキャラクターは自律配置できるとは限りません。出現しても戦闘や移動ができるとは限らず、体型の出力確認も全キャラクターのコリジョン・アニメーション検証を意味しません。

### 4.10 ブループリント編集

1. レベルのイベント一覧を開き、対応するインタラクションや範囲をダブルクリックします。
2. ノードと元オブジェクトを確認し、対応する書き込み可能フィールドを元の型に従って編集・適用します。
3. 新規接続では認識済みの既存ポートを選び、既存リンクは選択して切断します。
4. ノードをドラッグして表示配置を変更し、中ドラッグで移動、選択位置への移動コマンドで戻ります。
5. 画面内で元に戻す操作ができます。単独結果は `.exml` のシーンコピーとして保存しますが、それだけで検証済みゲーム Mod にはなりません。
6. マップで変更をプレビューできる場合、同じシーンリソースの全インスタンスに作用する可能性を確認してから全体保存してください。

Character AI は専用エディターを使用します。`.anmgph` では状態・ノードモードを使い、対応する既存遷移、入口キー、ローカル入力を変更して保存・出力します。

任意ノード作成や完全なゲームロジックコンパイル機能ではありません。一部の接続方向・ポート互換性は未検証で、AI・アニメーションの条件や実行時参照が読み取り専用の場合もあります。グラフの接続が実行を保証するわけではありません。

### 4.11 スクリプト関連の XML／EXML 設定

1. 設定ファイルを右クリックして XML／EXML 編集を選ぶか、リソース確認画面の同等の入口を使用します。
2. XMB2 は型と元フィールド識別情報を保持した XML に展開されます。対応文字列、真偽値、整数、浮動小数点、ベクトルなどのみを変更し、名前、offset、型、ハッシュを保持してください。
3. 専用インポートから XML／EXML テキストを読み込みます。検証が行われ、無関係なファイルを改名しても変換にはなりません。
4. プロジェクトへの書き戻しはワークスペースに変更を保持します。全体保存または **Ctrl+S** でディスクへ保存し、テキストコピーには XML 出力を使用します。
5. 画面またはメインツールバーから `.kanata` をビルドし、未対応型やリソース参照のエラーを修正します。

設定と対応するスクリプト関連データの編集であり、汎用スクリプトの作成・デバッグ・コンパイル・実行環境ではありません。XML の読み込みで命令は実行されず、未知の型は推測せず保持または拒否します。

### 4.12 VFX の編集と配置

1. `.vfx` をダブルクリックして静的外観画面を開きます。通常の入口は対応する外観を表示し、ノード図を効果の代わりに表示しません。
2. 対応リソースではフォーカスと表示露出を使い、テクスチャ断片や実装済みマテリアルを確認します。表示できない場合は診断を確認し、完全再現できたと判断しないでください。
3. マップを開いた状態でマップ追加を使用するか、対応する製品版アーカイブ内の VFX をドラッグします。
4. 位置、回転、拡縮を変更し、複製・削除・元に戻す・やり直しを使用して全体プロジェクトに保存します。
5. 元シーンの対応 VFX はビューポート設定で表示を有効にします。新規マップでは既定でオフです。
6. ビルドしてゲーム内の配置・起動を確認します。新規配置 VFX は現在の処理でレベル読み込み後の繰り返し起動を生成します。プレビュー露出は元の素材を書き換えません。

静的断片は元ゲームの1フレーム全体の空間形状ではありません。全パーティクル、エミッター分布、演出の取り付け先、手続き型マテリアル、継続表示は個別検証が必要です。研究段階のノード・曲線解析は、通常画面で任意のノードやパーティクルを編集できることを意味しません。PD VFX と任意の単独 VFX ファイルのゲーム配置は未対応です。

### 4.13 UI・フォント・メッセージ・アニメーション

1. **UI・HUD：** 対応 `.swfb` を開き、読み取り可能なレイアウトと内容をプレビューします。現時点ではプレビュー機能としてご利用ください。編集は不安定なため、HUD・UI の変更やゲームへの適用は推奨しません。
2. **フォント：** `.fntbin` から文字・字形・アトラスを選び、対応値やマッピングを変更し、`.kfont` または元形式コピーを保存します。未解決の実行時割り当てが自動復元されるわけではありません。
3. **メッセージ：** `.msgbin` の ID を検索し、通常文字や対応制御単位を変更して保存・出力します。未知の制御意味を推測しないでください。
4. **アニメーション：** `.ani`／`.amdl` でモデルとスケルトンを合わせ、再生、一時停止、ループ、速度、シーク、ルートモーションを確認します。状態グラフ編集は別の高度な入口です。

単独文書はプロジェクト全体のバックアップを代替しません。表示、保存、構造検証だけでは、ゲーム内 UI・文字・フォント・アニメーションの正しい動作は証明されません。

### 4.14 歩行者範囲・ルート・シフトポイント

1. 歩行者範囲またはルートを追加し、左クリックで順番に点を置きます。範囲は3点以上、ルートは2点以上です。**Enter** で確定、**Backspace** で1点戻す、**Esc** で中止します。現在の上限は256点です。
2. プロパティで人数、種類、対応する歩速、幅、並列人数、双方向移動を設定します。緑の壁は編集境界であり、その外観をゲームへ追加するものではありません。
3. 番号付きの点を選んで移動するか、描き直します。自己交差、密度、収容人数の問題は案内に従って修正してください。
4. ノクティスのシフトポイントでは位置、向き、元プリセット、ぶら下がり・着地、対応距離を設定します。青い球や矢印は編集マーカーで、元の自動方向調整が最終方向に影響する場合があります。
5. 保存・ビルド後、出現、歩行、回避、シフトをゲーム内で確認します。

人数上限は入力・出力の対応範囲であり、ゲーム性能の保証ではありません。ナビゲーションがない地面では出現しても歩けない場合があります。任意の新地面へのナビゲーション生成や、すべての障害物を自動回避するルート作成は行いません。

## 5. 免責事項

### 5.1 開発状況と表示の違い

本ソフトウェアは現在の開発状況と対応範囲で提供されます。全リソースの読み取り、全変更のビルド、すべての Mod の互換性、エディターとゲームの完全一致は保証しません。

ソフトウェアやゲームの更新、ドライバー、依存リソース不足、Mod の組み合わせによって動作が変わる場合があります。過去のサンプルやローカル性能値は、その検証条件の結果であり、他環境の安定性・性能を保証するものではありません。

### 5.2 データとゲームへの影響

編集、ビルド、変更の読み込みによって、エラー、表示不具合、リソース競合、クラッシュ、セーブデータの変化が発生する可能性があります。プロジェクトとセーブデータをバックアップし、復旧可能な環境で検証してください。ソース・ハッシュ・再読み込み検証やバックアップ・復元対策は、特定のリスクを低減するもので、すべてのリスクを除去したりバックアップを代替したりはできません。

### 5.3 第三者コンテンツと権利

インポート、編集、表示、配布する内容には、必要な使用根拠や許諾を確保してください。チームは他の権利者に代わって許可を与えることはできず、ビルド成功によって公開配布や商用利用の可否が確定するわけではありません。

リソースパス、元の名称、商標、素材の表示は処理対象を説明するためのもので、権利者による許諾、推奨、互換性認証を意味しません。

### 5.4 サポート・責任・適用規則

開発の進行に応じて機能やサポート範囲を変更する場合があります。明示的に約束した場合を除き、修正期限、継続的サービス、互換期間は保証されません。

適用法令で認められる範囲で現状のまま提供し、明示された書面上の約束を超える保証は行いません。損失に対する責任は、事実関係、適用法令、有効な合意に基づいて判断されます。本書は法令上免除・制限できない責任を排除せず、利用のみを同意とみなして法定の権利を奪うものではありません。

## 6. 禁止事項

KanataForFFXV の開発・保守チームの明確な許可なく、本ツールを改変して改変版を一般公開することを禁止します。公開提供は、オープンソースライセンスや自由な改変・再配布の許可を意味しません。特に次の3項目を禁止します。

### 6.1 改変・翻訳・移植・有料再配布

1. **無断の翻訳・ローカライズを禁止します。** チームの許可なく他言語への翻訳・ローカライズを行ったり、該当版を公開・配布したりしないでください。画面文言の変更、言語リソースの置換、言語パッチの公開も含みます。
2. **Flagrum との互換・統合を目的とする、本ソフトウェアの C#／.NET への無断書き換えを禁止します。** 本ツールの改変・移植・再配布によって、そのような互換版や統合版を作成しないでください。
3. **本ツール、または本ツールで制作した Mod の有料再配布を禁止します。** 有料ダウンロード、有料セット、有料会員限定アクセス、必須寄付などの実質的な課金も含みます。

お住まいの地域のユーザーに言語面の利便性を提供したい場合は、まず **sawamikanatarip@gmail.com** まで翻訳・ローカライズ・公開についてご相談ください。申請や相談のみでは許可になりません。チームの明確な承認をお待ちください。

Flagrum の使用を希望する場合は、その開発チームへ連絡し、KanataForFFXV を改変・移植・再配布するのではなく、相手側のツールで `.kanata` のインポート互換を実装する方法をご相談ください。**互換対応を実装し、該当 Mod を取り込み・表示する際は、その Mod のリソース説明に「Kanata で制作（Made with Kanata）」と明記してください。** この記載は、両チーム間の既存の協力関係、許諾、互換性保証を意味しません。

本節は本ツールの改変・配布に関するもので、第三者が自身のソフトウェアを独立して実装することを本ツールの改変と同一視するものではありません。第三者製コンポーネントのライセンスが認める権利には、そのライセンスが引き続き適用されます。

**Kanata のテーマカラーと識別表示の保持：** Kanata で Mod を編集・ビルドした後にゲームを起動すると、Kanata のテーマカラーとロゴなどの識別表示が表示されます。これらの特徴的な変更は保持する必要があり、削除、非表示化、置き換え、除去を禁止します。将来、その Mod を Flagrum で使用するために移行する場合も、テーマカラーと識別表示、および前述の「Kanata で制作（Made with Kanata）」というリソース説明の表記を保持してください。

### 6.2 その他の禁止事項

1. **他者の権利の侵害：** 必要な権利なく、ゲームプログラム、素材、個人情報、その他の内容を取得・複製・販売・配布しないでください。
2. **悪意ある利用：** プロジェクト、Mod、配布物、修復ツールを装うものに、マルウェア、認証情報・データ窃取、機器・ファイルへの意図的な損害を与える機能を含めないでください。
3. **なりすまし：** チーム、メンバー、ゲーム公式を装い、公開、課金、資金募集、アカウント情報の要求を行わないでください。改変版をチームの原版と偽らないでください。
4. **虚偽のクレジット・許諾表示：** 貢献者の捏造、法令・ライセンスで必要な表示の削除、存在しない許可や安全保証の主張を行わないでください。
5. **他のプレイヤーやサービスへの妨害：** 許可されていないオンライン不正行為、攻撃、サービス妨害、他プレイヤーの権利侵害に使用しないでください。
6. **技術的対応を素材配布許可とみなすこと：** 出力機能、自己完結パッケージ、元の Demo データが不要であることだけを理由に、素材の公開配布権を得たと主張しないでください。

## 7. お問い合わせ

チーム公式メール：**sawamikanatarip@gmail.com**。
