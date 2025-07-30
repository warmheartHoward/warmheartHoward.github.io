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


我目前在华为诺亚方舟实验室工作，工作岗位为AI工程师，主要的研究方向为自动驾驶和多模态大模型。我研究生毕业于清华大学深圳国际研究生院，所学专业为电子信息，主要的研究方向为视觉测量；本科就读于重庆大学，专业为机械设计制造及其自动化。我有着丰富的实习与工程落地经验，发表过中文核心期刊与多项专利。

<div class="tags">
  <span class="tag">国际化人才</span>
  <span class="tag">多学科融合交叉</span>
  <span class="tag">实习项目经历出众</span>
</div>

我的研究领域包括：

- 多模态大模型
- 自动驾驶
- 机器视觉
- 仪器仪表
  
<span class='anchor' id='-xl'></span>

# 🎓 学历
- *2022.09 - 2025.06*, <a href="https://www.sigs.tsinghua.edu.cn/"><img class="svg" src="/images/Tsinghua.png" width="23pt"></a> 清华大学，清华大学深圳国际研究生院, 电子信息（智能制造）, 广东深圳, 工学硕士学位(推荐免试)。 
- *2017.09 - 2022.06*, <a href="https://www.cqu.edu.cn/"><img class="svg" src="/images/Chongqing.png" width="23pt"></a> 重庆大学, 重庆大学-辛辛那提大学联合学院, 机械设计制作机器设计及自动化, 重庆, 工学学士学位。
 
<span class='anchor' id='-xmjl'></span>

# 🧭 项目经历

<div class="paper-box">
  <div class="paper-box-image">
    <div>
      <div class="badge">项目名称 2025</div>
      <!-- <video src="" autoplay loop muted playsinline style="max-width: 100%; border-radius: 8px;"></video> -->
      <img src="/images/vision_test.gif" alt="项目演示" style="max-width: 100%; border-radius: 8px;">
    </div>
  </div>
  <div class="paper-box-text" markdown="1">

  - **Situation:** 在水质在线检测仪器领域，精确计量进入反应容器的微液量至关重要。然而，传统液体体积计量方法受到气泡与残留在管壁上的液珠影响，误差范围在10-20%之间。因此，本课题的目标是基于机器视觉技术，实现微液量体积的精准检测。

  - **Task:** 作为研究生课题负责人，我承担了整体课题的软硬件开发与功能算法研究，具体任务包括：
      * 硬件实验平台的设计、仿真与搭建：选型相机、镜头和光源，设计计算摄像指标，并进行实物搭建。
      * 基于视觉的进液运动反馈控制算法实现：确保系统能够实时监测并调整进液过程。
      * 提取采集图像中液体计量的视觉特征：通过自适应邻域加权亮度分析算法，稳定提取液段像素长度，排除气泡干扰、光照不均及管壁反光等不利因素的影响。
      * 基于所提取的视觉特征与万分之一天平所称量的真实值进行线性回归拟合：获取标定曲线，或基于单应矩阵的图像特征坐标变换测量法，将像素坐标映射至物理空间并结合管道内径实现体积计算。

  - **Action:** 我独自完成了整个项目的研发工作，具体行动如下：
      * 设计并搭建了微液量进液视觉计量硬件系统，包括相机、镜头和光源的选型及计算摄像指标设计与硬件自动化控制。
      * 利用OpenCV和机器学习方法实现了图像计量特征如液段像素长度以及残留液滴特征的提取。
      * 分别基于标定测量法、物理建模直接测量法和基于物理机理先验的机器学习预测算法实现了微液量的计量，最终达到99%的计量精度。
      * 在此过程中，显著提升了个人独立解决实际工业机器视觉工程问题的能力，并产出一篇发明专利与一篇中文核心期刊。

  - **Result:** 根据我提出的整套技术方案，液体计量精度达到了98.4%，有效解决了现有环保水质检测仪器微液量进液计量受到气泡与残液干扰、传统方法精度低、稳定性差的问题。实验结果表明，在复杂环境中，两种计量策略的精度分别达到98.3%和98.4%，能够有效满足工业现场对微量液体体积快速测量的需求，具有显著的应用价值和推广潜力。
  
  </div>
</div>



<span class='anchor' id='-lwzl'></span>


# 📝 论文与专利

### 论文
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">光学精密工程 2025</div><img src='images/整体算法流程.png' alt="sym" width="100%"></div></div>
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
- *2024.05 - 2024.09*, 腾讯科技有限公司-TEG技术工程事业群-Robotics X/系统中心-感知算法实习生, 广东深圳
- *2024.01 - 2024.04*, Anker创新科技股份有限公司-先进机器人研究院-算法实习生, 广东深圳
- *2023.07 - 2023.12*, 清华大学云璟科技实践基地-科研项目负责人， 广西桂林
- *2023.03 - 2023.06*, Insta360影石创新科技股份有限公司-研究院-机器学习二组-深度学习算法实习生, 广东深圳
- *2021.01 - 2021.08*，重庆大学-UC联合学院-美方助教, 重庆
- *2021.01 - 2022.04*, 重庆大学机械传动国家重点实验室制造工程研究所-科研实习, 重庆
- *2019.01 - 2020.08*, 中冶赛迪重庆信息技术有限公司-大数据与人工智能部门-机器视觉小组-图像算法工程师, 重庆