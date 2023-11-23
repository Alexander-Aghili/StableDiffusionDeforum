# StableDiffusionDeforum - Alexander Aghili

This repo contains all my personal Stable Diffusion creations with Deforum and the settings associated with them.

Table of Contents
- [Introduction](#introduction)
- [Usage](#usage)
- [Settings Guide](<#settings guide>)
- [License](#license)

## Introduction
[Stable Diffusion Deforum](https://github.com/deforum-art/deforum-stable-diffusion) is an AI Art Generating tool that can create videos using AI generated images. You can edit configurations to create a variety of differing styles and movements. An example of a long, detailed rendering is here: [Pink Floyd - Echoes \(A.I. Generated Music Video\)](https://www.youtube.com/watch?v=kGLo8tl5sxs).
In this README, I will describe basic usage, provide supplementary resources, and explain the settings to create your own Deforum rendering.

## Usage
I recommend that you use Google Colab to run the .ipynb file, as it is easiest, you get access to Google's T4 GPUs, and its free. All you need is a Google Drive with enough storage for the AI models and then each rendering you want to make. Simply download the .ipynb file I have provided: 'Alexander\_Aghili-Deforum\_Stable\_Diffusion\_Template.ipynb'. Go to Google Colab and click File-\>Upload Notebook and upload it. You should see it pop up and be able to run the cells. 
Each Cells is as follows:
- Nvidia GPU: Runs notebook on a GPU.
- Environment Setup: Required configurations for notebook.
- Path Setup: Setup up of local drive path for storage (You'll need to sign in with your gmail, I used my school email since it has unlimited space).
- Model Setup: Downloads (or uses existing) AI models required for Deforum.
- Settings: Collects all input settings (See [Seetings Guide](<#settings guide>) below for detailed instruction on settings).
- Prompts: Input prompts at frame.
- Load Settings: Will load settings and run image creation.
- Create Video from Frames: Creates a video from generated frames.
- Disconnect Runtime: Disconnect Runtime after you're finished. (Not entirely necessary, deleting the tab should do the same.)

Note that from my file, you need to change the input image for it to work, as this is the starter image. After that, running it should be as simple as running the cells and waiting.
Another important note is that the video cannot be created unless all frames are finished and that might take some time. It takes about 5-10 seconds to create each frame.

You can also refer to this video, but note it uses a local version instead of Google Colab: [Create Infinite AI DEFORUM Animations | Stable Diffusion Tutorial](https://www.youtube.com/watch?v=bicPayZDI60).

Everytime you run the load settings cell, the settings are saved in the drive folder with the images. When creating the video, make sure to disable skip\_video\_for\_run\_all.

## Settings Guide
### Animation:
- **animation_mode:** Specifies the type of animation to be applied. Options include 'None', '2D', '3D', 'Video Input', 'Interpolation'. (Type: string)

- **max_frames:** Maximum number of frames in the animation. (Type: number)

- **border:** Specifies the border mode, either 'wrap' or 'replicate'. (Type: string)

### Motion Parameters:
These parameters control various aspects of motion during animation.

- **angle:** Rotation angle in degrees. Format: "start:(end)". (Type: string, Function: No)

- **zoom:** Zoom factor. Format: "start:(end)". (Type: string, Function: No)

- **translation_x, translation_y, translation_z:** Translation along the X, Y, and Z axes, respectively. Format: "start:(end)". (Type: string, Function: Yes)

- **rotation_3d_x, rotation_3d_y, rotation_3d_z:** 3D rotation along the X, Y, and Z axes, respectively. Format: "start:(end)". (Type: string, Function: Yes)

- **flip_2d_perspective:** Boolean indicating whether to flip 2D perspective. (Type: boolean)

- **perspective_flip_theta, perspective_flip_phi, perspective_flip_gamma, perspective_flip_fv:** Parameters for perspective flipping. (Type: string, Function: Yes)

- **noise_schedule, strength_schedule, contrast_schedule:** Schedules for noise, strength, and contrast, respectively. (Type: string, Function: Yes)

### Sampler Scheduling:
- **enable_schedule_samplers:** Boolean indicating whether to enable sampler scheduling. (Type: boolean)

- **sampler_schedule:** Schedule for samplers, with specified time intervals and corresponding sampler types. (Type: string, Function: Yes)

### Unsharp mask (anti-blur) Parameters:
- **kernel_schedule, sigma_schedule, amount_schedule, threshold_schedule:** Schedules for kernel size, sigma, amount, and threshold for unsharp mask. (Type: string, Function: Yes)

### Coherence:
- **color_coherence:** Specifies color coherence mode. Options include 'None', 'Match Frame 0 HSV', 'Match Frame 0 LAB', 'Match Frame 0 RGB', 'Video Input'. (Type: string)

- **color_coherence_video_every_N_frames:** Frequency of applying color coherence in video frames. (Type: integer)

- **color_force_grayscale:** Boolean indicating whether to force grayscale. (Type: boolean)

- **diffusion_cadence:** Cadence for diffusion. Options include '1', '2', '3', '4', '5', '6', '7', '8'. (Type: string)

### 3D Depth Warping:
- **use_depth_warping:** Boolean indicating whether to use 3D depth warping. (Type: boolean)

- **midas_weight, near_plane, far_plane, fov:** Parameters for 3D depth warping. (Type: number)

- **padding_mode:** Modes for padding, options include 'border', 'reflection', 'zeros'. (Type: string)

- **sampling_mode:** Modes for sampling, options include 'bicubic', 'bilinear', 'nearest'. (Type: string)

- **save_depth_maps:** Boolean indicating whether to save depth maps. (Type: boolean)

### Video Input:
- **video_init_path:** Path to the initial video. (Type: string)

- **extract_nth_frame:** Interval for extracting frames from the video. (Type: number)

- **overwrite_extracted_frames:** Boolean indicating whether to overwrite extracted frames. (Type: boolean)

- **use_mask_video:** Boolean indicating whether to use a mask video. (Type: boolean)

- **video_mask_path:** Path to the mask video. (Type: string)

### Hybrid Video for 2D/3D Animation Mode:
- **hybrid_generate_inputframes, hybrid_use_first_frame_as_init_image:** Booleans indicating whether to generate input frames and use the first frame as the initial image. (Type: boolean)

- **hybrid_motion:** Type of hybrid motion ('None', 'Optical Flow', 'Perspective', 'Affine'). (Type: string)

- **hybrid_motion_use_prev_img:** Boolean indicating whether to use the previous image for hybrid motion. (Type: boolean)

- **hybrid_flow_method:** Method for hybrid flow. Options include 'DenseRLOF', 'DIS Medium', 'Farneback', 'SF'. (Type: string)

- **hybrid_composite:** Boolean indicating whether to perform hybrid compositing. (Type: boolean)

- **hybrid_comp_mask_type:** Type of hybrid composite mask. Options include 'None', 'Depth', 'Video Depth', 'Blend', 'Difference'. (Type: string)

- **hybrid_comp_mask_inverse, hybrid_comp_mask_equalize, hybrid_comp_mask_auto_contrast:** Boolean settings for mask inversion, equalization, and auto-contrast. (Type: boolean)

- **hybrid_comp_save_extra_frames, hybrid_use_video_as_mse_image:** Boolean settings for saving extra frames and using the video as the mean squared error (MSE) image. (Type: boolean)

### Interpolation:
- **interpolate_key_frames:** Boolean indicating whether to interpolate key frames. (Type: boolean)

- **interpolate_x_frames:** Number of frames to interpolate between key frames. (Type: number)

### Resume Animation:
- **resume_from_timestring:** Boolean indicating whether to resume animation from a specified timestring. (Type: boolean)

- **resume_timestring:** Timestring to resume animation from. (Type: string)

This cell is designed to collect various parameters and settings for a stable diffusion animation, allowing for fine-tuning and customization. Adjustments can be made based on specific animation requirements and preferences.

### Prompts / Neg Prompts:
Include prompts at frames to guide the image creation.

### Image Settings
- **W**: Width of the output image in pixels.
- **H**: Height of the output image in pixels.
- **bit_depth_output**: Output image bit depth (8, 16, 32).

### Sampling Settings
- **seed**: Random seed for the generation process.
- **sampler**: Sampling method for image generation.
- **steps**: Number of steps for the diffusion process.
- **scale**: Scale parameter for the diffusion process.
- **ddim_eta**: Eta parameter for the DDIM sampler.
- **dynamic_threshold**: Dynamic threshold for sampling.
- **static_threshold**: Static threshold for sampling.

### Save & Display Settings
- **save_samples**: Whether to save generated samples.
- **save_settings**: Whether to save settings.
- **display_samples**: Whether to display generated samples.
- **save_sample_per_step**: Save a sample for each diffusion step.
- **show_sample_per_step**: Display a sample for each diffusion step.

### Batch Settings
- **n_batch**: Number of batches.
- **n_samples**: Number of samples per batch.
- **batch_name**: Name of the batch.
- **filename_format**: Format for saving filenames.
- **seed_behavior**: Seed behavior (iter, fixed, random, ladder, alternate).
- **seed_iter_N**: Seed iteration count.
- **make_grid**: Whether to arrange samples in a grid.
- **grid_rows**: Number of rows in the grid.
- **outdir**: Output directory for saved samples.

### Init Settings
- **use_init**: Whether to use an initial image.
- **strength**: Strength parameter for the initial image.
- **init_image**: URL of the initial image.
- **add_init_noise**: Whether to add noise to the initial image.
- **init_noise**: Strength of the noise.
- **use_mask**: Whether to use a mask for the initial image.
- **use_alpha_as_mask**: Whether to use the alpha channel as a mask.
- **mask_file**: URL of the mask image.
- **invert_mask**: Whether to invert the mask.
- **mask_brightness_adjust**: Brightness adjustment for the mask.
- **mask_contrast_adjust**: Contrast adjustment for the mask.
- **overlay_mask**: Overlay the masked image at the end.
- **mask_overlay_blur**: Blur edges of the overlay mask.

### Exposure/Contrast Conditional Settings
- **mean_scale**: Mean scale for exposure/contrast.
- **var_scale**: Variance scale for exposure/contrast.
- **exposure_scale**: Exposure scale.
- **exposure_target**: Target exposure.

### Color Match Conditional Settings
- **colormatch_scale**: Scale for color matching.
- **colormatch_image**: URL of the color matching image.
- **colormatch_n_colors**: Number of colors for matching.
- **ignore_sat_weight**: Saturation weight for color matching.

### CLIP\Aesthetics Conditional Settings
- **clip_name**: Name of the CLIP model.
- **clip_scale**: Scale for CLIP guidance.
- **aesthetics_scale**: Scale for aesthetics guidance.
- **cutn**: Cutn parameter for CLIP.
- **cut_pow**: Cut power parameter for CLIP.

### Other Conditional Settings
- **init_mse_scale**: Scale for MSE in initialization.
- **init_mse_image**: URL of the MSE initialization image.
- **blue_scale**: Scale for the blue channel.

### Conditional Gradient Settings
- **gradient_wrt**: Variable to compute gradient with respect to.
- **gradient_add_to**: Where to add the gradient (cond, uncond, both).
- **decode_method**: Decoding method (autoencoder, linear).
- **grad_threshold_type**: Type of gradient thresholding.
- **clamp_grad_threshold**: Gradient threshold value.
- **clamp_start**: Starting threshold value.
- **clamp_stop**: Stopping threshold value.
- **grad_inject_timing**: Timing for injecting gradient.

### Speed vs VRAM Settings
- **cond_uncond_sync**: Synchronize conditional and unconditional parts.
- **precision**: Precision mode (autocast).
- **C**: Constant for speed control.
- **f**: Constant for speed control.

## Video Creation Parameters
- **skip_video_for_run_all (Boolean):** If set to True, it skips the video creation process.
- **create_gif (Boolean):** If set to True, it will create a GIF along with the video.
- **ffmpeg_mode (String):** Specifies the mode for handling ffmpeg settings. Options include "auto," "manual," and "timestring." Default is "auto," determining how ffmpeg settings such as output directory and time string are handled.
- **ffmpeg_outdir (String):** Output directory for ffmpeg. Default is an empty string, specifying the directory where the output files will be saved.
- **ffmpeg_timestring (String):** Time string for ffmpeg. Default is an empty string, providing a time string for ffmpeg, used in the naming of output files.
- **ffmpeg_image_path (String):** Path for ffmpeg images. Default is an empty string, specifying the path where the images processed by ffmpeg will be saved.
- **ffmpeg_mp4_path (String):** Path for ffmpeg MP4 video. Default is an empty string, specifying the path where the MP4 video created by ffmpeg will be saved.
- **ffmpeg_gif_path (String):** Path for ffmpeg GIF. Default is an empty string, specifying the path where the GIF created by ffmpeg will be saved.
- **ffmpeg_extension (String):** File extension for ffmpeg output images. Default is "png," specifying the file extension for the images processed by ffmpeg.
- **ffmpeg_maxframes (Integer):** Maximum number of frames for ffmpeg. Default is 200, specifying the maximum number of frames to be processed by ffmpeg.
- **ffmpeg_fps (Integer):** Frames per second for ffmpeg. Default is 12, specifying the number of frames per second for the output video.
- **display_ffmpeg (Boolean):** If set to True, displays ffmpeg command during execution. Default is True, determining whether to display the ffmpeg command during execution.
- **debug (Boolean):** If set to True, enables debugging information during execution. Default is False, determining whether to enable debugging information during script execution.


## License
Copyright 2023 Alexander Aghili

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.




