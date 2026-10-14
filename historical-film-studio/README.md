# Historical Film Studio — browser-only image-to-video workflow

This page chains a hosted image generator into a hosted image-to-video model:

1. `mrfakename/Z-Image-Turbo` generates a still from the historical-scene prompt.
2. `zerogpu-aoti/wan2-2-fp8da-aoti-faster` receives that image automatically and animates it using the motion prompt.

The page can also animate an existing JPG, PNG, or WebP. Use **Animate an existing image instead** for a frame generated in ChatGPT; that file must be selected manually because a separate website cannot retrieve private ChatGPT attachments automatically.

## No installation

Open the live GitHub Pages subpage in a browser. The studio uses the Gradio JavaScript client from jsDelivr and does not require Blender, Python, Node, a paid API key, or a desktop installation.

## Limits

- The image and video backends are public Hugging Face ZeroGPU demos, not guaranteed production services.
- Free ZeroGPU quotas are limited, queues can be busy, and quotas or model endpoints can change.
- The first output is a short clip for testing the chain, not a finished historical film.
- The image generator creates a concept image; it does not validate the archaeology or the exact geography.
- A historical timelapse still requires source-backed matched frames and careful inspection for architecture drift before treating the result as geographically or historically accurate.

## Model connections

The page currently calls the public Gradio endpoints `/generate_image` and `/generate_video`. If either Space changes its API, update the endpoint configuration in `index.html`.

- Image Space: https://huggingface.co/spaces/mrfakename/Z-Image-Turbo
- Video Space: https://huggingface.co/spaces/zerogpu-aoti/wan2-2-fp8da-aoti-faster

This is a prototype to prove the automated frame-to-video handoff. It does not claim unlimited free rendering, guaranteed uptime, or automatic ingestion of private ChatGPT-generated images.
