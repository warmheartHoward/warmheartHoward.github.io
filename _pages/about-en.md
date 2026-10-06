---
permalink: /en/
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

# About Me

I am currently an AI Algorithm Engineer at the Multimodal Model Lab, Foundation Model Department, Huawei 2012 Laboratories, working on video understanding, world knowledge, and OCR reasoning for the Pangu multimodal large model (VL) and the Xiaoyi assistant. I graduated with a Master's degree in Electronic Information from Tsinghua University Shenzhen International Graduate School, specializing in vision measurement. I completed my undergraduate studies in Mechanical Design, Manufacturing and Automation at Chongqing University. I have extensive internship and engineering implementation experience, with publications in Chinese core journals and multiple patents.

<div class="tags">
  <span class="tag">International Talent</span>
  <span class="tag">Interdisciplinary Integration</span>
  <span class="tag">Outstanding Internship Experience</span>
</div>

My research areas include:

- Data and training for multimodal large models (VLM/MLLM)
- Streaming-video proactive interaction and long-video understanding
- World-knowledge injection, OCR, and complex reasoning
- Machine vision and vision-based measurement
  
<span class='anchor' id='-xl'></span>

# 🎓 Education Background
- *2022.09 - 2025.06*, <a href="https://www.sigs.tsinghua.edu.cn/"><img class="svg" src="/images/Tsinghua.png" width="23pt"></a> Tsinghua University, Shenzhen International Graduate School, Electronic Information (Intelligent Manufacturing), Shenzhen, Guangdong, Master's Degree (recommended exemption). 
- *2017.09 - 2022.06*, <a href="https://www.cqu.edu.cn/"><img class="svg" src="/images/Chongqing.png" width="23pt"></a> Chongqing University, Chongqing University - University of Cincinnati Joint College, Mechanical Design and Manufacturing Automation, Chongqing, Bachelor's Degree
 
<span class='anchor' id='-xmjl'></span>

# 🧭 Project Experience

<div class="proj-card" markdown="1">

### Project 1: Streaming-Video Proactive Interaction for Xiaoyi (Navigation and Obstacle Avoidance)

<span class="proj-meta">Huawei · 2025 - Present</span>

- **Situation:**
  Navigation and obstacle avoidance for visually impaired users require a model to spot obstacles in a continuous video stream and warn the user in time. The existing solution was single-frame and passive, which led to noticeable latency and poor temporal coherence.

- **Task:**
  Build a streaming-video proactive interaction stack from scratch, so that a multimodal large model can intervene, warn, and speak proactively in open-set scenes, covering data, training, inference, and evaluation.

- **Action:**
  - **Proactive trigger**: After surveying streaming frameworks such as VideoLLM-online, modeled proactive interaction as a binary special-token prediction task: after the image delimiter, the model predicts either a silent token or an assistant wake-up token.
  - **Streaming data engine**: Built a DenseCaption2PO-based synthesis and style-rewriting pipeline and a Grounding DINO-assisted human annotation loop, delivering **500K** curated samples.
  - **Stateful streaming inference**: Independently developed a Stateful Inference pipeline in PyTorch with a memory-friendly flow of historical chunk summaries and optimized KV-Cache management and tensor concatenation, reducing memory and latency for long streams.
  - **Training strategy**: Two-stage training (noisy-data pre-training, then fine-tuning on curated data) with a Sample Balance Loss to handle the heavy imbalance between trigger and non-trigger samples.
  - **Evaluation and diagnosis**: Built an open-set classification benchmark and visual diagnosis tools to locate issues in data distribution, trigger timing, and scene generalization.

- **Result:**
  - On key indoor and outdoor obstacle scenes, alert Precision reached **92.4%** and Recall **92.9%**, up 2.43 and 3.5 points over the single-frame baseline.
  - The project received the department **"2012 Star"** award and a **Xiaoyi Letter of Appreciation**.

</div>

<div class="proj-card" markdown="1">

### Project 2: Cultural-Relic World Knowledge for Pangu VL (92B)

<span class="proj-meta">Huawei · 2025 - Present</span>

- **Situation:**
  Foundation models have blind spots in vertical domains such as cultural relics and heritage, and tend to hallucinate facts, which blocks knowledge QA in the corresponding Xiaoyi scenarios.

- **Task:**
  Build a world-knowledge data system and a dedicated benchmark for the 92B model, meeting the need for knowledge density in the annealing stage and for instruction diversity in the SFT stage.

- **Action:**
  - **Knowledge system**: Built a relic tag taxonomy with multi-level categories from scratch, and sourced, cleaned, and organized data from digital museums and open datasets.
  - **Knowledge injection for annealing**: Built a high-concurrency labeling pipeline with external search and the ReAct paradigm, producing **2M** structured, dense captions.
  - **Data synthesis for SFT**: Designed a "Raw Distillation + Refine + confidence filtering" strategy that goes beyond a single template, producing **10M** QA and interleaved image-text samples while suppressing distillation hallucination.
  - **Benchmark**: Built the Xiaoyi relic benchmark covering knowledge accuracy, instruction following, and scene generalization.

- **Result:**
  - Delivered **12M** caption and QA samples in total.
  - The 92B model leads Qwen3.5-122B-A10B by **14.83 points** on the Xiaoyi relic benchmark and gains **13 points** on the Culture subset of the public WorldVQA benchmark.

</div>

<div class="proj-card" markdown="1">

### Project 3: OCR and Complex-Reasoning Data for Pangu VL v2.1

<span class="proj-meta">Huawei · 2025 - Present</span>

- **Situation:**
  For the Pangu VL v2.1 generation, the Xiaoyi smoke test covers real scenes such as ID cards, receipts, and tables, and demands strong OCR parsing and complex reasoning (e.g., multi-step numerical calculation). Existing data supplies perception and reasoning unevenly, and weak spots hide in capability cells nobody has measured.

- **Task:**
  Own the data for OCR and STEM capabilities: measure the weak spots first, generate data targeted at them, and use evaluation to correct the mix, supporting continuous training from Stage 2 and Midtrain to 32K / 128K / 512K long sequences.

- **Action:**
  - **Data profiling**: Ran large-scale deduplication with MD5 / embedding / pHash; designed a five-dimension profile (domain, genre, capability, difficulty, quality), labeled samples with a VLM, and trained lightweight classifiers on image-text embeddings to profile **100M+** samples.
  - **Weak-spot mining**: Mapped per-question evaluation results onto the same profile grid and combined them with training-corpus scarcity to separate true data gaps from quality or method problems, then filled gaps through recall from existing corpora, web retrieval, and procurement.
  - **Reasoning-QA production line**: Built a pluggable line driven by capability descriptions, seed questions, and weights, with capability-weighted question generation, multi-style answering, 13-dimension quality checks, and blind review and rewriting, using multiple models and fast/slow-thinking data; Stage 2 produced about 12M simple QA and Midtrain scaled to about 35M QA.
  - **Pilot before scale**: Validated the method on a 500K pilot (about +9 points) before scaling up.
  - **Fixing the long-sequence mix**: Traced a regression in 128K training to resampling that diluted the slow-thinking share from 64.1% to 23.7%; designed a resampling scheme that removes by length and refills by profile balance, with token counts measured in full, restoring the share to 64.9% (128K) and 70.0% (512K).

- **Result:**
  - The mid-train model scored **64.09%** on the Xiaoyi smoke test (582 questions), 12.5 points above the Stage 2 model.
  - 85.12% on the OCR subset, **4.95 points** above Qwen3.8-27B (non-thinking), and on par with it on the STEM-OCR subset.
  - The whole method was distilled into reusable workflows and tools that one person can rerun end to end.

</div>

<div class="proj-card" markdown="1">

### Project 4: Long-Video Understanding and Multi-Granularity Caption Pipeline

<span class="proj-meta">Huawei · 2025 - Present</span>

- **Situation:**
  When handling long-context video, foundation models suffer from broken global plots, confused character identities, drifting temporal grounding, and factual hallucination, and high-quality long-video training data is scarce.

- **Task:**
  Build an automatic pipeline that produces and verifies high-quality, multi-granularity long-video captions to support the evolution of the base model.

- **Action:**
  - **Semantic segmentation**: Generated temporal candidates with scenedetect and added timestamp fallback repair so that physical cuts align with semantic boundaries.
  - **Global memory**: Used sliding windows at the chunk level and fed all historical chunk summaries into the model to anchor long-range plots.
  - **Identity consistency**: Designed a Character Graph-based clustering and verification chain to keep character identities consistent across windows.
  - **Hallucination suppression**: Applied dense high-frame-rate sampling with a second hallucination check per chunk, and a dedicated fix for looping and repetition in long text.
  - **Production at scale**: Produced Event, Chapter, and Summary captions with a privately deployed Qwen-VL and vLLM acceleration.

- **Result:**
  - Delivered **300K** multi-granularity long-video captions.
  - In a 7B pilot, gained **3-4 points** over the SFT baseline on Video-MME (71.07, about +5% on the Long subset), MLVU, and LongVideoBench.

</div>

<div class="proj-card" markdown="1">

### Project 5: Xiaoyi Exhibition Guide: Activating World Knowledge in Streaming Video

<span class="proj-meta">Huawei · 2025 - Present</span>

- **Situation:**
  The base model already holds world knowledge about relics from static single images, but this knowledge is hard to trigger in streaming video interaction, showing clear cross-modal forgetting.

- **Task:**
  Transfer static knowledge to streaming video so that the model can recognize relics during an exhibition visit and proactively give a human-like guided tour.

- **Action:**
  - **Same-source scene mapping and style alignment**: Rewrote single-image relic QA into a tour-guide style and mapped it onto same-source video frames, linking single-frame knowledge to temporal interaction.
  - **Knowledge-injection streaming pipeline**: Built a streaming proactive-interaction data pipeline with injected world knowledge, and mixed or continued training on single-image and streaming data to reduce forgetting and hallucination.
  - **Aligned evaluation**: Built mutually aligned single-image knowledge and streaming proactive-interaction benchmarks from scratch.

- **Result:**
  - Validated the path from static knowledge injection to activation in dynamic scenes; the streaming model retains **81.1%** of single-frame image knowledge.

</div>

<div class="proj-card" markdown="1">

### Project 6: Machine Vision-based Micro Liquid Volume Measurement Technology and System

<span class="proj-meta">Tsinghua University · 2023 - 2025</span>

<div class="proj-gallery">
<img src="/images/platform.png" alt="Hardware System Schematic">
<img src="/images/vision_test.gif" alt="Host Computer Measurement Function Demo">
</div>

- **Situation:**  
  In environmental water quality online detection instruments, traditional micro-liquid volume measurement methods (~0.5 mL) are susceptible to bubbles, tube wall residue, and temperature fluctuations, resulting in unstable detection results with errors up to 10-20%. There is an urgent need for a high-precision, interference-resistant online measurement solution.

- **Task:**  
  As the graduate research project leader, I led the development of a non-contact micro-liquid volume measurement system based on machine vision. Core tasks included:
  - Designing and building a high-stability visual imaging hardware platform (camera + lens + light source)
  - Implementing robust segmentation and feature extraction of liquid segment images to overcome reflection and bubble interference
  - Building a quantitative mapping model from pixel length to actual volume, with a target accuracy of ≥98%
  - Developing supporting host computer software to achieve data acquisition, processing, and result display

- **Action:**  
  I independently completed system hardware/software development and algorithm research, with key work including:
  - Selecting industrial cameras and ring light sources, combined with FEP transparent tubing, to build an interference-resistant imaging environment
  - Implementing an **adaptive neighborhood weighted brightness analysis algorithm** based on OpenCV to stably extract liquid segment pixel lengths
  - Proposing two measurement methods:
    1. **Calibration fitting method**: Fitting the nonlinear relationship between pixels and volume through static weighing data
    2. **Physical mapping method**: Using homography matrices to convert image coordinates to physical dimensions, combined with pipe inner diameter to calculate volume
  - Exploring machine learning models integrated with physical priors to further enhance prediction robustness
  - Developing host computer software based on Python and PyQt5, integrating data acquisition, image processing, model calibration, and actual measurement functions

- **Result:**  
  - The system achieved **98.3% and 98.4%** measurement accuracy in complex industrial environments, outperforming traditional methods
  - Successfully resolved key interference issues such as bubbles, residue, and uneven lighting, demonstrating strong robustness
  - Project outcomes include **1 invention patent** (first inventor) and **1 Chinese core journal paper**
  - Significantly enhanced the ability to independently solve industrial-grade machine vision system engineering problems

</div>

<div class="proj-card" markdown="1">

### Project 7: 3D Hand Pose Estimation Based on RGBD/Stereo

<span class="proj-meta">Tencent Robotics X · 2024</span>

<div class="proj-gallery">
<img src="/images/Hand1.jpg" alt="Hand Pose Estimation Schematic - 1">
<img src="/images/Hand2.jpg" alt="Hand Pose Estimation Schematic - 2">
</div>

- **Situation:**  
  From a robot's perspective, there is a need to accurately estimate the absolute positions of hand joints in dynamic recognition distance scenarios of 0.5-2m, based on RGBD or stereo data input, with an error requirement of less than 5cm. The main challenges are handling hand self-occlusion and hand-object interaction occlusion, with a lack of real-world scenario data.

- **Task:**  
  Addressing these challenges, the project's main task was to develop a method capable of accurately estimating 3D hand pose to ensure MPJPE (Mean Per Joint Position Error) of less than 5cm.

- **Action:**  
  To solve this problem, three approaches were proposed:
  - **RGBD and VoxelPoseNet-based approach**: Surveyed relevant public datasets and selected NYU Hand as training data; adjusted the VoxelPoseNet model structure to adapt to hand pose estimation tasks; implemented model training and inference, including pre- and post-processing functions.
      - **Analysis**: Although MPJPE reached 30.824 mm on the NYU test set, performance was unsatisfactory in practical applications. The main reason was the significant deviation between depth map point clouds and prediction results. The model failed to adequately handle complex self-occlusion and hand-object interaction occlusion, resulting in insufficient generalization ability. Additionally, the domain gap between training dataset and real-world scenario depth maps limited performance without actual data fine-tuning.

  - **Deformable Detection DETR-based approach**: Directly outputting deviations in (x, y, z) directions relative to the root node from depth maps, including reproduction of this method, model training, and data pre- and post-processing.
      - **Analysis**: Final MPJPE was 14.204 mm on the NYU hand test set, an improvement over approach one. However, performance in real-world applications was still unsatisfactory, mainly due to large errors in the depth extraction step affecting baseline depth accuracy. Furthermore, distribution differences between training dataset and real-world scenario depth maps limited model generalization performance.

  - **Combined stereo triangulation and SOTA monocular RGB hand pose estimation model Hamer approach**: Using the ViT-H hand parametric model MANO for prediction, combined with stereo triangulation for absolute pose estimation. Used Fento Bolti's dataset to complete the overall process, achieving visualization effects of depth point clouds.
      - **Analysis**: This approach demonstrated the best generalization and prediction accuracy, successfully resolving issues present in the first two approaches. By combining stereo triangulation technology, not only was depth information accuracy significantly improved, but self-occlusion and hand-object interaction occlusion issues were effectively addressed, making this method particularly outstanding in complex scenarios. Although prediction results showed high matching with point cloud distributions, 1-2cm errors remained, providing direction for further optimization.

- **Result:**  
  Through multiple approaches and optimizations, it was ultimately found that combining stereo triangulation with SOTA monocular RGB hand pose estimation models showed the best prediction performance, effectively resolving generalization issues and achieving more accurate 3D hand pose estimation. Project outcomes not only enhanced understanding of hand pose estimation in complex scenarios but also provided valuable experience and technical accumulation for future research. Future work could consider further optimizing stereo triangulation algorithms to reduce prediction errors and exploring self-supervised learning methods to improve model robustness and generalization capabilities.

</div>

<div class="proj-card" markdown="1">

### Project 8: Automatic Video Editing System Based on LangChain and Large Language Models

<span class="proj-meta">Insta360 · 2023</span>

<div class="proj-gallery">
<img src="/images/LLM Clip.png" alt="Automatic Editing System Architecture">
<img src="/images/video understanding.png" alt="Video Structured Understanding Example">
</div>

- **Situation:**  
  Against the backdrop of growing demand for video content creation, users want to quickly filter, sort, and generate video clips that meet specific styles and storytelling requirements from large amounts of shooting footage. Automatic editing algorithms empowered by large models have emerged, aiming to achieve one-click video generation based on users' natural language descriptions (such as flash cuts, storytelling, and other editing style requirements).

- **Task:**  
  The goal was to develop a system based on large language models (LLM) and the LangChain framework that could filter and sequence the best combinations from a series of input video clips based on user-defined or specific requirements (such as flash cuts, storytelling, etc.) to automatically generate high-quality video edits that meet expected styles.

- **Action:**  
  During project implementation, I led and completed the following key technical work:
  - **Multimodal data analysis**: Applied Blip-image-captioning-base and Blip-VisualQuestionAnswering models to process video frames and generate structured image descriptions (captions) for each frame. Combined semantic segmentation with scoring algorithms to ensure accurate extraction and expression of key information.
  - **Intelligent video understanding and description generation**: Designed customized prompts to input video frame caption sequences into large language models, which would then infer and generate overall video semantic descriptions, covering time, scene, characters, emotions, and key events, enhancing contextual understanding.
  - **Advanced sorting and filtering mechanisms**: Based on LLM-generated video descriptions, built sorting logic that comprehensively considered event chronology, scene coherence, and character consistency to achieve intelligent sorting and structured organization of video clips.
  - **Model optimization**: Addressed compatibility issues across different LLM versions (from text-davinci-003 to GPT-3.5-turbo-instruct) by continuously optimizing prompt engineering and model calling strategies to ensure stable system output.

- **Result:**  
  - Successfully automated the entire functional pipeline, significantly improving video editing efficiency and quality.
  - Project outcomes were presented to the company CEO and received unanimous recognition from the technical team, validating the algorithm's feasibility and superiority in practical applications.
  - Fully demonstrated professional capabilities in multimodal data analysis, natural language processing (NLP), prompt engineering, LangChain applications, and machine learning system integration.

</div>

<div class="proj-card" markdown="1">

### Project 9: Visual Servo Control of Soft Robots in Complex Scenarios Based on Deep Learning

<span class="proj-meta">Chongqing University · 2022</span>

<div class="proj-gallery">
<img src="/images/DDPG.png" alt="DDPG Reinforcement Learning Online Training Process Design">
<img src="/images/robot servo.gif" alt="Visual Servo Control Demo">
</div>

- **Situation:**  
  Soft robots exhibit unique advantages in complex and variable environments due to their high compliance and adaptability. However, their highly nonlinear material characteristics make precise modeling and control particularly challenging. This project aims to develop an intelligent visual servo control system through deep learning technology to achieve precise control of soft robot end-effectors.

- **Task:**  
  As a core team member, I was primarily responsible for developing the visual servo control system for the soft robotic arm, with specific tasks including:
  - Designing and implementing a target detection algorithm based on the convolutional neural network SSD-MobileNet v2 for identifying and tracking target objects.
  - Developing a decision-making model based on the reinforcement learning DDPG algorithm to drive the soft robotic arm to complete visual servo tasks.
  - Building an experimental platform, integrating pneumatic soft robotic arms, electromagnetic proportional valves, and host computer control systems.
  - Completing the mapping from state space to operational space to ensure the soft robotic arm accurately aligns with target positions.

- **Action:**  
  During project implementation, the following key work was completed:
  - Established a dataset of 3000 images and trained a high-accuracy target detection model using the TensorFlow framework.
  - Optimized the DDPG algorithm for the dynamic characteristics of the soft robotic arm, achieving online learning and real-time decision-making.
  - Experimentally validated that the system achieved a 92% success rate in 100 consecutive tasks of moving target positions, with an average convergence time of 6.35 seconds and an average of 15.95 decision steps consumed.
  - Designed and built a pneumatic soft robotic arm experimental platform, thoroughly testing the technical parameters and interactions of various hardware components.

- **Result:**  
  - Successfully developed an efficient visual servo control system for soft robotic arms that performs excellently in complex environments.
  - The system can align the robotic arm end-effector with target objects within a limited time, with good convergence efficiency.
  - Improvement proposals were made for existing issues (such as target detection accuracy and reward function settings), laying the foundation for further system performance enhancement.
  - Won the Undergraduate Excellent Graduation Design Award

</div>


<span class='anchor' id='-lwzl'></span>

# 📝 Publications

### Papers
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">Optics and Precision Engineering 2025</div><img src='/images/Algorithm process.png' alt="sym" width="100%"></div></div>
<div class='paper-box-text' markdown="1">
- `Wang Hao`, Li Xinghui, Xiao Wei, et al. Machine vision-based volume measurement of micro-liquid in transparent hoses[J]. Optics and Precision Engineering, 2025,33(05):763-776. (Core journal)
[[Web]](https://kns.cnki.net/kcms2/article/abstract?v=liLFU49ICVv6jJCD0eIQSuXAIyB3Sp51wdG7mJ-nyE3PHj041eXQZwkBnFJTy-MeUnri7SK6LWF_LsUnyE8guJvkb7Q1wDjqkJXDcmg2i8E2hjxE1_R1rrtEXrJmSxiY58y-l73cwCXaBDFX9kil8ccOLejKTOIICLN7-iAW_DGyChbaWntvJw==&uniplatform=NZKPT&language=CHS) [[Preview]](https://github.com/warmheartHoward/warmheartHoward.github.io/tree/master/pdf) [[Download]]()  

</div>
</div>

### Patents

- Pang Shuyang, Yuan Yubo, Wang Jiajun, Jia Hongsheng, Mao Shangwei, Qin Sheng, `Wang Hao`, Liu Xuan, Xu Huaiwen, Du Yijie. A method, system, terminal and medium for determining raw material particle size. [[Web]](https://cprs.patentstar.com.cn/Search/Detail?ANE=7EBA9GFC9GCB9IIH5AEA8BGA9CGB9AIA9CFF9GAGBDHAEFHA)
- Pang Shuyang, `Wang Hao`, Yuan Yubo, Liu Bin, Jia Hongsheng, Mao Shangwei. A deep learning-based bar detection method, device and equipment.[[Web]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn)
- Pang Shuyang, Liu Yujia, Ran Xingming, Liu Rui, Zhang Chaojie, Jia Hongsheng, Mao Shangwei, `Wang Hao`, Du Yijie. A steel coil spacing detection method, system, medium and electronic terminal. [[Web]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- Pang Shuyang, Yu Yunfei, Jia Hongsheng, Mao Shangwei, `Wang Hao`, Liu Xuan. A floc image processing method, system, medium and electronic device. [[Web]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- Pang Shuyang, Liu Rui, Zhang Chaojie, `Wang Hao`, Jia Hongsheng, Mao Shangwei. A deep learning-based steel pile recognition method. [[Web]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- `Wang Hao`, Xiao Wei, Li Xinghui. A visual-based liquid volume metering method and system.

<span class='anchor' id='-ryjx'></span>

# 🏅 Awards
- Received the Huawei department `2012 Star` award and a `Xiaoyi Letter of Appreciation` (streaming-video proactive interaction project)
- *2025.05* Won the `Second Prize` in the 10th Professional Practice of Tsinghua Shenzhen International Graduate School
- *2023.10* Won the `Silver Award Team` in the 2023 Tsinghua University Student Social Practice  
- *2022.06* Won the `Excellent Graduation Design` of Chongqing University Undergraduate Graduation Design
- *2021.06* Won the `Good Completion` of the 5th Chongqing University Student Innovation Training Program 
- *2021.03* Won the `Third Prize` in the 11th MathorCup University Mathematical Modeling Challenge Graduate Group 
- *2019.08* Won the `Intern Star` of Chongqing University-UC Joint College

<span class='anchor' id='-xshy'></span>

# 🏛️ Academic Conferences
- *2024.10*, Wang H, Cao F, Xiao W, et al. Machine vision-based automatic liquid dispensing metering technology and system for microfluids[C]//Optical Metrology and Inspection for Industrial Applications XI. SPIE, 2024, 13241: 472-484.

<span class='anchor' id='-gzsx'></span>

# 💻 Work Experience
- *2025.09 - Present*, Huawei Technologies Co., Ltd. - 2012 Laboratories - Foundation Model Department - Multimodal Model Lab - AI Algorithm Engineer, Shenzhen, Guangdong
- *2024.05 - 2024.09*, Tencent Technology Co., Ltd. - TEG Technology Engineering Group - Robotics X/System Center - Perception Algorithm Intern, Shenzhen, Guangdong
- *2024.01 - 2024.04*, Anker Innovation Technology Co., Ltd. - Advanced Robotics Research Institute - Algorithm Intern, Shenzhen, Guangdong
- *2023.07 - 2023.12*, Tsinghua University Yunjing Technology Practice Base - Research Project Leader, Guilin, Guangxi
- *2023.03 - 2023.06*, Insta360 Innovation Technology Co., Ltd. - Research Institute - Machine Learning Group 2 - Deep Learning Algorithm Intern, Shenzhen, Guangdong
- *2021.01 - 2021.08*, Chongqing University-UC Joint College - US Teaching Assistant, Chongqing
- *2021.01 - 2022.04*, State Key Laboratory of Mechanical Transmission, Chongqing University - Manufacturing Engineering Research Institute - Research Intern, Chongqing
- *2019.01 - 2020.08*, MCC SEDI Chongqing Information Technology Co., Ltd. - Big Data and Artificial Intelligence Department - Machine Vision Group - Image Algorithm Engineer, Chongqing