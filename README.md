# 信用风险评估模型 (Credit Risk Model)

## 项目背景
本项目基于某信贷平台的历史数据，构建机器学习模型预测客户在未来两年内发生财务危机（违约）的概率。该模型可用于信贷审批自动化、风险定价等场景。

## 数据集
- 来源：Kaggle "Give Me Some Credit"
- 样本量：约15万条记录
- 特征数：10+（包含年龄、收入、负债比、信用卡使用率等）
- 目标变量：`SeriousDlqin2yrs`（1=违约，0=正常）

## 技术栈
- Python 3.10+
- Pandas / NumPy（数据处理）
- Scikit-learn（数据拆分、评估）
- XGBoost（建模）
- Matplotlib（可视化）
- SHAP（模型解释，使用XGBoost内置方法）

## 项目流程
1. 数据清洗：处理缺失值（中位数填充），删除无意义列
2. 特征工程：衍生收入负债比、信用卡使用率等特征
3. 样本不均衡处理：使用 `scale_pos_weight` 调整权重
4. 模型训练：XGBoost分类器，5折交叉验证
5. 模型评估：测试集AUC = 0.869，KS = 0.574
6. 模型解释：使用SHAP分析特征重要性，识别风险驱动因子

## 关键结果
- **AUC**: 0.869
- **KS值**: 0.574
- **混淆矩阵**（阈值0.5）: 
  - 好客户误判为坏客户（误伤）: 5731
  - 坏客户漏判（漏网）: 451
- **最重要特征**: 信用卡使用率（RevolvingUtilizationOfUnsecuredLines）

## 模型解释示例
下图展示了一个被预测为高风险的客户，各特征对其违约概率的贡献（红色推高风险，蓝色降低风险）：
<img width="1747" height="915" alt="333333" src="https://github.com/user-attachments/assets/da2d4eb4-cef8-446f-9968-fe99d69fa69b" />

## 如何复现
1. 克隆仓库：`git clone https://github.com/ghoston1234/credit-risk-model.git`
2. 运行 `Final_Project_File.ipynb` 即可复现所有结果

## 未来改进方向
- 收集更多维度的数据（如征信查询记录、社交行为等）
- 尝试LightGBM、神经网络等模型
- 部署为API服务，集成到审批系统

## 作者
薛先生 
邮箱：2945315190@qq.com  

## 许可证
暂无
