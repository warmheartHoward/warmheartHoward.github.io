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

### 项目一：基于机器视觉的微量液体体积测量技术与系统

<div class="paper-box">
  <div class="paper-box-image">
    <div class="flex-container">
      <img src="/images/platform.png" alt="硬件系统示意图" class="flex-item">
      <img src="/images/vision_test.gif" alt="上位机测量功能演示" class="flex-item">
    </div>
    <div class="badge">2025</div>
  </div>
  <div class="paper-box-text" markdown="1">

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
</div>

---


### 项目二：基于深度学习的复杂场景下软体机器人视觉伺服控制

<div class="paper-box">
  <div class="paper-box-image">
    <div class="flex-container">
      <img src="/images/soft_robot_arm.png" alt="软体机械臂系统示意图" class="flex-item">
      <img src="/images/vision_servo.gif" alt="视觉伺服控制演示" class="flex-item">
    </div>
    <div class="badge">2022</div>
  </div>
  <div class="paper-box-text" markdown="1">

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
    - 项目成果包括发表于相关领域国际会议或期刊论文，以及多项技术创新点。

  </div>
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