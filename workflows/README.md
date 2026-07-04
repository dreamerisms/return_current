# Example Workflows

Tested and tuned for Return Current. Drop these `.json` files into the app via **Import workflow (PNG / JSON)**.

---

### Ideogram 4 — Text-to-Image

The most feature-rich workflow in the set. Leverages the IdeogramStudio node for structured prompt control.

- JSON-formatted prompt with style, composition, and scene description fields
- Aspect ratio grid (8 presets) with resolution override
- Quality presets: 🐇 Turbo (8 steps) · 🦅 Default (20) · 🐢 Quality (35)
- Color palette picker — define up to 12 hex colors that influence the output
- Width/height fine-tuning below aspect ratio
- Power Lora Loader with trigger keyword tracking
- Text → JSON and Image → JSON prompt generation via Tools pane (requires LM Studio nodes)

### Krea 2 Turbo — Text-to-Image

Fast, clean T2I workflow built around the new Krea 2 model.

- UNET model dropdown (subfolder organized)
- DPRandomGenerator prompt input with `{ x | y | z }` random substitution syntax
- ResolutionSelector with aspect ratio + megapixel control
- KSampler with full parameter access (seed, steps, cfg, sampler, scheduler, denoise)
- Power Lora Loader with trigger keyword tracking

### Anima — Text-to-Image

SDXL-architecture workflow using UNETLoader.

- UNET model dropdown
- Prompt and negative prompt
- KSampler parameters
- Power Lora Loader with trigger keyword tracking

### SDXL — Text-to-Image

Standard SDXL checkpoint workflow. The baseline.

- Checkpoint model dropdown (subfolder organized)
- Prompt and negative prompt
- KSampler parameters (seed, steps, cfg, sampler, scheduler, denoise)
- Width/height controls
- Power Lora Loader with trigger keyword tracking

---

All workflows automatically get a virtual Power Lora Loader if one isn't already present — you can add LoRAs to any workflow regardless. Unrecognized custom nodes fall into the collapsible **Advanced** section with full parameter access.
