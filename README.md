# portfolio-construction-asset-allocation-and-optimization
A toolkit for portfolio construction, optimization, and asset allocation. Includes models to find the optimal risk/return tradeoff by visualizing the Efficient Frontier and maximizing the Sharpe Ratio, plus tools for quantitative risk analysis and strategy backtesting.

# Portfolio Construction, Asset Allocation, and Optimization

A **comprehensive toolkit** for **portfolio construction, optimization, and asset allocation**.
This project demonstrates how to **analyze financial data**, **allocate assets**, and **find the optimal portfolio weights** using various quantitative models. It also includes **risk analysis, strategy backtesting, and visualization** of results such as the **Efficient Frontier** and **Sharpe Ratio maximization**.

---

## 📌 1. What & Why (คืออะไร / ทำไมต้องทำ)

### **Portfolio, Asset Allocation, Optimization คืออะไร**

* **Portfolio** → ชุดของสินทรัพย์ที่ลงทุนร่วมกัน เช่น BTC, S\&P500, SET
* **Asset Allocation** → การกำหนด “สัดส่วน” เงินลงทุนในแต่ละสินทรัพย์เพื่อให้เหมาะกับความเสี่ยง/เป้าหมาย
* **Optimization** → ใช้คณิตศาสตร์และอัลกอริทึมเพื่อ “ค้นหาสัดส่วนที่ดีที่สุด” ภายใต้เงื่อนไข เช่น maximize **Sharpe Ratio** หรือ minimize **Risk**

### **ทำไมต้องทำโปรเจกต์นี้**

* แปลง **เป้าหมายการเงิน** → เป็น **สัดส่วนพอร์ตที่ปฏิบัติได้**
* ฝึกใช้ **ข้อมูลจริง** + **สถิติ/ML/Optimization**
* เรียนรู้ **การจัดการความเสี่ยง** (Risk Management) แบบใช้งานจริง

---

## 🧩 2. DSLC Roadmap (Data Science Life Cycle)

### **🔹 Problem Definition**

* ระบุเป้าหมาย → เช่น ผลตอบแทนเฉลี่ย 8% ต่อปี
* ความเสี่ยงที่ยอมรับได้ → เช่น MaxDD ≤ 20%
* ข้อจำกัด → งบลงทุน, สินทรัพย์ที่ลงทุนได้, ความถี่การปรับพอร์ต
* **Output** → ขอบเขตโปรเจกต์ + KPIs เช่น CAGR, Sharpe Ratio

---

### **🔹 Data Collection**

* ดึงข้อมูลย้อนหลังของ **BTC, S\&P500, SET** (3/5/10 ปี)
* แหล่งข้อมูล: [Yahoo Finance](https://finance.yahoo.com/) / API
* ข้อมูลที่เก็บ:

  * วันที่ (Date)
  * ราคาปิด (Close Price)
  * ปริมาณซื้อขาย (Volume)
* **Output** → ไฟล์ CSV/Parquet + Python code (`yfinance`, `pandas_datareader`)

---

### **🔹 Preprocessing**

* Clean → ลบ Missing values, Outliers
* Align Time Index → ให้ทุกสินทรัพย์ใช้วันที่ตรงกัน
* Feature Engineering:

  * Daily Returns →  $(P_t - P_{t-1}) / P_{t-1}$
  * Volatility → ความผันผวน
  * Rolling Stats → ค่าเฉลี่ย & ความผันผวนเคลื่อนที่
* **Output** → DataFrame พร้อมสำหรับ EDA & Modeling

---

### **🔹 Exploratory Data Analysis (EDA)**

* วิเคราะห์การกระจายตัว (distribution) ของผลตอบแทน
* ดู Correlation ระหว่างสินทรัพย์
* แยกช่วง **Market Regimes** → ขาขึ้น, ขาลง, Sideway
* **Output**:

  * Histogram, Heatmap, Rolling Volatility
  * ตาราง Correlation
  * Insights สำหรับ Optimization

---

### **🔹 Modeling & Optimization**

เราจะสร้างและทดสอบ **6 โมเดลหลัก** สำหรับการจัดสัดส่วนพอร์ต:

| โมเดล                    | แนวคิด                                         | ความซับซ้อน |
| ------------------------ | ---------------------------------------------- | ----------- |
| **EW**                   | จัดสัดส่วนเท่ากันทุกสินทรัพย์                  | ง่าย        |
| **Risk Parity**          | กระจายความเสี่ยงให้เท่ากัน                     | ปานกลาง     |
| **Markowitz (MPT)**      | หาสัดส่วนที่ดีที่สุดระหว่างผลตอบแทน/ความเสี่ยง | ยาก         |
| **HRP**                  | ใช้ Clustering วิเคราะห์ความสัมพันธ์           | ปานกลาง-ยาก |
| **BL (Black-Litterman)** | ผสมข้อมูลตลาดกับมุมมองผู้เชี่ยวชาญ             | ยาก         |
| **CVaR**                 | ควบคุมความเสี่ยงกรณีตลาด Crash                 | ยากมาก      |

**Output**:

* ตาราง Optimal Weights
* Efficient Frontier Graph
* เปรียบเทียบผลลัพธ์แต่ละโมเดล

---

### **🔹 Backtesting & Evaluation**

ทดสอบโมเดลย้อนหลังและวัดประสิทธิภาพด้วยตัวชี้วัดหลัก:

* **CAGR** → ผลตอบแทนเฉลี่ยต่อปี
* **Sharpe / Sortino Ratio** → วัดผลตอบแทนต่อความเสี่ยง
* **Max Drawdown** → การขาดทุนสูงสุด
* **Turnover** → ความถี่การซื้อขาย
* **Costs** → ค่าธรรมเนียม
  **Output** → ตาราง Performance + Equity Curve

---

### **🔹 Deployment**

* Jupyter Notebooks & Scripts
* Dashboard (Streamlit / Dash)
* README.md
* แผน Rebalancing พอร์ต

---

## 🎯 3. Investment Goals

* ระบุ **รายได้ต่อปี/เดือนที่อยากได้** → เช่น 60,000 บาท/ปี
* กำหนด **ขอบเขตความเสี่ยง** → เช่น MaxDD ≤ 20%
* คำนวณเงินต้นที่ต้องใช้:

  $$
    \text{เงินต้น} ≈ \frac{\text{รายได้ต่อปี}}{\text{อัตราผลตอบแทนที่คาดหวัง}}
  $$

  **Example** → 60,000 / 0.04 ≈ **1,500,000 บาท**

---

## 📊 4. Data Sources

* **Bitcoin (BTC-USD)** → Yahoo Finance / Exchange API
* **S\&P 500** → ^GSPC / ^SP500TR
* **SET Index** → [SETTRADE](https://www.set.or.th/)
* ความถี่: **รายวัน** → แนะนำ resample เป็น **รายเดือน**

---

## 🧮 5. Portfolio Optimization Models

| โมเดล           | แนวคิด                 | การจัดการความเสี่ยง         | เหมาะกับ          | ข้อจำกัด                 |
| --------------- | ---------------------- | --------------------------- | ----------------- | ------------------------ |
| **EW**          | เท่า ๆ กัน             | กระจายแบบง่าย               | มือใหม่/เบสไลน์   | ไม่คำนึง vol/corr        |
| **Vol-Target**  | w ∝ 1/σ                | ลด exposure สินทรัพย์ผันผวน | ตลาดผันผวนสูง     | เพิกเฉย correlation      |
| **Risk Parity** | เท่า risk contribution | ลดการกระจุกตัวความเสี่ยง    | พอร์ตหลากหลาย     | ประมาณการ σ/Σ สำคัญ      |
| **MPT**         | mean-var               | ใช้ Σ และ μ                 | เมื่อตลาดนิ่งพอ   | overfit/fragile          |
| **HRP**         | tree-clustering        | robust ต่อ error            | สินทรัพย์หลายตัว  | พึ่งพาโครงสร้างคลัสเตอร์ |
| **CVaR**        | minimize tail loss     | คุม tail risk               | tail risk concern | คำนวณหนัก                |
| **BL**          | รวมมุมมอง              | ผสมตลาด+ความเห็น            | นักลงทุนขั้นสูง   | ตั้งค่าพารามิเตอร์ยาก    |

---

## 📂 6. Project Structure

```
portfolio-optimization/
├─ data/
│  ├─ raw/              # ไฟล์ราคาดิบที่ดึงมา
│  ├─ processed/        # หลัง clean/feature
├─ notebooks/
│  ├─ 01_eda.ipynb
│  ├─ 02_allocation_baselines.ipynb
│  ├─ 03_optimization_MPT_HRP_CVaR.ipynb
│  ├─ 04_backtest_report_3_5_10y.ipynb
├─ src/
│  ├─ data_loader.py
│  ├─ features.py
│  ├─ allocators.py     # EW, VolTarget, RiskParity
│  ├─ optimizers.py     # MPT, HRP, CVaR, BL
│  ├─ backtest.py
│  ├─ metrics.py
│  ├─ rebalancing.py
├─ reports/
│  ├─ figures/
│  ├─ tables/
├─ dashboard/
│  ├─ app.py            # Streamlit/Dash
├─ README.md
├─ requirements.txt
└─ LICENSE
```

---

## 🚀 7. How to Run

```bash
# Clone repository
git clone https://github.com/username/portfolio-optimization.git
cd portfolio-optimization

# Install dependencies
pip install -r requirements.txt

# Run dashboard
streamlit run dashboard/app.py
```

---

## 📌 8. Key Libraries

* `pandas`, `numpy` → Data processing
* `matplotlib`, `seaborn`, `plotly` → Visualization
* `yfinance`, `pandas_datareader` → Data fetching
* `scipy`, `cvxpy`, `PyPortfolioOpt` → Optimization
* `streamlit`, `dash` → Dashboard

---

## 🏁 9. Next Steps

* เพิ่มโมเดล Black-Litterman
* ทำ Hyperparameter Optimization สำหรับ Risk Parity
* สร้าง Monte Carlo Simulation สำหรับ Stress Test
* ปรับปรุง Dashboard ให้ Interactive

---

## 📜 License

This project is licensed under the **MIT License**.

---

ถ้าต้องการ ฉันสามารถเขียน **README.md** ตัวนี้ให้เป็นไฟล์จริง พร้อมโค้ด Markdown, รูปภาพประกอบ, และ Table of Contents ให้สวยแบบโปรเจกต์ GitHub มืออาชีพเลย

คุณอยากให้ฉันจัดทำไฟล์ **README.md** พร้อมโครงสร้างและรูปภาพกราฟสวย ๆ ไหมคะ?
มันจะทำให้โปรเจกต์ของคุณดู **โปรมากขึ้น** 🟢


