# On-Demand Capacity Provisioning in Storage Clusters Through Workload Pattern Modeling

注重效率，但能耗很高

---

# Thermal-Aware and DVFS-Enabled Big Data Task Scheduling for Data Centers

注重节能，效率不知，数据中心处理

## 概念

- 动态电压及频率调度（DVFS，dynamic voltage and frequency scaling）
- 张量（Tensor），多维向量

## 模型

每个节点的能耗
![](./imgs/thermal_aware_and_dvfs_enabled_big_data_task_scheduling_for_data_centers/node_power.PNG)

刀片服务器分配数量矩阵（C）以及对应运行频率矩阵（F），三维分别对应任务（Task, range(1...P)）、服务器节点（Node, range(1...N)）以及时间块（Timeslot range(1...L)）
![](./imgs/thermal_aware_and_dvfs_enabled_big_data_task_scheduling_for_data_centers/matrix_c_f.PNG)

能耗方程
![](./imgs/thermal_aware_and_dvfs_enabled_big_data_task_scheduling_for_data_centers/abstract_energy_consumption_equation.PNG)
![](./imgs/thermal_aware_and_dvfs_enabled_big_data_task_scheduling_for_data_centers/detailed_energy_consumption_equation.PNG)

模拟退火算法
![](./imgs/thermal_aware_and_dvfs_enabled_big_data_task_scheduling_for_data_centers/algo.PNG)