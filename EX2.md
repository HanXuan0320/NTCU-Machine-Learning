# Credit Card Fraud Detection - 實驗說明

作者：ACS111107  簡祐暄
作業類型：Machine Learning 練習作業 (挑戰二)  
日期：2025/6/5

---

## 使用資料集

- 資料來源：[Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- 總筆數：284,807
- 詐騙交易數：492（佔 0.172%）
- Class：0 = 正常，1 = 詐騙

---

## 實驗設定

- 使用固定設定：
  - `RANDOM_SEED = 42`
  - `TEST_SIZE = 0.3`
- 評估指標：
  - Accuracy
  - Precision
  - Recall
  - F1 Score

---

## 使用的模型

###  非監督式
- 套件：`from sklearn.ensemble import IsolationForest
`
- 調整參數：
  ```python
  iso = IsolationForest(
    n_estimators=200,
    contamination=0.0017,
    max_samples=5000,
    random_state=42
  )
   ```
     就監督式學習，XGBClassifier 較適合使用在此實例上，再慢慢測試個參數的結果，即可得出此結果。

  ### 2. 監督式
  -使用 XGBClassifier
- 調整參數：
  ```python
  rf_model = XGBClassifier(
    n_estimators=400,
    max_depth=10,
    learning_rate=0.16,
    scale_pos_weight=100,
    eval_metric='logloss',
    use_label_encoder=False,
    random_state=42
  )
  ```
- 說明：
    我是用範例的兩個方式進行參數的調整，改變樹的數量與learning rate的值與樹的深度(depth)
- 範例結果
  -   ![image](https://github.com/user-attachments/assets/61c60032-9224-419c-804c-cdd8fd337e5a)
- 我的結果
  - ![image](https://github.com/user-attachments/assets/2d711785-52e6-4b37-84c5-088675b82db1)
 
    
   
