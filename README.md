# Samsung-Electronics-Internship-Project
Joined the AI Analytics group, which manages network systems using AI technologies. My role involved working on a project to create an AI model for Network Time Series Forecasting. This model is designed to predict various network related data, enhancing the accuracy and efficiency of network forecasting.

(日本語)
AI技術を用いてネットワークシステムを管理するAIアナリティクスグループに参加しました。私の役割は、ネットワークの時系列予測を行うAIモデルの開発プロジェクトに携わることでした。このモデルは、ネットワーク関連のさまざまなデータを予測することを目的としており、ネットワーク予測の精度と効率の向上に貢献しました。

**Coding Language**：Python

## 1. Objective
Evaluating the applicability and performance of open-source multivariate time-series forecasting models for analyzing and predicting network data.

(日本語)

## 2. Models
### 2.1. PatchTST
utilizes a novel patching mechanism where time-series are divided into segments (patches) before being fed into a transformer encoder
allows the model to effectively capture both local temporal patterns within patches and global dependencies across the entire time-series
Benefits: able to learn long-range correlations, making it suitable for complex and high-dimensional data
Weaknesses:  computationally intensive
Resources: [Model Card](https://huggingface.co/docs/transformers/en/model_doc/patchtst),[Tutorial](https://github.com/ibm-granite/granite-tsfm/blob/main/notebooks/hfdemo/patch_tsmixer_getting_started.ipynb), [Paper](https://arxiv.org/pdf/2306.09364)

(日本語)
本モデルは、時系列データをセグメント（パッチ）に分割し、それらをTransformerエンコーダに入力する新しいパッチング機構を採用しています。
このアプローチにより、各パッチ内の局所的な時間的パターンと、時系列全体にわたるグローバルな依存関係の両方を効果的に捉えることが可能になります。

### 2.2. PatchTSMixer
Patching Concept + MLP-based mixing strategy capable to pay attention to multiple resolutions and channels.
Benefits: computational efficiency compared to pure transformer models while maintaining competitive forecasting performance
Weaknesses: compared to transformer models, sometimes struggle with extremely long-range dependencies
Resources: [Model Card](https://huggingface.co/docs/transformers/en/model_doc/patchtsmixer),[Tutorial](https://github.com/ibm-granite/granite-tsfm/blob/main/notebooks/hfdemo/patch_tsmixer_getting_started.ipynb), [Paper](https://arxiv.org/pdf/2306.09364)

(日本語）
パッチング手法とMLPベースのミキシング戦略を組み合わせることで、複数の解像度およびチャネルに対して注意を向ける能力を実現しています。
このアーキテクチャにより、時系列データをパッチ単位で処理しながら、チャネル間の相互作用やスケールの異なる時間的特徴を効果的に捉えることが可能となります。

## Experiments
### 3.1. Practice (ETL & Tutorial)
Dataset : ETTh1 (Open-source dataset)
Results
PatchTST: {eval_loss: 0.370, eval_sampels_per_second: 101.263, epochs: 8}
PatchTSMixer: {eval_loss: 0.379, eval_sampels_per_second: 670.682, epochs: 15}
### 3.2. Network KPIs
Target Channels : RRC_CONN(count), AIR_RLC_BYTES(bytes), ACTIVE_UE(count), PRB_TOTAL(%)
Key Results
Setup: Context Length = 24, Forecast Horizon = 1
PatchTSMixer performs better than PatchTST
Performance Improvement of PatchTST over PatchTST (measured with MSE)
{RRC_CONN: +65%, AIR_RLC_BYTES: 88%, ACTIVE_UE: 95%, PRB_TOTAL: +50%}

## 4. Conclusion
PatchTSMixer performs better than PatchTST with faster inference.
Both models require accurate context length and forecast horizon value. 

## **Unable to provide Full Code for company policies**
