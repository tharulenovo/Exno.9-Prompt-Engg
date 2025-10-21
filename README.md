# Exno.9-To explore and understand the various prompting techniques used for generating videos through AI models. 

# Date: 16-10-2025
# Register no.: 25012025
# Aim: To perform the Exploration of Prompting Techniques for Video Generation
# Algorithm: Explore how various prompting techniques can be used to generate and manipulate video content (e.g., animations, visual effects, video summaries) using AI models. Procedure:
Familiarize Yourself with Video Generation Models:
Begin by exploring AI tools capable of video generation from text prompts. Popular models for video generation include:
Runway Gen-2
Synthesia
Pictory
DeepBrain
Understand the capabilities and limitations of each tool before starting the experiment.
Create Simple Prompts for Video Generation:
Start with simple prompts to generate short videos. These prompts should describe the general subject or activity.
Example prompt: "A person walking in a park."
Experiment with More Detailed Prompts:
Gradually refine your prompts by adding specific details, such as the setting, lighting, actions, or expressions.
Example prompt: "A person in a red jacket walking along a sunny park path, with birds flying in the sky, and a dog running beside them."
Add Time and Motion Elements:
Incorporate aspects like timing, transitions, or camera movement in your prompts.
Example prompt: "A time-lapse video of the sun setting over the ocean, with the camera slowly zooming out from a beach, capturing the waves and changing colors in the sky."
Test Different Video Styles:
Experiment with different styles of video generation, such as animations, live-action, cinematic, or artistic.
Example prompt: "An animated scene of a futuristic city at night, with glowing neon lights, flying cars, and a bustling crowd of people."
Iterate and Adjust Prompts:
Evaluate the generated video and refine the prompt if needed. Consider aspects like the pacing, transitions, and consistency of motion in the video.
Example: After reviewing, refine the prompt to add more details about the camera angles or actions: "A cinematic shot of a car speeding through a neon-lit city at night, with reflections on the wet street and a high-speed chase scene."
Generate Multiple Versions:
Generate multiple versions of the same prompt with slight variations to compare how the video output differs based on the phrasing of the prompt.
Save and Compare Outputs:
Save different versions of the videos and compare the results to understand how different prompts produce varying styles, sequences, and video qualities.

# 1. Prompt Complexity Spectrum

# Level 1: Basic Prompts (Minimal Guidance)

# structure

"Generate a video of a cat playing in a garden"

# Output Characteristics:

- Generic content

- Default style/lighting

- Short duration (2-4 sec)

- Limited camera movement

# Level 2: Structured Prompts (Scene Description)

# structure:

"Create a 10-second video of:

Subject: A gray tabby cat

Action: Chasing a red butterfly

Environment: Sunlit flower garden at golden hour

Style: Cinematic close-ups with shallow depth of field"

# Output Improvements:

- Specific subject details

- Controlled environment

- Intentional visual style

- Better temporal coherence

# Level 3: Advanced Prompts (Directorial Control)

# Structure:

"Generate a 30-second animated sequence:

Scene 1 (0-10s): Wide shot of cyberpunk city at night, neon lights reflecting on wet pavement

Transition: Quick zoom to...

Scene 2 (10-20s): Close-up of android's face as eyes glow blue

Camera: Dutch angle with slow dolly movement

Style: Blade Runner aesthetic with cinematic color grading

FPS: 24 for filmic look"

# Output Enhancements:

- Precise shot composition

- Controlled pacing

- Consistent art direction

- Professional cinematography elements

# 2. Key Prompting Techniques

# A. Temporal Chunking

Break videos into sequential segments:

"Create a 15-second product demo:  

1. 0-5s: Wide shot showing product in context  

2. 5-10s: Close-up highlighting key features  

3. 10-15s: Text overlay with value proposition"

# B. Style Anchoring

Reference known media properties:

"Generate in the style of Studio Ghibli:  

- Hand-painted watercolor backgrounds  

- Character designs with soft edges  

- Gentle camera movements  

- Pastel color palette"

# C. Motion Specification

Control movement dynamics:

"Camera: Slow 360° orbit around subject  

Subject motion: Hair blowing in wind (speed: gentle breeze)  

Background: Time-lapse clouds moving left-to-right"


# D. Negative Prompting

Exclude unwanted elements:

"Exclude:  

- Watermarks  

- Low-resolution frames  

- Uncanny valley effects  

- Jittery camera movements"


# 3. Python Implementation Example


    from diffusers import DiffusionPipeline


    import torch


    class VideoGenerator:
   
    def __init__(self, model_name="zeroscope-v2-xl"):
    
        self.pipe = DiffusionPipeline.from_pretrained(
        
            model_name,
            
            torch_dtype=torch.float16
        
        ).to("cuda")
    
    def generate_video(self, prompt, negative_prompt="", 
                     num_frames=24, fps=8, steps=30):
        return self.pipe(
            prompt,
            negative_prompt=negative_prompt,
            num_frames=num_frames,
            height=576,
            width=1024,
            num_inference_steps=steps,
            guidance_scale=15,
            fps=fps
        ).frames[0]


    generator = VideoGenerator()

    basic_vid = generator.generate_video(

    "A spaceship flying through space"
    
    )

    advanced_vid = generator.generate_video(

    prompt="""Cinematic shot of SpaceX Starship launch:
    
             - Camera: Slow-motion tracking from launchpad POV
             
             - Details: Visible engine plume dynamics
             
             - Atmosphere: Dawn lighting with fog effects""",
   
    negative_prompt="low quality, cartoonish, unrealistic",
    
    num_frames=48,
    
    fps=24,
    
    steps=50
    
    )

# 4. Prompt Engineering Best Practices

# The 5 W Framework:

- Who/What: Clear subject specification

- Where: Environmental context

- When: Temporal setting

- Why: Purpose/goal of the video

# Technical Parameters:

    {
   
     "duration": "15 seconds",
  
    "aspect_ratio": "16:9", 
  
    "framerate": 24,
  
    "style": "hyper-realistic CGI",
  
    "lighting": "volumetric god rays"
    
    }
 
# Reference Embedding:

"Visual composition similar to <reference_image.jpg> but with:  

- Cooler color temperature  

- More dynamic camera angles  

- Added futuristic HUD elements"

# Iterative Refinement:

"Based on output #1 (attached):  

1. Maintain the excellent lighting  

2. Increase character detail by 30%  

3. Smooth the walking animation  

4. Add falling cherry blossom petals"

# Comparative Results Analysis

<img width="682" height="247" alt="image" src="https://github.com/user-attachments/assets/ab7777b9-6eec-4d5f-973f-326bffb5da38" />

# 6. Emerging Techniques

# A. Multi-Modal Prompting

Combine:

1. Text description (this prompt)

2. Style reference images (3 samples)

3. Audio track (for timing/mood)

4. Motion capture data (for animations)

# B. Interactive Generation

    while not user_satisfied:

    generated_vid = model.generate(
    
        prompt + user_feedback,
        
        preview=True
    
    )
    
    user_feedback = get_user_input()

# C. Physics-Aware Prompting    

"Water simulation parameters:  

- Surface tension: 0.072 N/m  

- Viscosity: 0.89 mPa·s  

- Splash particle count: 500-700  

- Render: Photorealistic fluid dynamics"

# Prompt For Video Generation

Create a 30-second advertisement video for Cetaphil Face Wash featuring only male characters,
targeting young men with sensitive or acne-prone skin. Start with a close-up of a young man looking at his irritated
skin in the mirror. Show him applying Cetaphil Face Wash with a smooth lather, followed by water rinsing off easily.
Include visuals of calming ingredients like aloe vera and water splashes. Show his skin
visibly clearer and healthier after use. End with him confidently stepping out, smiling. Voiceover:
‘Real care for real skin. Cetaphil – gentle, effective, and made for men.’ Include soft, modern background
music and display the Cetaphil logo at the end.

# Result: The Prompt of the above task executed successfully









# Result:

