---
permalink: /
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


我目前就职于华为技术有限公司 2012 实验室基础大模型部多模态模型实验室，任 AI 算法工程师，主要负责盘古多模态大模型（VL）与小艺的视频理解、世界知识及 OCR 推理能力建设。我研究生毕业于清华大学深圳国际研究生院，所学专业为电子信息，主要的研究方向为视觉测量；本科就读于重庆大学，专业为机械设计制造及其自动化。我有着丰富的实习与工程落地经验，发表过中文核心期刊与多项专利。

<div class="tags">
  <span class="tag">国际化人才</span>
  <span class="tag">多学科融合交叉</span>
  <span class="tag">实习项目经历出众</span>
</div>

我的研究领域包括：

- 多模态大模型（VLM/MLLM）数据与训练
- 流视频主动交互与长视频理解
- 世界知识注入、OCR 与复杂推理
- 机器视觉与视觉测量
  
<span class='anchor' id='-xl'></span>

# 🎓 学历
- *2022.09 - 2025.06*, <a href="https://www.sigs.tsinghua.edu.cn/"><img class="svg" src="/images/Tsinghua.png" width="23pt"></a> 清华大学，清华大学深圳国际研究生院, 电子信息（智能制造）, 广东深圳, 工学硕士学位(推荐免试)。 
- *2017.09 - 2022.06*, <a href="https://www.cqu.edu.cn/"><img class="svg" src="/images/Chongqing.png" width="23pt"></a> 重庆大学, 重庆大学-辛辛那提大学联合学院, 机械设计制造及其自动化, 重庆, 工学学士学位。
 
<span class='anchor' id='-xmjl'></span>

# 🧭 项目经历

<div class="proj-card" markdown="1">

### 项目一 小艺流视频主动交互（盲人导航与避障）

<span class="proj-meta">华为 · 2025 - 至今</span>

- **Situation:**
  盲人导航与避障等场景要求模型在连续视频流中及时发现障碍物并主动提醒。原有方案基于单帧触发、被动应答，存在明显的时延与滞后，且难以保持时序上下文的连贯。

- **Task:**
  从 0 到 1 构建流视频主动交互体系，使多模态大模型能够在开放集环境下的时序视频流中主动干预、及时预警并播报，覆盖数据、训练、推理与评测全链路。

- **Action:**
  - **主动触发机制**：调研 VideoLLM-online 等流式框架后，将主动交互建模为特殊 Token 的二分类预测任务——在图像右分隔符后预测静默符或 Assistant 唤醒符，使模型具备主动干预与打断能力。
  - **流式数据引擎**：自研基于 DenseCaption2PO 的流式数据合成与风格改写 Pipeline，并设计基于 Grounding DINO 的人工标注闭环，累计交付 **50 万条**精标数据。
  - **状态化流式推理**：基于 PyTorch 独立开发 Stateful Inference 管线，设计显存友好的历史 Chunk Summary 流转机制，优化 KV-Cache 状态管理与张量拼接，降低长时流式解码的显存与延迟开销。
  - **训练策略**：采用“带噪数据预训练 + 精标数据微调”的两阶段训练，并针对触发正负样本严重失衡引入 Sample Balance Loss。
  - **评测与诊断**：独立搭建开放集分类评测体系与可视化诊断工具，用于定位数据分布、触发时机与场景泛化问题。

- **Result:**
  - 室内外障碍物等重点场景中，预警 Precision 达 **92.4%**、Recall 达 **92.9%**，较原单帧触发基线分别提升 2.43 与 3.5 个百分点。
  - 项目获部门 **“2012 之星”** 及 **“小艺感谢信”**。

</div>

<div class="proj-card" markdown="1">

### 项目二 盘古 VL（92B）文物世界知识构建

<span class="proj-meta">华为 · 2025 - 至今</span>

- **Situation:**
  基础大模型在文物与文化遗产等垂直领域存在认知盲区，容易产生事实性幻觉，无法支撑小艺在相关场景下的知识问答。

- **Task:**
  为 92B 模型构建文物垂域的世界知识数据体系与专属评测基准，分别满足退火阶段对知识密度、SFT 阶段对指令多样性的不同需求。

- **Action:**
  - **知识体系**：从零构建文物专属标签库与多层级分类体系，对数字博物馆及开源文物数据进行拓源、清洗与知识组织。
  - **退火阶段知识注入**：结合外部搜索与 ReAct 范式搭建高并发知识打标链路，生产 **200 万条**结构化、高密度的 Caption。
  - **SFT 阶段数据合成**：设计“裸蒸（Raw Distillation）+ 精炼（Refine）+ 置信度过滤”的数据策略，突破单模板限制，生产 **1,000 万条** QA 与图文交织数据，有效抑制蒸馏幻觉。
  - **评测基准**：结合标签体系构建小艺文物业务 Benchmark，覆盖知识准确性、指令遵循与场景泛化。

- **Result:**
  - 累计交付 **1,200 万条** Caption 与 QA 数据。
  - 92B 模型在小艺文物评测集上领先 Qwen3.5-122B-A10B **14.83 分**，公开基准 WorldVQA 的 Culture 子集提升 **13 分**。

</div>

<div class="proj-card" markdown="1">

### 项目三 盘古 VL v2.1 OCR 与复杂推理数据攻关

<span class="proj-meta">华为 · 2025 - 至今</span>

- **Situation:**
  面向盘古 VL v2.1 的代际演进，小艺冒烟集覆盖卡证、票据、表格等真实场景，对模型的 OCR 解析与复杂推理（如多步数值计算）要求很高。现成数据在“读得准”与“想得对”两方面供给并不均衡，短板往往藏在没人注意到的能力格子里。

- **Task:**
  负责 OCR 与 STEM 相关能力的数据建设：不靠盲目堆量，而是先量出短板、再定向造数据、最后用评测回头校正配比，并支撑 Stage 2、Midtrain 到 32K / 128K / 512K 长序列的连续训练。

- **Action:**
  - **数据画像**：完成 MD5 / Embedding / pHash 大规模去重；设计领域、体裁、能力、难度、质量五维画像体系，以 VLM 打标并训练基于图文 Embedding 的轻量分类器，将画像铺到 **100M+** 全量数据。
  - **短板定位**：把逐题评测结果映射到同一套画像格子，结合“训练语料稀缺性”区分“真缺数据”与“质量或方法问题”，据此从存量召回、互联网检索与采购定向补源。
  - **推理 QA 生产线**：搭建由“能力描述 + 种子问题 + 权重”驱动的可插拔生产线，包含能力加权出题、多风格作答、13 维质检与盲审改写，并引入多模型分工与快慢思考数据；Stage 2 产出约 1,200 万条简单 QA，Midtrain 放量至约 3,500 万条 QA。
  - **先验证后放量**：先以 50 万规模 pilot 验证方法有效（约 +9 分），再逐步放量。
  - **长序列配比修复**：定位到 128K 训练掉点的原因——重采样使慢思考占比由 64.1% 被稀释到 23.7%；设计“按长度删除、按画像均衡补充”的重采样方案并用官方口径全量实测 token，128K / 512K 的慢思考占比分别恢复至 64.9% / 70.0%。

- **Result:**
  - mid-train 模型在小艺冒烟集（582 题）总分达 **64.09%**，较 Stage 2 阶段提升 12.5 个点。
  - OCR 子集 85.12%，较 Qwen3.8-27B（非思考）高 **4.95 分**；STEM-OCR 子集与其持平。
  - 整套方法沉淀为可复用的流程与工具，可由单人独立重跑。

</div>

<div class="proj-card" markdown="1">

### 项目四 长视频理解与多粒度 Caption 管线

<span class="proj-meta">华为 · 2025 - 至今</span>

- **Situation:**
  基础大模型在处理长上下文视频时，面临全局剧情断层、角色身份混淆、时序定位偏移以及事实幻觉等问题，缺少高质量的长视频训练数据。

- **Task:**
  搭建高质量、多粒度的长视频 Caption 自动生产与校验管线，支撑底座模型长视频理解能力的演进。

- **Action:**
  - **语义切分**：结合 scenedetect 生成时间候选，并加入时间戳兜底修复，使物理切分对齐语义边界。
  - **全局记忆**：在 Chunk 级理解中采用滑动窗口，并将全部历史 Chunk Summary 汇总输入模型，锚定长程剧情。
  - **人物一致性**：设计基于人物图谱（Character Graph）的聚类与校验链路，约束跨窗口的角色身份一致。
  - **幻觉抑制**：在 Chunk 粒度进行高帧率密集采样与二次幻觉校验，并对长文本的循环重复问题做专项修复。
  - **规模化生产**：基于私有化 Qwen-VL 与 vLLM 推理加速，生产 Event、Chapter、Summary 三个粒度的 Caption。

- **Result:**
  - 交付 **30 万条**多粒度长视频 Caption。
  - 7B 模型先导实验中，较 SFT 基线在 Video-MME（71.07，Long 子集约 +5%）、MLVU、LongVideoBench 等公开榜单提升 **3-4 个点**。

</div>

<div class="proj-card" markdown="1">

### 项目五 小艺逛展：流视频世界知识激发

<span class="proj-meta">华为 · 2025 - 至今</span>

- **Situation:**
  模型底座已具备静态单图的文物世界知识，但在流式动态视频交互场景中难以被有效触发，存在明显的跨模态遗忘。

- **Task:**
  解决静态知识向动态流式视频迁移的难题，使模型能在逛展场景中识别文物并主动进行拟人化导览。

- **Action:**
  - **同源场景映射与风格对齐**：将单图文物知识 QA 重构为贴合逛展场景的导览风格，并映射至与之同源的视频帧，建立从单帧知识到时序交互的对应关系。
  - **知识注入流式数据管线**：搭建注入世界知识的流式主动交互数据生产管线，采用单图知识数据与流式数据混训 / 续训，缓解知识遗忘与交互幻觉。
  - **对齐评测**：从零构建相互对齐的单图世界知识 Benchmark 与流式主动交互 Benchmark。

- **Result:**
  - 验证了“静态知识注入—动态场景激发”的技术链路；流式模型对单帧图像知识的继承率达 **81.1%**。

</div>

<div class="proj-card" markdown="1">

### 项目六 基于机器视觉的微量液体体积测量技术与系统

<span class="proj-meta">清华大学 · 2023 - 2025</span>

<div class="proj-gallery">
<img src="/images/platform.png" alt="硬件系统示意图">
<img src="/images/vision_test.gif" alt="上位机测量功能演示">
</div>

- **Situation:**  
  在环保水质在线检测仪器中，传统微液量（~0.5 mL）计量方法易受气泡、管壁残液和温度波动影响，误差高达 10–20%，导致检测结果不稳定。亟需一种高精度、抗干扰的在线计量方案。

- **Task:**  
  作为研究生课题负责人，主导开发基于机器视觉的非接触式微液量体积测量系统。核心任务包括：
  - 设计并搭建高稳定性视觉成像硬件平台（相机 + 镜头 + 光源）
  - 实现液段图像的鲁棒分割与特征提取，克服反光、气泡干扰
  - 构建从像素长度到实际体积的定量映射模型，目标精度 ≥98%
  - 开发配套的上位机软件，实现数据采集、处理及结果显示

- **Action:**  
  独立完成系统软硬件开发与算法研究，关键工作包括：
  - 选用工业相机与环形光源，结合 FEP 透明软管，构建抗干扰成像环境
  - 基于 OpenCV 实现 **自适应邻域加权亮度分析算法**，稳定提取液段像素长度
  - 提出两种计量方法：
    1. **标定拟合法**：通过静力称重数据拟合像素-体积非线性关系
    2. **物理映射法**：利用单应矩阵将图像坐标转换为物理尺寸，结合管道内径计算体积
  - 探索融合物理先验的机器学习模型，进一步提升预测鲁棒性
  - 开发基于 Python 和 PyQt5 的上位机软件，集成数据采集、图像处理、模型标定和实际测量功能

- **Result:**  
  - 系统在复杂工业环境下实现 **98.3% 与 98.4%** 的计量精度，优于传统方法
  - 成功解决气泡、残液、光照不均等关键干扰问题，具备强鲁棒性
  - 项目成果产出 **1项发明专利**（第一发明人）与 **1篇中文核心期刊论文**
  - 显著提升独立解决工业级机器视觉系统工程问题的能力

</div>

<div class="proj-card" markdown="1">

### 项目七 基于RGBD/双目的人手关节3D姿态估计

<span class="proj-meta">腾讯 Robotics X · 2024</span>

<div class="proj-gallery">
<img src="/images/Hand1.jpg" alt="人手姿态估计示意图-1">
<img src="/images/Hand2.jpg" alt="人手姿态估计示意图-2">
</div>

- **Situation:**  
  在机器人视角下，需要在0.5-2m的动态识别距离场景中，基于RGBD或双目数据输入，实现对人手关节绝对位置的精确估计，误差要求小于5cm。主要难点在于处理人手自遮挡与手物交互遮挡的情况，并且缺乏实际场景数据。

- **Task:**  
  针对上述挑战，项目的主要任务是开发一种能够准确估计人手关节3D姿态的方法，确保MPJPE（平均关节位置误差）小于5cm。

- **Action:**  
  为解决这一问题，提出了三种方案：
  - **基于RGBD与VoxelPoseNet的方案**：调研相关公开数据集，选择NYU Hand作为训练数据；调整VoxelPoseNet模型结构以适应人手姿态估计任务；实现模型的训练与推理，包括前后处理功能的实现。
      - **分析**：尽管在NYU测试集上的MPJPE达到了30.824 mm，但在实际应用中表现不佳。主要原因在于深度图点云与预测结果之间的偏差较大，模型未能充分处理复杂的自遮挡和手物交互遮挡问题，导致其泛化能力不足。此外，训练数据集与实际场景所采集的数据深度图存在Domain Gap，没有实际数据微调的情况下，很难实现较好的泛化效果。

  - **基于Deformable Detection DETR的方案**：直接从深度图输出其他关节相对于根节点(x, y, z)方向上的偏差，具体工作包括对该方法的复现、模型训练及数据前后处理等。
      - **分析**：最终在NYU hand测试集上的MPJPE为14.204 mm，较方案一有所提升。然而，在实际应用场景中的表现仍不理想，主要是由于深度提取步骤带来的误差较大，影响了基准深度的准确性。此外，训练数据集与实际场景深度图的分布差异进一步限制了模型的泛化性能。

  - **结合双目三角化与SOTA单目RGB人手姿态估计模型Hamer的方案**：利用ViT-H的人手参数化模型MANO进行预测，结合双目三角化对绝对位姿进行估计。使用Fento Bolti的数据集完成整体流程，实现了深度点云的可视化效果。
      - **分析**：该方案展示了最佳的泛化性和预测准确性，成功解决了前两种方案中存在的问题。通过结合双目三角化技术，不仅显著提升了深度信息的准确性，还有效应对了自遮挡和手物交互遮挡的问题，使得该方法在复杂场景下的表现尤为突出。尽管预测结果与点云分布匹配性较高，但仍存在1-2cm的误差，为进一步优化提供了方向。

- **Result:**  
  经过多种方案的尝试与优化，最终发现结合双目三角化与SOTA单目RGB人手姿态估计模型的方法表现出最佳的预测效果，有效解决了泛化性问题，实现了更准确的人手关节3D姿态估计。项目成果不仅提升了对复杂场景下人手姿态估计的理解，还为后续研究提供了宝贵的经验和技术积累。未来的工作可以考虑进一步优化双目三角化算法，减少预测误差，并探索自监督学习方法来提高模型的鲁棒性和泛化能力。

</div>

<div class="proj-card" markdown="1">

### 项目八 基于LangChain与大语言模型的自动视频剪辑系统

<span class="proj-meta">Insta360 · 2023</span>

<div class="proj-gallery">
<img src="/images/LLM Clip.png" alt="自动剪辑系统架构图">
<img src="/images/video understanding.png" alt="视频结构化理解示例">
</div>

- **Situation:**  
  在当前视频内容创作需求日益增长的背景下，用户希望快速从大量拍摄素材中筛选、排序并生成符合特定风格和故事性的视频片段。基于大模型赋能的自动剪辑算法应运而生，旨在根据用户的自然语言描述（如快闪、故事性等剪辑风格要求），实现一键成片的功能。

- **Task:**  
  目标是开发一套基于大语言模型（LLM）和LangChain框架的系统，能够根据用户定义或特定要求（如快闪、故事性等），从一系列输入视频片段中筛选并排序出最佳组合，以自动生成符合预期风格的高质量视频剪辑。

- **Action:**  
  在项目实施过程中，主导并完成了以下关键技术工作：
  - **多模态数据分析**：应用 Blip-image-captioning-base 和 Blip-VisualQuestionAnswering 模型对视频进行抽帧处理，并为每一帧生成结构化的图像描述（caption）。结合语义分割与评分算法，确保关键信息的准确提取与表达。
  - **智能视频理解与描述生成**：设计定制化 Prompt，将视频帧的 caption 序列输入大语言模型，由其推理生成整体视频语义描述，涵盖时间、场景、人物、情绪与关键事件，提升上下文理解能力。
  - **高级排序与筛选机制**：基于LLM生成的视频描述，构建排序逻辑，综合考虑事件时序、场景连贯性与角色一致性，实现视频片段的智能化排序与结构化组织。
  - **模型优化**：针对不同LLM版本（如从 text-davinci-003 到 GPT-3.5-turbo-instruct）的兼容性问题，持续优化 Prompt 工程与模型调用策略，保障系统稳定输出。

- **Result:**  
  - 成功实现了整个功能 pipeline 的自动化，显著提升了视频剪辑的效率和质量。
  - 项目成果面向公司CEO进行了汇报，并获得了技术团队的一致认可，验证了该算法在实际应用中的可行性与优越性。
  - 充分展现了在多模态数据分析、自然语言处理（NLP）、Prompt工程、LangChain应用及机器学习系统集成方面的专业能力。

</div>

<div class="proj-card" markdown="1">

### 项目九 基于深度学习的复杂场景下软体机器人视觉伺服控制

<span class="proj-meta">重庆大学 · 2022</span>

<div class="proj-gallery">
<img src="/images/DDPG.png" alt="DDPG强化学习在线训练流程设计">
<img src="/images/robot servo.gif" alt="视觉伺服控制演示">
</div>

- **Situation:**  
  软体机器人因其高柔顺性和适应性在复杂和多变环境中展现出独特优势。然而，其高度非线性的材料特性使得精准建模与控制变得尤为困难。本项目旨在通过深度学习技术，开发一种智能视觉伺服控制系统，以实现对软体机器人末端执行器的精确控制。

- **Task:**  
  作为项目核心成员，主要负责软体机械臂视觉伺服控制系统的开发工作，具体任务包括：
  - 设计并实现基于卷积神经网络 SSD-MobileNet v2 的目标检测算法，用于识别和跟踪目标物体。
  - 开发基于强化学习 DDPG 算法的决策模型，驱动软体机械臂完成视觉伺服任务。
  - 构建实验平台，集成气动软体机械臂、电磁比例阀及上位机控制系统。
  - 完成从状态空间到操作空间的映射，确保软体机械臂能够准确对准目标位置。

- **Action:**  
  在项目的实施过程中，完成了以下关键工作：
  - 建立了一个包含3000张图像的数据集，并利用Tensorflow框架训练了高精度的目标检测模型。
  - 针对软体机械臂的动态特性，优化DDPG算法，实现了在线学习和实时决策。
  - 实验验证了该系统在连续100次移动目标位置的任务中，有92%的成功率，平均收敛时间为6.35秒，平均消耗的决策步数为15.95步。
  - 设计并搭建了气动软体机械臂实验平台，详细测试了各个硬件组件的技术参数及其相互作用。

- **Result:**  
  - 成功开发了一套高效的软体机械臂视觉伺服控制系统，在复杂环境下表现出色。
  - 该系统能够在有限时间内使机械臂末端对准目标物体，且具有良好的收敛效率。
  - 针对存在的问题（如目标检测精度、奖励函数设置等），提出了改进方案，为进一步提升系统性能奠定了基础。
  - 获得本科优秀毕业设计

</div>


<span class='anchor' id='-lwzl'></span>


# 📝 论文与专利

### 论文
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">光学精密工程 2025</div><img src='/images/Algorithm process.png' alt="sym" width="100%"></div></div>
<div class='paper-box-text' markdown="1">
- `王昊`, 李星辉,肖巍等.基于机器视觉的透明软管内微量液体体积测量[J].光学精密工程, 2025,33(05):763-776.（核心期刊）
[[网页]](https://kns.cnki.net/kcms2/article/abstract?v=liLFU49ICVv6jJCD0eIQSuXAIyB3Sp51wdG7mJ-nyE3PHj041eXQZwkBnFJTy-MeUnri7SK6LWF_LsUnyE8guJvkb7Q1wDjqkJXDcmg2i8E2hjxE1_R1rrtEXrJmSxiY58y-l73cwCXaBDFX9kil8ccOLejKTOIICLN7-iAW_DGyChbaWntvJw==&uniplatform=NZKPT&language=CHS) [[预览]](https://github.com/warmheartHoward/warmheartHoward.github.io/tree/master/pdf) [[下载]]()  

</div>
</div>

### 专利

- 庞殊杨, 袁钰博, 王嘉骏, 贾鸿盛, 毛尚伟, 秦盛, `王昊`, 刘璇, 许怀文, 杜一杰. 一种原料粒度确定方法、系统、终端及介质. [[网页]](https://cprs.patentstar.com.cn/Search/Detail?ANE=7EBA9GFC9GCB9IIH5AEA8BGA9CGB9AIA9CFF9GAGBDHAEFHA)
- 庞殊杨, `王昊`, 袁钰博, 刘斌, 贾鸿盛, 毛尚伟. 一种基于深度学习的棒材检测方法、装置及设备.[[网页]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn)
- 庞殊杨, 刘雨佳, 冉星明, 刘睿, 张超杰, 贾鸿盛, 毛尚伟, `王昊`, 杜一杰. 一种钢卷间距检测方法、系统、介质及电子终端. [[网页]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- 庞殊杨, 余云飞, 贾鸿盛, 毛尚伟, `王昊`, 刘璇. 一种矾花图像处理方法、系统、介质及电子设备. [[网页]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- 庞殊杨, 刘睿, 张超杰, `王昊`, 贾鸿盛, 毛尚伟. 基于深度学习的堆钢识别方法. [[网页]](https://cprs.patentstar.com.cn/Search/ResultList?CurrentQuery=44CK5LiA56eN5Y6f5paZ57KS5bqm56Gu5a6a5pa55rOV44CB57O757uf44CB57uI56uv5Y+K5LuL6LSo44CLL1lZ&type=cn) 
- `王昊`, 肖巍, 李星辉. 一种基于视觉的液量进液体积计量方法与系统.

<span class='anchor' id='-ryjx'></span>

# 🏅 荣誉奖项
- 获得 华为部门 `2012之星` 及 `小艺感谢信`（流视频主动交互项目）
- *2025.05* 获得 清华大学深圳国际研究生院第十届专业实践`二等奖`
- *2023.10* 获得 2023年清华大学学生社会实践 `银奖团队`  
- *2022.06* 获得 重庆大学本科毕业设计 `优秀毕业设计`
- *2021.06* 获得 第五届重庆市大学生创新训练项目 `良好结题` 
- *2021.03* 获得 第十一届MathorCup高校数学建模挑战赛研究生组  `三等奖` 
- *2019.08* 获得 重庆大学-UC联合学院 `实习之星`

<span class='anchor' id='-xshy'></span>

# 🏛️ 学术会议
- *2024.10*, Wang H, Cao F, Xiao W, et al. Machine vision-based automatic liquid dispensing metering technology and system for microfluids[C]//Optical Metrology and Inspection for Industrial Applications XI. SPIE, 2024, 13241: 472-484.


<span class='anchor' id='-gzsx'></span>

# 💻 工作实习
- *2025.09 - 至今*, 华为技术有限公司-2012实验室-基础大模型部-多模态模型实验室-AI算法工程师, 广东深圳
- *2024.05 - 2024.09*, 腾讯科技有限公司-TEG技术工程事业群-Robotics X/系统中心-感知算法实习生, 广东深圳
- *2024.01 - 2024.04*, Anker创新科技股份有限公司-先进机器人研究院-算法实习生, 广东深圳
- *2023.07 - 2023.12*, 清华大学云璟科技实践基地-科研项目负责人， 广西桂林
- *2023.03 - 2023.06*, Insta360影石创新科技股份有限公司-研究院-机器学习二组-深度学习算法实习生, 广东深圳
- *2021.01 - 2021.08*，重庆大学-UC联合学院-美方助教, 重庆
- *2021.01 - 2022.04*, 重庆大学机械传动国家重点实验室制造工程研究所-科研实习, 重庆
- *2019.01 - 2020.08*, 中冶赛迪重庆信息技术有限公司-大数据与人工智能部门-机器视觉小组-图像算法工程师, 重庆