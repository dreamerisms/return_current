# Example Workflows

Tested and tuned for Return Current. Drop these `.json` files into the app via **Import workflow (PNG / JSON)** — they also open cleanly in ComfyUI itself.

The four image workflows share the same surrealist botanical default prompt (each rendering its own model name as a glass emblem), and the Wan 2.2 video workflow's default prompt is built to animate their outputs — an end-to-end demo chain out of the box.

---

### Ideogram 4 — Text-to-Image

The most feature-rich workflow in the set. Leverages the IdeogramStudio node for structured prompt control.

- JSON-formatted prompt with style, composition, and scene description fields
- Aspect ratio grid (8 presets) with resolution override
- Quality presets: 🐇 Turbo (12 steps) · 🦅 Default (20) · 🐢 Quality (28)
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

### Wan 2.2 — Image-to-Video

Two-stage HIGH/LOW I2V pipeline tuned for speed via Lightning LoRAs. The default prompt is designed to animate outputs from the other example workflows — generate a botanical, feed it straight in.

- Dual Insight Q8 GGUF models (HIGH + LOW stages) with split sampling (steps 0–3 HIGH, 3–end LOW)
- Lightning 4-step LoRAs pre-loaded and enabled on both stages (strength 1.0)
- 720×1280 @ 121 frames, h264 output
- RIFE interpolation with in-app on/off toggle
- Upscale pass via 4x-ClearRealityV1
- Load image input with camera/library picker in the app
- Power Lora Loader on both stages with trigger keyword tracking

**Required downloads:**

| File | Goes in |
|------|---------|
| `Wan2_2-I2V-A14B-HIGH_Insight-Q8_0.gguf` | `models/unet/` |
| `Wan2_2-I2V-A14B-LOW_Insight-Q8_0.gguf` | `models/unet/` |
| `Wan2.2-Lightning_I2V-A14B-4steps-lora_HIGH_fp16.safetensors` | `models/loras/` |
| `Wan2.2-Lightning_I2V-A14B-4steps-lora_LOW_fp16.safetensors` | `models/loras/` |
| `umt5_xxl_fp8_e4m3fn_scaled.safetensors` | `models/clip/` |
| `wan_2.1_vae.safetensors` | `models/vae/` |
| `4x-ClearRealityV1.pth` | `models/upscale_models/` |
| `rife47.pth` | auto-downloaded by RIFE VFI node |

Custom nodes required: [ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF), [VHS](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite), [Frame Interpolation (RIFE)](https://github.com/Fannovel16/ComfyUI-Frame-Interpolation), [rgthree-comfy](https://github.com/rgthree/rgthree-comfy)

---

All workflows automatically get a virtual Power Lora Loader if one isn't already present — you can add LoRAs to any workflow regardless. Unrecognized custom nodes fall into the collapsible **Advanced** section with full parameter access.
