信用卡詐欺偵測實驗 (ex1)

任務目標
使用隨機森林（Random Forest）與 KMeans 模型進行監督與非監督學習，提升信用卡詐欺偵測準確度。

---

使用資料
- 來源：Kaggle MLG 提供信用卡交易資料
- 筆數：284,807 筆
- 詐欺交易：492 筆（約 0.172%，資料極度不平衡）
- 特徵數：30 個（包含經過 PCA 轉換的 V1~V28）

---

使用模型
   監督式學習：Random Forest
- 資料分割：70% 訓練 / 30% 測試
- 特徵處理：標準化 `Amount` 欄位
- 評估指標：Accuracy、Precision、Recall、F1-score

   非監督式學習：KMeans
- 使用部分正常交易（前 1000 筆）進行訓練
- 對齊 KMeans 結果與真實標籤
- 使用 silhouette score 找最佳 K 值

---

實驗結果（範例）
- Random Forest：
  - Precision: 0.91
  - Recall: 0.87
  - F1-score: 0.89

- KMeans：
  - Precision: 0.40
  - Recall: 0.33
  - F1-score: 0.36

---

改進方向
- 使用 SMOTE 等技術處理不平衡資料
- 試驗更多監督模型如 XGBoost、LightGBM
- 融合學習提升辨識力（見 ex2）
