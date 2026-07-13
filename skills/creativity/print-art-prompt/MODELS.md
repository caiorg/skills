# Models — output adaptation

Reference for [`print-art-prompt`](SKILL.md), step 4. Read only the target model's section. Every variant keeps the skeleton's content; what changes is phrasing, negatives, and how aspect ratio is expressed.

## Generic (default — model unknown)

- Full skeleton as written, including the `Negative prompts:` section.
- Aspect ratio stated inside the production specs.

## Stable Diffusion / SDXL

- Skeleton sections flattened into comma-separated keyword phrases; keep section labels as plain-text headers for the user's readability.
- Split output into two labeled blocks: **Positive prompt** and **Negative prompt** (paste into separate fields).
- State the render resolution to set in the UI, plus the upscale needed to reach print resolution (SDXL natively renders near ~1 megapixel; e.g. playmat: render 1344×768, upscale 5–6× to 7200×4200).

## Flux

- Flowing natural-language prose; keyword lists merged into sentences.
- Standard pipelines take no negative prompt: convert each exclusion into a positive statement ("a clean seamless full-art composition, completely free of text, logos, watermarks or borders").
- State the render resolution + upscale note as in SD.

## Midjourney

- Single continuous prose line (no section headers, no line breaks).
- Append parameters at the end: `--ar {ratio}` (playmat `--ar 12:7`, XL desk mat `--ar 9:4`, poster `--ar 2:3`), `--no text, watermark, borders, frame, logo`, and `--stylize` only if the user asked for stronger stylization.
- Mention that upscale to print resolution happens after generation (external upscaler).

## DALL-E / GPT Image / Imagen

- Conversational descriptive prose, positive phrasing throughout; exclusions become affirmations of what the image *is* ("borderless edge-to-edge artwork with no text or logos anywhere").
- Express the format as a described canvas ("wide 12:7 landscape composition for a 24×14 inch playmat print").
- These models output fixed sizes; include the note that the result must be upscaled to the format's print resolution.

## Nano Banana (Gemini image)

- Rich narrative prose — describe the scene as a story, not keyword lists; this family rewards detailed natural-language description above all.
- No negative prompt field: convert exclusions into affirmations, as in Flux.
- State the aspect ratio explicitly in the prompt text ("landscape 12:7 aspect ratio") and mirror it in the API/App aspect-ratio setting when available.
- Ask which tier when unstated: **Nano Banana** outputs ~1024 px (needs heavy upscale, 6–7× for a playmat); **Nano Banana Pro** outputs up to 4K — generate at 4K and note the remaining upscale to the format's print resolution (e.g. playmat 7200×4200: ~2× from a 4K landscape output).
- Leverage its strong instruction-following for the composition rules: spell them out as plain sentences ("keep the outer edges darker and less detailed…") instead of bullet fragments.

## Model not listed

When the target model has no section above, research it before generating:

1. Run a brief web search (1–3 queries, e.g. `{model name} prompt guide`, `{model name} negative prompt aspect ratio`) and answer this checklist:
   - preferred prompt style: keyword lists or natural-language prose?
   - negative prompt support: dedicated field, inline parameter, or none?
   - aspect ratio / resolution control: parameter, setting, or described in text?
   - maximum native output resolution (drives the upscale note)
   - any model-specific parameter syntax worth appending
2. Build the adaptation from those answers, following the same pattern as the sections above. Tell the user, in one line, what the research found.
3. When search is unavailable or the findings stay inconclusive, fall back to **Generic** and say so.
