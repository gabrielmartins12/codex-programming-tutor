# Visual lessons connected to programming work

## Scope and intake

Reuse the conversation's language, learning preference, topic, and familiarity. Infer the topic from the feature being developed when clear. Ask only for missing information that changes the lesson. Default to a focused explanation of one mechanism; honor a requested depth or screen count. Depth and prior knowledge are separate.

Keep the active project as the point of reference. Put lesson artifacts in its existing documentation area, or `learning/<topic>/` when it has none; announce the path. For standalone learning, use a visible working folder. Never write generated lessons, captures, dependencies, or reports into this skill's directory. Do not change the product's UI or add runtime dependencies to the application merely to teach a concept.

Let `$VISUAL` be the absolute path to this skill's `visual/` folder, and `$WORK` the lesson's working folder. The bundled resources retain their original Portuguese filenames and prose; translate the delivered lesson to the user's language.

## Prepare a faithful explanation

Read the bundled references for the relevant stage:

- Before planning: `visual/references/00-experiencia-do-aluno.md`, `01-didatica.md`, and `10-arco-da-aula.md`.
- Before writing: `visual/references/11-escrita.md` and `03-roteiro-de-cenas.md`.
- When sourcing facts or UI: `visual/references/02-fontes-e-interfaces.md`.
- Before implementation: `visual/references/04-direcao-visual.md`, `05-motion.md`, `06-receitas-motion.md`, and `07-runtime-html.md`; inspect `visual/examples/mecanismo.html` for the API. Use `visual/examples/exemplar-dns/` for a longer worked example.
- Before delivery: `visual/references/08-captura-e-revisao.md`, `09-criterios-e-falhas.md`, and `12-qualidade-e-portoes.md`.

For a short project explanation, scale the brief and storyboard to the mechanism; do not require a long course or a fixed number of screens. Use the bundled brief and roteiro templates when the lesson warrants them. Preserve the following evidence regardless of length:

1. An observable outcome and the prerequisite concepts.
2. One concrete input, its execution path, and a verified result.
3. A progression from problem to visual model, mechanism, worked example, variation, optional practice, and return to code. Several movements may share a screen, but each step has one central idea.
4. A mapping between visible entities and actual files, functions, or variables. A diagram may simplify the system, but label assumptions where they matter.

Verify outputs by running the relevant project code when possible. Use authoritative documentation for external technical facts. Label simulations and illustrative data; never display an invented terminal result as an actual execution.

## Build with the included runtime

Copy `visual/templates/` to `$WORK/source/templates/`. Start `$WORK/source/lesson.html` from `visual/examples/mecanismo.html`, adjusting its relative asset paths from `../templates/` to `templates/`. Use the existing player rather than writing another navigation system. Keep scripts in order: `motion.js`, `kit.js`, `player.js`, lesson code.

Use short explanations beside diagrams, code excerpts, or verified UI simulations. Introduce terms before using them. Connect code highlights to the visual step: for example, focus a conditional, show its input, then show the chosen branch and resulting state. Keep the code excerpt small and identify its source path. Clearly label a UI mock as a simulation.

Navigation is learner controlled: Continuar, Voltar, and replay, with keyboard support. Finish each animated step in a stable state; never force automatic progression. Keep practice optional with an explicit skip route when the selected kit quiz otherwise requires an answer. Feedback must explain how the chosen input led to the result; allow another attempt.

### Motion that teaches

Use persistent names, colors with consistent meaning, and a recognizable object or focus across steps. Connect the explanation to the exact element moving or changing. Animate the mechanism: a value crossing a function boundary, a queue changing order, a branch selected, or a component updating. Distinguish logical relationships from physical transport.

Borrow these craft principles from `motion-designer`: plan explanation and image together, establish the concrete situation before a reveal, keep a single reading path, finish outgoing labels before inserting replacements in the same space, and inspect intermediate frames as well as endpoints. For software, favor code, state tables, and faithful UI over unrelated physical metaphors.

Use calm motion and one major change at a time unless simultaneity is essential to the mechanism. Keep numbers and captions synchronized with the same computed state as the drawing. Render as a pure function of slide, step, local time, and inputs so arbitrary seeks reproduce the scene. Respect reduced motion with an equivalent static sequence. Keep enough time and stable endpoints to read; do not borrow social-video retention tricks, continuous camera movement, or forced pacing.

No narration, music, MP4 production, paid APIs, 3D engine, or additional skill is required. PDF or video export is available through the bundled tools only when requested. Never inherit model-switching instructions, platform-specific shell commands, or questionnaires from video workflows.

## Verify and deliver

Use Node.js, Playwright, Sharp, and an available Chromium. Reuse an existing tooling installation via `LESSON_NODE_MODULES`, or install tooling in a separate working directory. Verify the available browser; `--channel chrome` is only for installed Chrome. Without that flag, tools use Playwright Chromium.

```bash
node "$VISUAL/scripts/check_env.mjs"
node "$VISUAL/scripts/pack.mjs" "$WORK/source/lesson.html" --out "$WORK/out/lesson.html"
node "$VISUAL/scripts/capture.mjs" "$WORK/out/lesson.html" --out "$WORK/qa/keyframes" --mode keyframes --viewports 1440x900,390x844
node "$VISUAL/scripts/storyboard.mjs" "$WORK/qa/keyframes/manifest.json"
node "$VISUAL/scripts/capture.mjs" "$WORK/out/lesson.html" --out "$WORK/qa/motion" --mode motion --fps 30
node "$VISUAL/scripts/contact_sheet.mjs" "$WORK/qa/motion/manifest.json" --stride 3
node "$VISUAL/scripts/audit.mjs" "$WORK/out/lesson.html" --capture "$WORK/qa/motion/manifest.json" --out "$WORK/qa/audit.json"
```

Inspect the rendered storyboard on desktop and phone, intermediate animation frames, and feedback for both correct and incorrect attempts. Check navigation, replay, reduced motion, offline loading, and the mechanism's outputs. Add lesson-specific behavioral checks for the taught rules; the bundled reference tests validate the runtime, not the correctness of new lesson content. Fix issues and repeat affected checks. Do not claim visual inspection from successful command output alone.

If tooling prevents inspection, describe the exact limitation and label the artifact as not fully verified; still provide an accessible static explanation of the mechanism. Do not silently downgrade a requested animated lesson to prose.

Deliver a clickable path to the packed HTML, one line on navigation, the corresponding code locations, and any material verification limits. Open the lesson when supported and authorized. Include requested code changes and their verification in the same delivery. Keep reports and captures in the working folder, separate from the final HTML.
