## Table of Contents
  
- [Introduction](#introduction)
- [Setting Expectations](#setting-expectations)
- [Existing Plugins](#existing-plugins)
- [New Plugin](#new-plugin)
- [Planned Improvements for the plugins](#planned-improvements-for-the-plugins)
- [YouTube Update](#youtube-update)
- [Procedural Generation Project](#procedural-generation-project)
- [Community Updates](#community-updates)


### Introduction

Thank you all for your continued support and patience.  
  
Since this is a lengthy announcement, I've made it available on GitHub for easier access and archiving. I recommend reading it there instead of Discord.

I've divided this announcement into two parts.

### Setting Expectations

Classes begin on Monday, and as some of you know, I am a full time university student. Balancing school, previous commitments, and personal challenges has left me with limited time for projects. I want to be transparent about this because I truly value your support and understanding. 

Moving forward, I will not be as active in providing direct assistance or answering questions on the Discord server. My goal is for this community to evolve into something more collaborative, rather than just a place to ask for help. In time, I will create an FAQ and other resources to fill the gap in my absence, but these will only come after I finish setting up the necessary infrastructure for community contributions.

Additionally, my time constraints will impact how frequently I can release new content. I need to focus on fulfilling my previous commitments in the short term while shifting my future work to align with my research interests.

I will also be working on creating tools to automate and streamline certain aspects of my life, intending to reduce the time and mental effort spent on non-priority tasks. Some of these tools may be relevant to the community, and I may share more about them in the future if they could be beneficial to others.

**Shifting Focus and Priorities**

I will be stepping back from content that focuses solely on game development. Instead, I plan to work on projects and activities that align with my values—projects that aim to benefit society, the planet and animals. As part of this shift, I will only take on new projects and research that reflect these values. I plan to transition to working on machine learning projects and research where I can make the most meaningful impact.

In light of this, I will not be taking on any new game development projects or experiences for the foreseeable future, including as part of community initiatives. However, I will still consider game development research proposals, but I will be very selective about the ones I choose to support. I plan to develop a formal application process for proposals in the future.

That said, I will continue to develop and release Unreal Engine plugins for free on the Unreal Marketplace. However, stepping back from non-development aspects of the community will allow me to release these plugins more efficiently. However, I need your help—if you’d like to see the plugins released sooner, need additional features, or want to contribute to their development, please consider becoming a contributor. Be aware that contributor resources are currently limited, and the initial stages may be a bit messy as we work to establish proper onboarding processes and dedicated spaces. Please dm me if you are interested in contributing.

**Addressing Plugin Bugs**

Some long-standing bugs in the plugins still need to be addressed. I will be creating GitHub issues to track these bugs, and I will resolve some of them myself. However, contributions from the community will be greatly appreciated.

**Origins and Goals**

The Unreal Engine plugins were originally created to support my research. One of the main initiatives driving these efforts is the exploration of transfer learning from Unreal Engine datasets to real-world applications. A key goal of this research is to develop an autonomous trash collection robot.

Thank you for your patience and understanding as we navigate these changes. I am deeply grateful to be part of this community, and I look forward to continuing this journey together. Together, we will keep evolving, learning, and growing.
### Existing Plugins  
  
**Tokenizers-UE Update:**    
  
I've significantly improved the README for [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE). The updated documentation now includes detailed steps to get started with the library, making it more user-friendly.  
  
**Unreal plugin CI/CD:**    
  
You can now compile the [Tokenizers-CPP](https://github.com/P1ayer-1/tokenizers-cpp) static library required for [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE) using GitHub Actions. This addition streamlines the setup process and is a step towards a complete CI/CD pipeline for the Unreal plugins.  
  
I've been exploring continuous integration/continuous deployment (CI/CD) solutions for Unreal Engine. There’s a [project](https://github.com/Guganana/UnrealPluginCIWithGithubActions) that has developed a miniature version of Unreal Engine suitable for the free tier of GitHub Actions. Although it can’t be distributed due to Epic’s TOS, we can create it ourselves for use with our GitHub organization. This version would be accessible only to members of our organization to comply with Epic’s TOS. While we can't share this build publicly, I plan to create a public repository with steps to build your own miniature Unreal Engine. Ideally, this would include a script to handle the process.  
  
I believe that a miniature Unreal build would be immensely beneficial to the community. I've done some initial work determining what parts of the engine can be removed to save space. The miniature CI/CD Unreal build is planned for future creation. Contributors are welcome to take on this task themselves, as I believe it would be useful to many Unreal developers. If there is insufficient interest in this approach, I may decide to go the paid self-hosted route instead.  
  
All of the plugins have been transferred to the newly created GitHub organization, [NextGen GameDev](https://github.com/NextGen-GameDev).  Contributors can become organization members, enhancing our collaborative efforts.  
  
### New Plugin  
  
I’m excited to announce a new plugin named **[DeepThought Engine](https://github.com/NextGen-GameDev/DeepThought-Engine)**. This library integrates the existing [LibTorch-UE](https://github.com/NextGen-GameDev/LibTorch-UE) and [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE) plugins as optional dependencies, enabling streamlined machine learning operations, such as generation with transformer models.  
  
[DeepThought Engine](https://github.com/NextGen-GameDev/DeepThought-Engine) will integrate multiple machine learning backends and related libraries (e.g. [OpenCV](https://opencv.org/)). The name draws inspiration from "[*The Hitchhiker's Guide to the Galaxy*](https://en.wikipedia.org/wiki/The_Hitchhiker%27s_Guide_to_the_Galaxy)" and [Microsoft's DeepSpeed](https://www.deepspeed.ai/). Notably, "[*DeepSpeedEngine*](https://github.com/microsoft/DeepSpeed/blob/master/deepspeed/runtime/engine.py#L182)" is the class name for training models using [DeepSpeed](https://www.deepspeed.ai/).  
  
The library serves a role similar to [HuggingFace Transformers](https://huggingface.co/docs/transformers/en/index) in relation to PyTorch but will focus on various model architectures, such as diffusion models. Future updates will include support for additional frameworks like TensorFlow and ONNX. There will also be support for model formats like GGUF ([Llama-CPP](https://github.com/ggerganov/llama.cpp)) and backends like Vulkan and SYCL.
  
Plugins for [TensorFlow](https://github.com/getnamo/TensorFlow-Unreal) and [Llama-CPP](https://github.com/getnamo/Llama-Unreal) already exist. They will be forked and integrated as ML backend plugins in [DeepThought Engine](https://github.com/NextGen-GameDev/DeepThought-Engine).  

### Planned Improvements for the plugins  
  
I recently found a method to improve the [LibTorch-UE](https://github.com/NextGen-GameDev/LibTorch-UE) plugin by compiling [LibTorch](https://pytorch.org/cppdocs/) (PyTorch C++) inside Unreal Engine. This allows us to avoid modifying LibTorch header files during setup and enables us to use `torch::jit::load` to load TorchScript models (The process shown [here](https://pytorch.org/tutorials/advanced/cpp_export.html)). This improvement makes it significantly easier to load models created outside the plugins, such as those developed using the PyTorch Python library. This enhancement will be implemented before the marketplace release.  
  
Additionally, it should be possible to compile [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE) in-engine using a similar strategy. This change would allow for easier packaging and avoid manually placing the [Tokenizers-CPP](https://github.com/P1ayer-1/tokenizers-cpp) static library inside [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE) during setup.  
  
### YouTube Update  

**Data Course on Hold Indefinitely**

After much consideration, I’ve decided to put the data course on hold. I don’t have a set date for when or if I’ll resume work on it. I’ve realized that my priorities have shifted, and there are other projects that align more closely with where I want to focus my energy right now.


**YouTube Video on Tiny Custom Models**

Regarding the YouTube series, I’ve been rethinking how to approach the video on training a tiny custom model. While I initially planned to create a video on training a tiny custom model to use with the Unreal plugins, I realized that making this video both useful and applicable to everyone is more complex than I initially thought. The amount of information needed for viewers to do this effectively is quite substantial. 

The process of creating a custom model involves several steps, including acquiring and preparing high-quality data, which is a challenge even for many in the ML community. The quality of the model heavily depends on the dataset used, and determining what constitutes good data is something many experienced ML practitioners struggle with. While I could demonstrate my method, it might not be easily applicable to most people's projects, especially since many would need to create or scrape custom datasets for their games—a task that requires specific skills and a significant time investment.

Moreover, since this is a method I’ve developed through my own experimentation, there aren’t many external resources or guides to supplement the video. Outside of a few academic papers that inspired me, much of what I’ll cover isn’t documented elsewhere. This means the video would need to be very detailed to ensure it's comprehensive.

The video would need to cover a lot of ground to be truly effective, which could make it longer and more detailed than originally planned. I'm concerned that without a solid understanding of how to integrate these models into a game, many might not be able to apply the concepts effectively. There’s also a risk of confusion around how model accuracy translates to in-game use and how to feed game data into the model as inputs.

I still believe in the value of custom models, but I want to ensure that any content I produce is both accessible and useful. Therefore, I’m rethinking how to best present this material. The goal is to create something that not only builds on the existing tutorials but also provides a clear, practical path for those looking to apply these techniques in their own projects.

**Video Reupload**

The video on using [LibTorch-UE](https://github.com/NextGen-GameDev/LibTorch-UE) and [Tokenizers-UE](https://github.com/NextGen-GameDev/Tokenizers-UE) plugins was temporarily taken down due to an incorrect content ID claim by UMG. I decided to refrain from disputing the claim and have put the video live again.  

Here is a [link](https://youtu.be/XlMys9e3NgY) to the reuploaded video
### Procedural Generation Project  

**Deferred Start Due to Prior Commitments**

I wanted to give an update regarding a new project I mentioned recently in the general channel. While I’m excited about this collaboration with Simon, I’ve realized that I won’t be able to start on it immediately due to my existing commitments. I need to finish what I’m currently working on before I can fully contribute to this project.

Once I’m ready to dive in, we will make an official announcement with all the details through a public post on our Discord server and Medium. This post will also serve as the project's official start date, and development will kick off from there. The project repository will be hosted under the newly created GitHub organization, [NextGen GameDev](https://github.com/NextGen-GameDev).

For those of you eager to get involved, there will be some preliminary work that can be started in the meantime. If you're interested, please drop a message in the [#diffusion-procedural-gen](https://discord.com/channels/1127804091477799042/1276292304067625051) channel, which is exclusively for contributors. Please direct message me if you are interested in becoming a contributor. 

Simon, who has extensive experience with diffusion models, will be a key contributor to this project. We connected through the [LAION OpenAssistant project](https://open-assistant.io/bye), and his expertise will be crucial in tackling the challenges we’ve identified with current procedural generation techniques.

Our goal is to improve procedural generation by using AI-generated heightmaps via latent probabilistic diffusion, similar to methods used in Stable Diffusion and Midjourney. We aim to create more realistic and engaging environments, addressing the common issue of unrealistic and dull worlds found in games like Bethesda's Starfield. This [video](https://youtu.be/EkURp59BAas?si=ztv7y7n4r83-eAoL) illustrates the issues that stem from poor procedural generation.

To achieve this, we’ll start by collecting Digital Elevation Model (DEM) data for planets like Earth and Mars, and then train a diffusion model from scratch. There’s also potential to expand this approach by incorporating Digital Terrain Model (DTM) data and Digital Surface Model (DSM) data in the future.

For those interested in how heightmaps work within Unreal Engine, you can refer to this [page](https://dev.epicgames.com/documentation/en-us/unreal-engine/importing-and-exporting-landscape-heightmaps-in-unreal-engine).

### Community Updates  
  
**Business Registration:**    
  
I have registered the business that will manage these plugins. It is a federal corporation in Canada. 
  
**Marketplace Vendor Profile:**    
  
I applied to become an Epic marketplace publisher when I started writing this post. Over the time I've been writing, the application has been approved.  
  
This is very exciting! We can release the plugins on the Epic Marketplace once we have achieved the requirements.  
  
**Free and Open Source:**    
  
The plugins will be free and open source indefinitely. They will be released on the Epic Marketplace at no cost.  
