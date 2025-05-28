信用卡詐欺偵測實驗 (ex2)

任務目標
嘗試融合非監督式學習（Isolation Forest）與監督式學習（XGBoost）進行詐欺交易偵測，提升整體預測能力。

---

實驗方法
1. 使用 Isolation Forest 對訓練資料進行異常偵測（非監督）
2. 將異常偵測結果（標籤）作為新的特徵欄加入資料集中
3. 使用 XGBoost 模型進行監督式學習分類
4. 對測試集資料也做同樣的異常特徵提取並預測

---

技術細節
- Isolation Forest：
  - contamination 設為 0.01（對應實際詐欺比例）
  - 對訓練與測試集分別標記異常
- XGBoost：
  - 使用 anomaly 欄位 + 原始特徵進行訓練與預測
  - 評估：accuracy、precision、recall、f1-score

---

實驗結果（示意）
- 精準度（Precision）有明顯提升
- 模型可辨識更多詐欺樣本，提高 Recall 與 F1
- 預測能力優於單一模型結果（如 Random Forest）

---

模型融合的優勢
- Isolation Forest 可發掘隱藏異常點
- XGBoost 對分類邊界掌握能力強，補強預測結果
- 適合資料極度不平衡的詐欺偵測問題