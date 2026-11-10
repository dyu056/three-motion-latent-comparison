# Three-motion latent comparison

710 input-image/prompt pairs: MemoBench 360, MIND test 150, MIND train 100, R2M-Bench 100. All cases completed and passed independent CPU FP64 readback. Training and evaluation splits remain labeled; this is a representation diagnostic, not an official benchmark score.

A is forward camera translation; B is right camera yaw; both use the same first image, original prompt, seed 42, initial noise and intermediate re-noising draws. C is the exact time reversal of B's original floating-point RGB, independently encoded by the same frozen VAE. C starts at B's endpoint.

Frozen DreamX-World-5B and Wan2.2 TI2V VAE, 1280x704, source 24fps, four denoising steps, three-latent AR blocks, sink 3 and local window 12. Generate 12 latents and decode the first 10 into 37 RGB frames. The requested RGB trajectory reaches forward displacement 1.8 / right yaw 30 degrees at index 36, followed by endpoint holds through index 44. The official camera packer samples [0,1,5,9,13,17,21,25,29,33,37,41]; the last retained latent uses the index33 request, displacement 1.65 / yaw27.5 degrees. These are requested controls, not independently estimated visual poses.

All three groups are RGB-reencoded before comparison. FP32 latent values use FP64 metric reductions. Full, first-slot-excluded and first/last-slot-excluded metrics are retained in CSV/JSON. Per-case 10x10 cosine/Pearson/MSE matrices retain every temporal position. Nominal latent reversal changes indexing; causal history and four-frame supports still differ.

The three-column videos preserve all 37 frames at 8fps for inspection (3x slower than the source). H.264 CRF24 web copies and JPEG previews are presentation assets. Published numerical data are unchanged; no metrics are recomputed from the compressed videos. Original floating-point RGB, full-resolution videos, shared noise, camera arrays and latent tensors remain in the experiment archive.

No analytics, third-party scripts, external fonts or runtime dependencies are used. All site links work under a GitHub Pages project subpath. The site includes every registered case, regardless of its similarity score.
