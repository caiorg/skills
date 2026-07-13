---
name: print-art-prompt
description: Guided interview that produces a print-ready image-generation prompt for playmats, mousepads, and posters.
disable-model-invocation: true
---

Produce **one copy-ready image-generation prompt, always in English**, for artwork that will be physically printed. The interview happens in the user's language; only the final prompt is English.

The prompt is built from six **dimensions**:

| Dimension | Default when delegated |
|---|---|
| **Subject** | — user must confirm |
| **Format** (playmat / mousepad / poster) | — user must confirm |
| **Target model** | Generic (structured, negative block included) |
| **Art style** | Epic fantasy illustration, painterly realism, AAA TCG quality |
| **Palette & lighting** | Rich fantasy palette, cinematic contrast, volumetric lighting |
| **Composition emphasis** | The chosen format's defaults in [`FORMATS.md`](FORMATS.md) |

## Steps

### 1. Triage

Parse the invocation and label each dimension **resolved** (stated or clearly implied) or **open**. A vague gesture ("something with dragons, maybe a mat?") counts as open. Done when all six dimensions carry a label.

### 2. Interview

Interview the user about the open dimensions, one question at a time, each with your recommended answer, waiting for the reply before the next. The user may **delegate** at any point ("you decide", "whatever works"): fill every remaining open dimension with its default and move on. Subject and Format are exempt from delegation — when either is vague, put your best reading to the user and get an explicit yes; a wrong guess on these invalidates the whole prompt. Done when every dimension is resolved or delegated, with Subject and Format user-confirmed.

### 3. Load references

Read the chosen format's section in [`FORMATS.md`](FORMATS.md) and the target model's section in [`MODELS.md`](MODELS.md). When the model has no section, follow **Model not listed** at the end of `MODELS.md`. Done when you hold the format's production specs + composition rules and the model's output adaptation.

### 4. Generate

Fill the skeleton below with the resolved dimensions, apply the model adaptation from `MODELS.md`, and output the prompt in a single code block, followed by a one-line recap of the chosen dimensions (in the user's language) so the user can request tweaks. Done when every skeleton section applicable to the target model is filled, the aspect ratio and resolution match the format, and no placeholder remains.

## Prompt skeleton

```
{Subject — 1–3 vivid sentences}

Ultra-detailed {art style} illustration for a premium {format}, cinematic composition, designed specifically for a {dimensions} print format, high-resolution artwork, {orientation} layout, no UI elements, no text, no logos, no borders, seamless full-art composition.

Composition optimized for {format} use:
{composition rules — FORMATS.md}

Art style:
{art style keywords}

Rendering quality:
extremely sharp details, professional illustration, 300 DPI print quality, ultra high resolution, highly detailed brushwork, intricate textures, volumetric lighting, realistic materials, depth haze, strong silhouette readability.

Production specifications:
{production specs — FORMATS.md}

Color and lighting:
{palette & lighting keywords}

Negative prompts:
{only when MODELS.md says the model supports it}
```

Baseline negative list (adapt per `MODELS.md`): text, watermark, frame, UI, symbols, labels, borders, cropped face, cut-off character, low resolution, blurry details, distorted anatomy, oversaturated colors, empty background, flat lighting, simplistic rendering, duplicate subjects, noisy image, artifacts.
