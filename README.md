# 🏆 Datathon 2026 — The Gridbreakers
**Team:** Tomorrow Business Analyst  
**Host:** VinTelligence — VinUniversity DS&AI Club  
**Competition:** [Kaggle — Datathon 2026 Round 1](https://www.kaggle.com/competitions/datathon-2026-round-1)

---

## 📁 Repository Structure

```
Datathon-R1/
├── 1. Tomorrow Business Analyst MCQs.ipynb        # Phần 1: Câu hỏi trắc nghiệm
├── 2. Tomorrow Business Analyst (Predictive & Pre...).ipynb  # Phần 2: EDA & Phân tích
├── 2. Tomorrow Business Analyst_EDA.pbix          # Power BI Dashboard
├── 3_Tomorrow_Business_Analyst_Sales_Forecasting.ipynb      # Phần 3: Forecasting
├── Tomorrow Business Analyst_Report.pdf           # Báo cáo chính thức (NeurIPS format)
├── submission.csv                                 # File nộp Kaggle
└── README.md
```

---

## 📊 Dashboard Preview

> **Tool:** Power BI  
> **File:** `2. Tomorrow Business Analyst_EDA.pbix`
## 📊 Dashboard Preview

> **Tool:** Power BI | **File:** `2. Tomorrow Business Analyst_EDA.pbix`

| Dashboard | Preview |
|---|---|
| 1. Báo cáo lãi lỗ | ![](assets/1.%20Báo%20cáo%20lãi%20lỗ.png) |
| 2. Phân tích doanh thu | ![](assets/2.%20Phân%20tích%20doanh%20thu.png) |
| 3. Phân tích chi phí | ![](assets/3.%20Phân%20tích%20chi%20phí.png) |
| 3. Phân tích Sales data | ![](assets/3.%20Phân%20tích%20Sales%20data.png) |
| 4. Phân tích Promo data | ![](assets/4.%20Phân%20tích%20Promo%20data.png) |
| 5. Phân tích website | ![](assets/5.%20Phân%20tích%20website.png) |
| 6. Phân tích Customer data | ![](assets/6.%20Phân%20tích%20Customer%20data.png) |
| 7. Phân tích Customer data 2 | ![](assets/7.%20Phân%20tích%20Customer%20data%202.png) |
| 8. Phân khúc khách hàng | ![](assets/8.%20Phân%20khúc%20khách%20hàng.png) |
| 9. Tình hình kho vận | ![](assets/9.%20Tình%20hình%20kho%20vận.png) |

> 💡 *Để xem dashboard tương tác, tải file `.pbix` và mở bằng [Power BI Desktop](https://powerbi.microsoft.com/desktop).*

---

## 🔍 Tóm tắt phân tích (Phần 2)

Doanh thu đạt đỉnh năm 2018 và suy giảm liên tục. Qua phân tích 4 cấp độ **Descriptive → Diagnostic → Predictive → Prescriptive**, chúng tôi xác định 3 nguyên nhân gốc rễ:

| # | Vấn đề | Giải pháp | Revenue phục hồi |
|---|---|---|---|
| 1 | Chiến lược vùng chưa tối ưu (West sụt giảm 30% volume) | Curated Regional Strategy | — |
| 2 | Return rate cao (wrong_size 35%) + SKU mismatch | AI Size Tool + Demand Forecasting | ~125M |
| 3 | Retention cực thấp (inter-order gap 407 ngày) | RFM-based Loyalty Program | ~558M |
| | | **Tổng** | **~683M** |

---

## 🤖 Mô hình Dự báo (Phần 3)

**Mục tiêu:** Dự báo `Revenue` và `COGS` hàng ngày cho giai đoạn 2023-01-01 → 2024-07-01.

**Pipeline:**
1. **Feature Engineering** — Lag features (7/14/30/365 ngày), Rolling Mean, Time features, Promotion flags
2. **Time-based Split** — Train: 2012–2020 | Validation: 2021–2022 (không data leakage)
3. **Ensemble Model** — LightGBM + XGBoost (50-50 average), tuned via GridSearchCV
4. **Recursive Forecasting** — Dự báo tuần tự từng ngày, dùng $\hat{y}_t$ làm lag cho $t+1$

**Kết quả validation (2021–2022):** R² ≈ 0.80

### Hướng dẫn chạy lại

```bash
# 1. Clone repo
git clone https://github.com/tratramcute/Datathon-R1.git

# 2. Mở notebook trên Google Colab (recommended)
# File: 3_Tomorrow_Business_Analyst_Sales_Forecasting.ipynb

# 3. Mount Google Drive và cập nhật DATA_DIR trỏ đến folder chứa dataset Kaggle
# Dataset: https://www.kaggle.com/competitions/datathon-2026-round-1/data

# 4. Run All Cells — random_state=42 đã được set để đảm bảo reproducibility
```

**Dependencies:**
```
pandas, numpy, matplotlib, seaborn
lightgbm, xgboost, scikit-learn, shap
```

---

## 📄 Báo cáo

Báo cáo chính thức theo template **NeurIPS 2025**: [`Tomorrow Business Analyst_Report.pdf`](./Tomorrow%20Business%20Analyst_Report.pdf)

---

*Datathon 2026 — VinTelligence × VinUniversity*
