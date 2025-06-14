# Samsung-Electronics-Internship-Project
Joined the AI Analytics group, which manages network systems using AI technologies. My role involved working on a project to create an AI model for Network Time Series Forecasting. This model is designed to predict various network related data, enhancing the accuracy and efficiency of network forecasting.

# 1. Objective
Evaluating the applicability and performance of open-source multivariate time-series forecasting models for analyzing and predicting network data.

# 2. Models
2.1. PatchTST
utilizes a novel patching mechanism where time-series are divided into segments (patches) before being fed into a transformer encoder
allows the model to effectively capture both local temporal patterns within patches and global dependencies across the entire time-series
Benefits: able to learn long-range correlations, making it suitable for complex and high-dimensional data
Weaknesses:  computationally intensive
Resources: Model Card, Tutorial, Paper

2.2. PatchTSMixer
Patching Concept + MLP-based mixing strategy
capable to pay attention to multiple resolutions and channels
Benefits: computational efficiency compared to pure transformer models while maintaining competitive forecasting performance
Weaknesses: compared to transformer models, sometimes struggle with extremely long-range dependencies
Resources: Model Card, Tutorial, Paper

# Experiments
3.1. Practice (ETL & Tutorial)
Dataset : ETTh1 (Open-source dataset)
Results
PatchTST: {eval_loss: 0.370, eval_sampels_per_second: 101.263, epochs: 8}
PatchTSMixer: {eval_loss: 0.379, eval_sampels_per_second: 670.682, epochs: 15}
3.2. Network KPIs
Target Channels : RRC_CONN(count), AIR_RLC_BYTES(bytes), ACTIVE_UE(count), PRB_TOTAL(%)
Key Results
Setup: Context Length = 24, Forecast Horizon = 1
PatchTSMixer performs better than PatchTST
Performance Improvement of PatchTST over PatchTST (measured with MSE)
{RRC_CONN: +65%, AIR_RLC_BYTES: 88%, ACTIVE_UE: 95%, PRB_TOTAL: +50%}

# 4. Conclusion
PatchTSMixer performs better than PatchTST with faster inference.
Both models require accurate context length and forecast horizon value. 
