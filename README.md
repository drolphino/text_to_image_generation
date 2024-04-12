# text_to_image_generation
Brief about your familiarity of Diffusion space:
I found it very interesting, to generate cool stuff by just entering texts, I got through all the possible ways to generate and modulate the image. Generally the processof image generation happens via learning to predict the noise in a given noisy image to remove it and make it more close to the generated image. But it is highly resource extensive, so first via VAE the image is encode to latent space where performing the diffusion process is much easier and faster, and then finally the image is decoded into original image. Majorly this happens in the base diffusion models. We can fine tune this base model for various specific use cases or add adapters such as LORA for faster implementation.


Models I used for the experiment:(SDXL turbo, SDXL base, ByteDance/SDXL-Lightning(2-Step, 4-Step, 8-Step UNet), ByteDance/SDXL-Lightning(2-Step, 4-Step, 8-Step LoRA)

STEP 1:  
Prompt: 
Approach:
Wrote prompt in detailed, describing:
  	1. Photographic style, drawing.
	2. About subject, body , hair, facial expression.
	3. Style, resolution, lightning, colors.
Negative promt:
1. Qualities and thing Idon’t want to be part of image.
Used upweights(++), downweights(--) and blends to emphasise on certain parts of the prompts.

Findings:
For different types of models, different type of prompts give better results.
Instead of describing sentence, a more precise word is better understood by model.

Optimization:
More in detail prompts can be written, using more precise words and embedded texts.

STEP 2:
Models:
Approach:
For more photorealistic image generation, I used stable diffusion heavy models( SDXL ) and its checkpoints.
For making inference faster, decreased the precision.
For every different model, we have to choose the right scheduler(which is a challenge).
Used .safetensor models as they are safe and fast.
Gradient_scale parameter is used to make image more diverse with same random seed.


Findings:
I used CLIP score to evaluate used models, as how much the generated image is aligned with the text embeddings, based on which  ByteDance/SDXL-Lightning(2-Step, 4-Step, 8-Step UNet) performed the best.
If we don’t need to train our models, we can use pruned models which are faster, and almost give similar results.

Optimization:
Better models such as SDjuggernaut can give better results.
Mixing models such as realism and juggernaut can give very amazing results.
For facial expression we can use GFPGAN.
For upscalling we can use Real-ESRGAN.


Note: I tried to upscale the image using stable-diffusion-x4-upscaler-img2img but got some GPU issues, optimization ( can be implemented by reducing the size of image befor processing, or apply batching computing).


