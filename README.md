#### 0712
- 上午1：
- 计图深度学习框架及其应用
  1. 英文名：jittor
  2. 提出元算子（18个）
        - 元算子具有反向穿鼻闭包的特性
        - 重要元算子：
            - 重索引算子 1->n
            - 重索引化简算子 n->1
            - 元素级算子 1->1
  3. 优势
        - 元算子融合
        - 统一计算图
        - 动态切分->静态子图
  4. 特色
        - 动态编辑
        - 统一内存
        - 模型转换
        - 分布式
        - 骨干网络
        - 可微渲染库JRender
   5. 缺点
        - 生态不完善（windows下无法直接使用）
        - bug较多
****
- 上午2：
- 深度几何的学习表示
    1.  各类深度几何表示
        - Multiview
        - Voxel
        - Point Cloud
        - Mesh
    2. 点云分割与识别-VV-Net
        - 先驱工作
            - PointNet
        - 核心思想
            - RBF-VAE编码点云顶点
            - 群卷积消除点云旋转影响
    3. 网格分析与识别-LaplaceNet
        - 核心思想
            -  基于拉普拉斯矩阵的多层级区域聚类
            -  相关性网络提取全局顶点
    4. 无监督三维模型对称性分析-RPS-Net
    5. 三维深度生成模型- SDM-Net||DSG-Net
    6. 高质量纹理模型生成-TM-Net
        - 核心思想
            - 通过变形刻画几何细节
            - 使用有向支撑图来编码结构 
    7. 三维动态细节合成-DeformTransformer
    8. 智能人脸画板-DeepFaceDrawing
        - 核心思想
            - 局部细节-全局结构
            - 流形投影
***
- 下午1
-  三维视觉：过去、现在与未来
    1. 三维视觉
        - 语义无解
        - 三维感知->三维视觉
    2. 三维重建
        - 自动驾驶
            - 精准三维地图构建
            - 实时三维环境感知
    3. 三维行为计算
        - 时代划分
            - 摄影侧重理论时代
            - 光场摄影时代
            - SLAM时代
            - 深度相机时代
                - 双表面协同动态重建方法
                - 隐式函数表面融合方法
            - 表征学习时代
                - 多表征协同重建方法
            - 三维语义时代
                - 数据+知识+认知
                - 三维数据生成+三维语义表征+三维视觉认知原型 
***
- 下午2
- 点云智能处理与重建
    1. 3D形状表达
        - multi-view
        - point-cloud
        - volumetric
        - mesh
        - implicit function
    2. data-driven:
        - learning from large scale details 
    3. Representation learning:
        - encoding/latent code/feature
    4. 关注数据先验
        - encode，decode
        - 如何利用数据先验，如何设计一个好的encode，decode
    5. 已有网络
        - APPI-19:提出基于局部邻域的序列化点
            - 无序性->有序性
        - TIP-20：基于空间胶囊网络的三维模型特征学习       
            -  提出了几何特征整合模块，解决局部特征的无序性问题
        - ICCV-19：提出基于无监督三维点云的多视角。联合重建的划分预测算法
        - ACMMM-20：基于特征上下文融合的三维场景语义-实例联合分割
        - SA-Net：（CVPR 2020）基于局部形状特征相似度融合的三维模型补全
            - 层次化折叠，从稀疏到稠密逐步生成完整点云
        - cycle4completion（CVPR 2021）：
            - 无配对情况下三维点云的补全 
    6. 感悟
        - 傅里叶变换在encode中的应用
        - 点云投影
        - 神经网络可解释
        - 点云三维模型补全可以使用变换的方法，已有一个飞机找另一个飞机变换过去   
***
### 0713
- 上午1
- 物理和数据驱动的计算机角色动画
    1. Data-driven Character Animation
        - Motion graphs
        - Motion generative models 
    2. Physics-based Character Animation
        - Handcrafted motion control
        - Trajectory optimization
            -  Open-loop Control
        - Policy optimization
            - Reinforcement learning
    3. Multi-skilled Character
        - Control graphs
        - Scheduler
        - Motion generator + Tracking
        - Generative motion control
        - GAIL 
    4.  Data-driven vs. Data-free
    5.  Kinematic methods vs. Physics-based methods
    6.  Transfer learning & Multi-task learning
    7.  Multi-agent learning
***
- 上午2
- 使用拉格朗日粒子方法的图形学多流体模拟
    1. Navier-Stokes方程组
        - 牛顿
        - 动量方程:
        - $\rho \frac{D \mathbf{u}}{D t}=-\nabla p+\nabla \cdot \boldsymbol{\tau}+\rho \mathbf{g}$
        - 连续性方程:
        - $\frac{\partial \rho}{\partial t}+\nabla \cdot(\rho \mathbf{u})=0$ 
    2. 基础例子模拟方法：
        - SPH方法
            - WCSPH
            - IISPH
            - DFSPH
        - PBF方法 
    3. SPH方法
        - 一种将连续的场函数利用离散点采样值插值求和近似的方法
        - “核函数” W：
            - 较近处权重较大，拥有范围半径h
            - 对场的求导转化为对W的求导
        - 常见核函数
            - Poly6 Kernel：插值求和
            - Spiky Kernel：梯度计算
    4. PBF方法
        - 设粒子质量不变，在任意粒子领域分布中，其中心（粒子）的“实际密度”是一个关于所有邻域粒子位置的函数。
    5. 三个层次的模型
        - 完整模型
            - 使用原始的k组方程
            - 最基础，但难以完备化实用化计算
        - 混合流模型
            - 通过一点近似，解析地计算各相与混合平均间的相对漂移速度
        - “共同运动”模型
            - 假设各相的宏观速度完全相同
            - 非常容易计算，但无法正确模拟一些现象
***
- 下午1
- 高性能可视流体计算及其应用
    1. 高性能流体实现
        - Contiguity equation
            - $\frac{\partial}{\partial t} \oint_{V} \rho d v=-\oint_{S} \rho \boldsymbol{u} \cdot d \mathbf{s} \quad \Rightarrow \quad \frac{\partial \rho}{\partial t}+\nabla \cdot \rho \boldsymbol{u}=0$
        - Momentum equation
            - $\begin{aligned} \frac{\partial}{\partial t} \oint_{V} \rho \boldsymbol{u} d v+\oint_{S} \rho \boldsymbol{u} \otimes \boldsymbol{u} \cdot d s &=-\oint_{S} p \boldsymbol{n} \cdot d s+\oint_{S} \boldsymbol{\sigma} \cdot d s+\oint_{V} F d v \\ & \\ \frac{\partial \rho \boldsymbol{u}}{\partial t}+\nabla \cdot(\rho \boldsymbol{u} \otimes \boldsymbol{u}) &=-\nabla p+\nabla \cdot \boldsymbol{\sigma}+\boldsymbol{F} \quad \boldsymbol{F}=\rho \boldsymbol{g} \end{aligned}$
***   
- 下午2
-  Real-Time Cloth Simulation on GPUs
    1. 实时计算
        - Dynamics solver 40%
        - Collision Handling 60%
    2. Backword Eular Integration
        - Backward Euler Integration $\left\{\begin{array}{l}\mathbf{x}^{t+\Delta t}=\mathbf{x}^{t}+\Delta t \mathbf{v}^{t+\Delta t} \\ \mathbf{v}^{t+\Delta t}=\mathbf{v}^{t}+\Delta t \mathbf{M}^{-1} \mathbf{f}\left(\mathbf{x}_{i} i t+\Delta t\right) i\end{array} \Leftrightarrow\left\{\begin{array}{l}\mathbf{x}^{t+\Delta t}=\mathbf{x}^{t}+\Delta t \mathbf{v}^{t}+\Delta t^{2} \mathbf{M}^{-1} \mathbf{f}(\mathbf{x}\{\dot{i t+\Delta t) i} \\ \mathbf{v}^{t+\Delta t}=\mathbf{v}^{t}+\frac{1}{\Delta t}\left(\mathbf{x}^{t+\Delta t}-\mathbf{x}^{t}\right)\end{array}\right.\right.$  
***
### 0714
- 上午
- 大规模城市场景三维重建
    - 多源融合三维几何重建->细粒度三维语义重建->规范化三维矢量重建->基于三维地图的视觉定位
-  

