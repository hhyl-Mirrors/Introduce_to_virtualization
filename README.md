<h1> 💨 500篇关于虚拟化的经典资料，含CPU虚拟化，磁盘虚拟化，内存虚拟化，IO虚拟化。 </h1>

整理不易, 希望能够得到各位网友的支持，给予一颗小星星star，作者将更有动力。也欢迎广大网友提出宝贵的意见。
<br/>

<!--
![image](https://user-images.githubusercontent.com/87458342/134299929-8f7e5675-600e-4af3-b5b9-57b0bcf3f0af.png)
-->

<br/>

<h2>目录</h2>

* [🪐 虚拟化基础](#nav_vt0) 
  * [🍃 虚拟化分类](#nav_vt0_chapter1)
  * [🦕 CPU虚拟化](#nav_vt1) 
  * [🦖 内存虚拟化](#nav_vt2)
  * [🐊 IO虚拟化](#nav_vt3)
  * [🦎 存储虚拟化](#nav_vt4)
* [🌱 架构](#nav_vt1_chapter2)
* [🍊 实现](#nav_vt1_chapter8)
* [🧿 视频](#nav_vt1_chapter3)
* [🍀 论文](#nav_vt1_chapter4)
* [🌰 开源项目](#nav_vt1_chapter5)
* [📄 文章](#nav_vt1_chapter6)
* [📙 电子书籍](#nav_vt1_chapter7)

<br/>
<br/>

# <h1 id="nav_vt0">🪐 虚拟化基础</h1>

## [虚拟化技术](./virtualization_type/虚拟化技术.md)


## 虚拟化四种网络模型
<div align="center">
 
![image](https://user-images.githubusercontent.com/87458342/135031523-cfd6b87d-c918-497a-b84d-e976a58fd2e2.png)
 
 </div>

* [虚拟化四种网络模型](./virtualization_type/虚拟化之四种网络模型.md)

## 虚拟化思维导图
![image](https://user-images.githubusercontent.com/87458342/134476897-59097b19-9726-465c-a293-5781325b9f56.png)

## <h2 id="nav_vt0_chapter1">🍃 虚拟化分类</h2>

* [虚拟化技术分类](./virtualization_type/虚拟化技术分类.md)
* [全虚拟化和半虚拟化](./virtualization_type/全虚拟化和半虚拟化.md)
* [虚拟化五种类型](./virtualization_type/虚拟化五种类型.md)
* [CPU的三种虚拟化机制](./virtualization_type/CPU的三种虚拟化机制.md)

## <h2 id="nav_vt1">🦕 CPU虚拟化 </h2>

### CPU虚拟化三种实现技术
![image](https://user-images.githubusercontent.com/87458342/135200327-a1f0780a-8d09-4db6-b1ca-c83914d5a709.png)

<!--
![image](https://user-images.githubusercontent.com/87458342/134474242-094cd645-d33b-4566-9692-9a64782f674f.png)
-->

### 1. [基于二进制翻译的全虚拟化（Full Virtualization with Binary Translation）](./virtualization_type/cpu_virtualization/CPU虚拟化.md#cpu_virtualization_mode1)

### 2. [超虚拟化（或者半虚拟化/操作系统辅助虚拟化 Paravirtualization）](./virtualization_type/cpu_virtualization/CPU虚拟化.md#cpu_virtualization_mode2)

### 3. [硬件辅助的虚拟化](./virtualization_type/cpu_virtualization/CPU虚拟化.md#cpu_virtualization_mode3)

### 4. [CPU的三种虚拟化机制](./virtualization_type/cpu_virtualization/CPU的三种虚拟化机制.md)

## <h2 id="nav_vt2">🦖 内存虚拟化 </h2>

### 内存虚拟化思维导图
![image](https://user-images.githubusercontent.com/87458342/134679600-2bec9438-fa5f-49b0-b79c-7f8a2c9198d6.png)

### VMM内存虚拟化实现方式
* 软件方式：通过软件实现内存地址的翻译，比如 Shadow page table （影子页表）技术
* 硬件实现：基于 CPU 的辅助虚拟化功能，比如 AMD 的 NPT 和 Intel 的 EPT 技术 
![image](https://user-images.githubusercontent.com/87458342/134478479-4b09e660-bfce-4920-b954-15f3c817e710.png)

### 1. [内存虚拟化](./virtualization_type/memory_virtualization/内存虚拟化.md)
### 2. [KVM内存虚拟化](./virtualization_type/memory_virtualization/KVM内存虚拟化.md)
### 3. [内存虚拟化-shadow实现](./virtualization_type/memory_virtualization/内存虚拟化-shadow实现.md)
### 4. [内存虚拟化](./virtualization_type/memory_virtualization/内存虚拟化.md)
### 5. [影子页表技术](./virtualization_type/memory_virtualization/内存虚拟化影子页表技术和EPT技术.md#memory_t1)
### 6. [EPT技术](./virtualization_type/memory_virtualization/内存虚拟化影子页表技术和EPT技术.md#memory_t2)


## <h2 id="nav_vt3">🐊 IO虚拟化 </h2>

### I/O虚拟化三种方式
![image](https://user-images.githubusercontent.com/87458342/134502637-d16f6873-4f20-47c3-a706-ba1039bfb26e.png)

* 全虚拟化：宿主机截获客户机对I/O设备的访问请求，然后通过软件模拟真实的硬件。这种方式对客户机而言非常透明，无需考虑底层硬件的情况，不需要修改操作系统。
* 半虚拟化：通过前端驱动/后端驱动模拟实现I/O虚拟化。客户机中的驱动程序为前端，宿主机提供的与客户机通信的驱动程序为后端。前端驱动将客户机的请求通过与宿主机间的特殊通信机制发送给后端驱动，后端驱动在处理完请求后再发送给物理驱动。
* IO透传：直接把物理设备分配给虚拟机使用，这种方式需要硬件平台具备I/O透传技术，例如Intel VT-d技术。它能获得近乎本地的性能，并且CPU开销不高。

### 1. [I/O虚拟化](./virtualization_type/io_virtualization/IO虚拟化.md)
### 2. [I/O虚拟化三种形式](./virtualization_type/io_virtualization/IO虚拟化三种形式.md)
### 3. [I/O虚拟化基本原理](./virtualization_type/io_virtualization/IO虚拟化基本原理.md)
### 4. [I/O虚拟化面临的问题及解决方案](./virtualization_type/io_virtualization/IO虚拟化面临的问题及解决方案.md)



## <h2 id="nav_vt4">🦎 存储虚拟化 </h2>

### 存储虚拟化结构
![image](https://user-images.githubusercontent.com/87458342/134514544-c51a7bf1-24cd-45a1-b98a-aff06b47204a.png)

### 1. [块虚拟化](./virtualization_type/storage_virtualization/块虚拟化.md)
### 2. [磁盘虚拟化](./virtualization_type/storage_virtualization/磁盘虚拟化.md)
### 3. [磁带、磁带驱动器、磁带库虚拟化](./virtualization_type/storage_virtualization/在Linux平台使用mhVTL虚拟化磁带库.md)
### 4. [文件系统虚拟化](./virtualization_type/storage_virtualization/文件系统虚拟化解决方案.md)
### 5. [文件/记录虚拟化](./virtualization_type/storage_virtualization/什么是文件虚拟化(File%20Virtualization))
### 6. [基于主机的虚拟化](./virtualization_type/storage_virtualization/基于主机的虚拟化存储应用及注意事项.md)
### 7. [基于网络的虚拟化](./virtualization_type/storage_virtualization/Neutron实现网络虚拟化.md)
### 8. [基于存储设备、存储子系统的虚拟化](./virtualization_type/storage_virtualization/详解存储子系统的虚拟化.md)
### 9. [带内虚拟化](./virtualization_type/storage_virtualization/带内虚拟化和带外虚拟化.md)
### 10. [带外虚拟化](./virtualization_type/storage_virtualization/带内虚拟化和带外虚拟化.md)

<br/>
<br/>

# <h1 id="nav_vt1_chapter2">🌱 架构</h1>

## 虚拟化架构图

![image](https://user-images.githubusercontent.com/87458342/134765640-f9bb5323-067d-427c-b7b9-ea0e06b5cd1b.png)

* [虚拟化架构文章](./virtualization_type/虚拟化架构图.md)
* [虚拟化架构、特点及优势](./framework/虚拟化架构、特点及优势.md)

<br/>
<br/>

# <h1 id="nav_vt1_chapter8">🍊 实现</h1>

* [系统级虚拟化实现](./product/系统级虚拟化实现.md)
* [操作系统级虚拟化实现](./product/操作系统级虚拟化实现.md)

<!--
### VMM

* [虚拟化技术概要之VMM结构](./product/虚拟化技术概要之VMM结构.md)
* [vmm执行基本流程](./product/vmm执行基本流程.md)

### OpenStack

* [OpenStack官方网址](https://www.redhat.com/zh/topics/openstack)
* [OpenStack介绍及原理](./product/OpenStack介绍及原理.md)
* [OpenStack知识体系](./product/OpenStack知识体系.md)
* [P8整理的OpenStack构架，希望能帮助到你.md](./product/P8整理的OpenStack构架，希望能帮助到你.md)

### Xen

* [Xen虚拟化详解](./product/Xen虚拟化详解.md)

### vSphere

* [vSphere体系架构](./framework/vSphere体系架构.md)

### KVM

* [KVM简介及安装](./product/KVM简介及安装.md)
-->

<br/>
<br/>

# <h1 id="nav_vt1_chapter3">🧿 视频</h1>

提取码|vedio
:-------: | :--------------- 
2s25|[01-vSphere入门 ① 虚拟化杂谈，深入了解ESXI技巧及进阶后能做什么](https://pan.baidu.com/s/1eAO7ec9at8vu8vlVEc7U3Q)
u112|[02-vSphere入门 ② 全网最详细的ESXI进阶教程；vCenter Server、AD域部署](https://pan.baidu.com/s/1YFtLeT3IvKV64cE0bXL3_A)
px91|[03-vSphere入门 ③ 进阶ESXI与初始化配置vSphere Client](https://pan.baidu.com/s/10R0FLDf_Ov_qA_9YjqXpow)
dy45|[04-vSphere入门 ④ 在ESXI上安装FydeOS，运行安卓并Root。安卓虚拟化各方案情况说明](https://pan.baidu.com/s/1O5eoO8vm-CKVHpJJVFPkig)
1nht|[05- 虚拟化简介、实验环境介绍高清版](https://pan.baidu.com/s/1zeIJ1o1jeAuDKc11whjuow)
ljhw|[06-桌面虛擬化方案架構設計暨案例分享--VMware資深技術顧問](https://pan.baidu.com/s/1GoN-iLU6FlZr9Y5YNOKp_A)
un2r|[07-服务器虚拟化](https://pan.baidu.com/s/1p3B4gARzQL0HPQ1n06LP0Q)
cwgs|[08-xen虚拟化技术基础](https://pan.baidu.com/s/1n0qNnCaYcmM4GIT8cBpVxQ)
8vjj|[09-存储虚拟化](https://pan.baidu.com/s/1deaSAlsfLflVaKOYRXrO2g)
l349|[10-什么是VMware vSphere](https://pan.baidu.com/s/1WiGQVs6uWrsuKWAFoo8cHg)
2d68|[11-vSphere升级流程](https://pan.baidu.com/s/1uSrk-Ply3tRqxjhVXowffA)
r4zn|[12-VMware in 2020 - Detailed Version](https://pan.baidu.com/s/1UPdwO7L_nptRmnTjXXa_Yw)
16vo|[13-VMware NSX 開創新視界--VMware資深技術顧問](https://pan.baidu.com/s/1_X0zaazf_Clo6KusRSahnA)
5pvr|[14-VMware OCTO – xLabs – Computational Storage](https://pan.baidu.com/s/1u2cgwQs5JrDSFwNAGoBxCA)
n5hb|[15-how to enable virtualization in windows 7, 10  Enable Hyper-V In Bios](https://pan.baidu.com/s/1PNLW6gpDns0O83dCDRNVuw)
0xtd|[16-Virtualization in Cloud Computing](https://pan.baidu.com/s/1BrBx1m8AxDxejBBeRCKC7w)
6sun|[17-Docker虚拟化安装配置](https://pan.baidu.com/s/1XA4DxscLyMeoTIUUdJPKTw)
qnc2|[18-Docker虚拟化独立外网IP配置](https://pan.baidu.com/s/1xlxu2tDqfQiAL6hI_83iVw)
ibl6|[19-阿里云虚拟化技术分享](https://pan.baidu.com/s/1iJrDnVBFMB7-IWe4lay8xw)
yp1b|[20-传统数据中心的IT资源配置模式--烟囱式结构](https://pan.baidu.com/s/1uIu_cQF-54L7Syn4oFKAPg)
hagy|[21-构建vSphere虚拟化平台的准备工作](https://pan.baidu.com/s/1ir2T4eAx2zBzpHUg537Hsg)
xvs0|[22-虚拟化技术的分类](https://pan.baidu.com/s/1xfxjaEjuAwEKBO-rpOG-mw)

# <h1 id="nav_vt1_chapter4">🍀 论文</h1>

No.|Title|Translate|Company
:-------: | :--------------- | :------------|:---------------
1|[《Emerging Virtualization Technology》](./papers/01_Emerging_Virtualization_Technology.pdf) |《新兴虚拟化技术》|
2|[《HYPERVISOR FOR VIRTUALIZATION IN PRIVATE CLOUD》](./papers/02_HYPERVISOR_FOR_VIRTUALIZATION_IN_PRIVATE_CLOUD.pdf) |《私有云虚拟化管理程序》|
3|[《Secure Virtualization for Cloud Environment Using Hypervisor-based Technology》](./papers/03_Secure_Virtualization_for_Cloud_Environment_Using_Hypervisor-based_Technology.pdf) |《基于虚拟机监控程序的云环境安全虚拟化技术》|
4|[《OPERATING SYSTEM VIRTUALIZATION IN THE EDUCATION OF COMPUTER SCIENCE STUDENTS》](./papers/04_OPERATING_SYSTEM_VIRTUALIZATION_IN_THE_EDUCATION_OF_COMPUTER_SCIENCE_STUDENTS.pdf) |《计算机科学学生教育中的操作系统虚拟化》|
5|[《Virtualization Technologies and Cloud Security:advantages, issues, and perspectives》](./papers/05_Virtualization_Technologies_and_Cloud_Security:advantages,issues,and_perspectives.pdf) |《虚拟化技术和云安全：优势、问题和前景》|
6|[《Xen and the Art of Virtualization》](./papers/06_Xen_and_the_Art_of_Virtualization.pdf) |《Xen与虚拟化的艺术》|
7|[《Analysis of Virtualization Technologies for High Performance Computing Environments》](./papers/07_Analysis_of_Virtualization_Technologies_for_High_Performance_Computing_Environments.pdf) |《高性能计算环境的虚拟化技术分析》|
8|[《Research on Cloud Computing Based on Storage Virtualization in Data Center》](./papers/08_Research_on_Cloud_Computing_Based_on_Storage_Virtualization_in_Data_Center.pdf) |《基于数据中心存储虚拟化的云计算研究》|
9|[《Architecture for Technology Transformation》](./papers/09_Architecture_for_Technology_Transformation.pdf) |《技术改造架构》|
10|[《A Study On Virtualization Techniques And Challenges In Cloud Computing》](./papers/10_A_Study_On_Virtualization_Techniques_And_Challenges_In_Cloud_Computing.pdf) |《云计算中的虚拟化技术与挑战研究》|
11|[《Virtual Machine Security Guidelines Version 1.0》](./papers/11_Virtual_Machine_Security_Guidelines_Version_1.0.pdf) |《虚拟机安全指南1.0版》|
12|[《Comparative Performance Analysis of the Virtualization Technologies in Cloud Computing》](./papers/12_Comparative_Performance_Analysis_of_the_Virtualization_Technologies_in_Cloud_Computing.pdf) |《云计算中虚拟化技术的比较性能分析》|
13|[《Improving Business Performance by Employing VirtualizationTechnology: A Case Study in the Financial Sector》](./papers/13_Improving_Business_Performance_by_Employing_VirtualizationTechnology:_A_Case_Study_in_the_Financial_Sector.pdf) |《利用虚拟化技术提高业务绩效：金融行业案例研究》|
14|[《Consolidation Using Oracle's SPARCVirtualization Technologies》](./papers/14_Consolidation_Using_Oracle's_SPARCVirtualization_Technologies.pdf) |《使用Oracle的SPARCVirtualization技术进行整合》|
15|[《Development of a virtualization systems architecture course for Development of a virtualization systems architecture course for the information sciences and technologies depar the information sciences and technologies department at the tment at the Rochester Institute of Technology (RIT) Rochester Institute of Technology (RIT)》](./papers/15-Development_of_a_virtualization_systems_architecture_course_for_t.pdf) |《为信息科学和技术开发虚拟化系统体系结构课程的虚拟化系统体系结构课程的开发》|
16|[《Educational Infrastructure Using Virtualization Technologies: Experience at Kaunas University of Technology》](./papers/16_Educational_Infrastructure_Using_Virtualization_Technologies:_Experience_at_Kaunas_University_of_Technology.pdf) |《“利用虚拟化技术的教育基础设施：考纳斯技术大学的经验”》|
17|[《Comparative Study of Virtual Machine Software Packages with Real Operating System》](./papers/17_Comparative_Study_of_Virtual_Machine_Software_Packages_with_Real_Operating_System.pdf) |《虚拟机软件包与真实操作系统的比较研究》|
18|[《Dell EMC Unity: Virtualization Integration》](./papers/18_Dell_EMC_Unity:_Virtualization_Integration.pdf) |《Dell EMC Unity：虚拟化集成》|
19|[《A Study On Virtualization And Virtual Machines》](./papers/19_A_Study_On_Virtualization_And_Virtual_Machines.pdf) |《虚拟化与虚拟机研究》|
20|[《Review on Virtualization for Cloud Computing》](./papers/20_Review_on_Virtualization_for_Cloud_Computing.pdf) |《云计算虚拟化综述》|
21|[《A Survey on Virtualization and Hypervisor-based Technology in Cloud Computing Environment》](./papers/21_A_Survey_on_Virtualization_and_Hypervisor-based_Technology_in_Cloud_Computing_Environment.pdf) |《云计算环境中基于虚拟化和虚拟机监控程序的技术综述》|
22|[《STUDY ON VIRTUALIZATION TECHNOLOGY AND ITS IMPORTANCE IN CLOUD COMPUTING ENVIRONMENT》](./papers/22_STUDY_ON_VIRTUALIZATION_TECHNOLOGY_AND_ITS_IMPORTANCE_IN_CLOUD_COMPUTING_ENVIRONMENT.pdf) |《虚拟化技术及其在云计算环境中的重要性研究》|
23|[《Research on the Virtualization Technology in Cloud Computing Environment》](./papers/23_Research_on_the_Virtualization_Technology_in_Cloud_Computing_Environment.pdf) |《云计算环境下虚拟化技术研究》|
24|[《Research and Development on Network Virtualization Technologies in Japan》](./papers/24_Research_and_Development_on_Network_Virtualization_Technologies_in_Japan.pdf) |《日本网络虚拟化技术的研究与开发》|
25|[《Eliminate Software Development and Testing Constraints with Service Virtualization》](./papers/25_Eliminate_Software_Development_and_Testing_Constraints_with_Service_Virtualization.pdf) |《通过服务虚拟化消除软件开发和测试限制》|
26|[《Network Virtualization: A Data Plane Perspective》](./papers/26_Network_Virtualization:_A_Data_Plane_Perspective.pdf) |《网络虚拟化：数据平面透视图》|
27|[《A taxonomy of virtualization technologies》](./papers/27_A_taxonomy_of_virtualization_technologies.pdf) |《虚拟化技术分类》|
28|[《Network Functions Virtualisation》](./papers/28_Network_Functions_Virtualisation.pdf) |《网络功能虚拟化》|
29|[《Recommendations of the National Institute of Standards and Technology》](./papers/29_Recommendations_of_the_National_Institute_of_Standards_and_Technology.pdf) |《国家标准与技术研究所建议》|
30|[《Big Data Virtualization: Why and How?》](./papers/30_Big_Data_Virtualization:_Why_and_How.pdf) |《大数据虚拟化：为什么和如何？》|
31|[《Server Virtualization Technology and ltsLatest Trends》](./papers/31_Server_Virtualization_Technology_and_ltsLatest_Trends.pdf) |《服务器虚拟化技术和最新趋势》|
32|[《Virtualization Technologies for Cars Solutions to increase safety and security of vehicular ECUs》](./papers/32_Virtualization_Technologies_for_Cars_Solutions_to_increase_safety_and_security_of_vehicular_ECUs.pdf) |《提高车辆ECU安全性的车辆虚拟化技术解决方案》|
33|[《Virtualization and Future Technologies》](./papers/33_Virtualization_and_Future_Technologies.pdf) |《虚拟化与未来技术》|
34|[《Virtualization and the Computer Architecture》](./papers/34_Virtualization_and_the_Computer_Architecture.pdf) |《虚拟化与计算机体系结构》|
35|[《Virtualization Introduction QSM White Paper》](./papers/35_Virtualization_Introduction_QSM_White_Paper.pdf) |《虚拟化简介QSM白皮书》|
36|[《Security Implications of Different Virtualization Approaches for Secure Cyber Architectures》](./papers/36_Security_Implications_of_Different_Virtualization_Approaches_for_Secure_Cyber_Architectures.pdf) |《不同虚拟化方法对安全网络体系结构的安全影响》|
37|[《Server Virtualization: A Step Toward Cost Efficiency and Business Agility》](./papers/37_Server_Virtualization_A_Step_Toward_Cost_Efficiency_and_Business_Agility.pdf) |《服务器虚拟化：迈向成本效益和业务灵活性的一步》|
38|[《Performance Implications of Virtualization》](./papers/38_Performance_Implications_of_Virtualization.pdf) |《虚拟化的性能影响》|
39|[《State-of-the-Art of Virtualization, its Security Threats and Deployment Models》](./papers/39_State-of-the-Art_of_Virtualization,_its_Security_Threats_and_Deployment_Models.pdf) |《虚拟化技术现状、安全威胁和部署模型》|
40|[《HMI & Virtualization in Process Automation》](./papers/40_HMI_&_Virtualization_in_Process_Automation.pdf) |《过程自动化中的人机界面和虚拟化》|
41|[《Terra: A Virtual Machine-Based Platform for Trusted Computing》](./papers/41_Terra_A_Virtual_Machine-Based_Platform_for_Trusted_Computing.pdf) |《Terra：基于虚拟机的可信计算平台》|
42|[《Research on Virtualization Technology for Real-time Reconfigurable Systems》](./papers/42_Research_on_Virtualization_Technology_for_Real-time_Reconfigurable_Systems.pdf) |《实时可重构系统虚拟化技术研究》|
43|[《A Survey on Virtualization Technologies》](./papers/43_A_Survey_on_Virtualization_Technologies.pdf) |《虚拟化技术概览》|
44|[《Intel Virtualization Technology》](./papers/44_Intel_Virtualization_Technology.pdf) |《英特尔虚拟化技术》|
45|[《EXPERIENCES WITH VIRTUALIZATION TECHNOLOGY IN EDUCATION》](./papers/45_EXPERIENCES_WITH_VIRTUALIZATION_TECHNOLOGY_IN_EDUCATION.pdf) |《虚拟化技术在教育中的应用经验》|
46|[《VIRTUALIZATION IN CLOUD COMPUTING》](./papers/46_VIRTUALIZATION_IN_CLOUD_COMPUTING.pdf) |《云计算中的虚拟化》|
47|[《Systematic Study of Virtualization》](./papers/47_Systematic_Study_of_Virtualization.pdf) |《虚拟化系统研究》|
48|[《Virtualization in Cloud Computing : Developments and Trends》](./papers/48_Virtualization_in_Cloud_Computing__Developments_and_Trends.pdf) |《云计算中的虚拟化：发展与趋势》|
49|[《Virtualization Overview》](./papers/49_Virtualization_Overview.pdf) |《虚拟化概述》|
50|[《ArcGIS Pro Virtualization》](./papers/50_ArcGIS_Pro_Virtualization.pdf) |《ArcGIS Pro虚拟化》|
51|[《Intel® Virtualization Technology(VT) in Converged Application Platforms》](./papers/51_Intel®_Virtualization_Technology(VT)_in_Converged_Application_Platforms.pdf) |《聚合应用程序平台中的英特尔虚拟化技术（VT）》|
52|[《Virtualization Technology Whitepaper - Infrastructure to Perform Static Tools and Binary Analysis》](./papers/52_Virtualization_Technology_Whitepaper-Infrastructure_to_Perform_Static_Tools_and_Binary_Analysis.pdf) |《虚拟化技术白皮书-执行静态工具和二进制分析的基础架构》|
53|[《A Survey on Virtual Machine Security》](./papers/53_A_Survey_on_Virtual_Machine_Security.pdf) |《虚拟机安全调查》|
54|[《Intel® Virtualization Technology: Hardware Support for Efficient Processor Virtualization》](./papers/54_Intel®_Virtualization_Technology_Hardware_Support_for_Efficient_Processor_Virtualization.pdf) |《英特尔®虚拟化技术：高效处理器虚拟化的硬件支持》|
55|[《Network functions virtualization》](./papers/55_Network_functions_virtualization.pdf) |《网络功能虚拟化》|
56|[《BEYOND VIRTUALIZATION The MontaVista Approach to Multi-core SoC Resource Allocation and Control》](./papers/56_BEYOND_VIRTUALIZATION_The_MontaVista_Approach_to_Multi-core_SoC_Resource_Allocation_and_Control.pdf) |《超越虚拟化——多核SoC资源分配和控制的MontaVista方法》|
57|[《A PRINCIPLED TECHNOLOGIES WHITE PAPER》](./papers/57_A_PRINCIPLED_TECHNOLOGIES_WHITE_PAPER.pdf) |《原则性技术白皮书》|
58|[《Data Virtualization – Flexible Technology for the Agile Enterprise》](./papers/58_Data_Virtualization–Flexible_Technology_for_the_Agile_Enterprise.pdf) |《数据虚拟化——敏捷企业的灵活技术》|
59|[《Top 5 Things You Need in a Virtualization Management Solution》](./papers/59_Top_5_Things_You_Need_in_a_Virtualization_Management_Solution.pdf) |《虚拟化管理解决方案中需要的五大要素》|
60|[《The IBM Advantage for Implementing the Virtualization Reference Architecture》](./papers/60_The_IBM_Advantage_for_Implementing_the_Virtualization_Reference_Architecture.pdf) |《IBM实施虚拟化参考体系结构的优势》|


<br/>
<br/>

# <h1 id="nav_vt1_chapter5">🌰 开源项目</h1>

## <h3 id="nav_vt1_chapter5_01">[KVM](http://www.linux-kvm.org)</h3>

KVM (全称是 Kernel-based Virtual Machine) 是 Linux 下 x86 硬件平台上的全功能虚拟化解决方案，包含一个可加载的内核模块 kvm.ko 提供和虚拟化核心架构和处理器规范模块。
使用 KVM 可允许多个包括 Linux 和 Windows 每个虚拟机有私有的硬件，包括网卡、磁盘以及图形适配卡等。

## <h3 id="nav_vt1_chapter5_02">[Xen](https://xenproject.org)</h3>

Xen 是一个开放源代码虚拟机监视器，由剑桥大学开发。它打算在单个计算机上运行多达100个满特征的操作系统。操作系统必须进行显式地修改（“移植”）以在Xen上运行（但是提供对用户应用的兼容性）。这使得Xen无需特殊硬件支持，就能达到高性能的虚拟化。

## <h3 id="nav_vt1_chapter5_03">[OpenVZ](https://openvz.livejournal.com)</h3>

OpenVZ是基于Linux内核和作业系统的操作系统级虚拟化技术。OpenVZ允许物理服务器运行多个操作系统，被称虚拟专用服务器（VPS，Virtual Private Server）或虚拟环境（VE, Virtual Environment）。
与VMware这种虚拟机和Xen这种半虚拟化技 术相比，OpenVZ的host OS和guest OS都必需是Linux（虽然在不同的虚拟环境里可以用不同的Linux发行版）。但是，OpenVZ声称这样做有性能上的优势。根据OpenVZ网站的 说法，使用OpenVZ与使用独立的服务器相比，性能只会有1-3%的损失。
OpenVZ是SWsoft, Inc.公司开发的专有软件Virtuozzo的基础。OpenVZ的授权为GPLv2。
OpenVZ由两部分组成，一个经修改过的操作系统核心与及用户工具。

## <h3 id="nav_vt1_chapter5_04">[VirtualBox](https://www.virtualbox.org)</h3>

VirtualBox 是一款功能强大的 x86 虚拟机软件，它不仅具有丰富的特色，而且性能也很优异。更可喜的是，VirtualBox 于数日前走向开源，成为了一个发布在 GPL 许可之下的自由软件。

## <h3 id="nav_vt1_chapter5_05">[Lguest](http://lguest.ozlabs.org)</h3>

Lguest 是由IBM工程师Rusty Russell（澳大利亚开发者)发起的虚拟化项目，是一个只有5000行代码的精简hypervisor（虚拟机管理程序），它已经包括在最近版本的内核里了。和KVM相似，它支持 Intel和AMD芯片的最新虚拟化技术。但又与VMware公司的ESX Server不同，在Lguest创建的虚拟机里的操作系统知道自己是被虚拟出来的。所以在调用CPU周期时它可以直接向真正的硬件发出请求，而不是作为中间媒介而降低了效率，因此这种架构大大提高了效率。Lguest采用GPL授权。

* [VManagePlatform ：一个KVM虚拟化管理平台](https://github.com/Moniter123/VManagePlatform)
* [MalAnalyzer ：基于docker虚拟化的恶意代码沙箱](https://github.com/felicitychou/MalAnalyzer)
* [PinVMP ：虚拟化代码辅助分析工具](https://github.com/lmy375/pinvmp)
* [File-Management ：基于虚拟磁盘模仿ext2的图形化文件管理系统](https://github.com/pancerZH/File-Management)

<br/>
<br/>

# <h2 id="nav_vt1_chapter6">📄 文章</h2>

<div align=left>
</div>

<br/>
<br/>

# <h1 id="nav_vt1_chapter7">📙 电子书籍</h1>

* 《VMware vSphere4 云操作系统搭建配置入门与实战》.pdf
* 《VMwareCertifiedProfessionalTest Prep》.pdf
* 《企业虚拟化实战Vmware篇》.pdf
* 《精通VMware vSphere 5原版》.pdf
* 《虚拟智慧VMware vSphere运维实录》.pdf


<br/>
<br/>

## <h2 id="nav_9">🤝 鸣谢</h2>

##### 为了让我们的repo内容更加的丰富，更加的专业。欢迎大家贡献patch，希望大家在issue里面出谋划策，我们期待你的加入。

<a href="https://github.com/wangbojing">
    <img src="https://avatars.githubusercontent.com/u/18027560?v=4" width="40px">
</a> 

<a href="https://github.com/ls-Brynn">
    <img src="https://avatars.githubusercontent.com/u/87458342?v=4" width="40px">
</a> 

## 联系专栏

#### 零声教育，专注于c/c++Linux后台服务器开发架构技术学习提升。<br>
每天晚上8点【免费技术直播】：[分享Linux，Nginx，ZeroMQ，MySQL，Redis，fastdfs，MongoDB，ZK，流媒体，CDN，P2P，K8S，Docker，TCP/IP，协程，DPDK等技术内容，立即学习。](https://ke.qq.com/course/417774?flowToken=1037127)

#### 关注微信公众号【后台服务架构师】——【联系我们】，获取本repo最全PDF学习文档！

<img width="65%" height="65%" src="https://user-images.githubusercontent.com/87457873/130796999-03af3f54-3719-47b4-8e41-2e762ab1c68b.png"/>
