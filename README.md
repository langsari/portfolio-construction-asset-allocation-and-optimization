📌 Portfolio Construction, Asset Allocation & Optimization 

 1️⃣ What & Why (คืออะไร / ทำไมต้องทำ)
**Portfolio (พอร์ตการลงทุน)**  
- คือ ตะกร้าการลงทุน ที่ประกอบด้วยหลายสินทรัพย์ เช่น หุ้น, พันธบัตร, ทองคำ, ETF, Crypto  
- เหตุผล: ลดความเสี่ยงจากการถือสินทรัพย์เดียว (Diversification)  

**Asset Allocation (การจัดสัดส่วนการลงทุน)**  
- กำหนด น้ำหนักการลงทุน ในแต่ละสินทรัพย์ เช่น:
    - หุ้น 60%
    - พันธบัตร 30%
    - ทองคำ 10%
- เหตุผล: จัดสมดุลระหว่างผลตอบแทนและความเสี่ยง  

**Optimization (การหาสัดส่วนพอร์ตที่ดีที่สุด)**  
- ใช้ คณิตศาสตร์และโมเดลเชิงปริมาณ เพื่อเลือกสัดส่วนที่เหมาะสม  
- ตัวอย่างเป้าหมาย: maximize Sharpe Ratio, minimize variance หรือ CVaR  
**เหตุผลสำคัญในการทำโปรเจกต์นี้**
1. แปลง เป้าหมายทางการเงิน → เป็น สัดส่วนพอร์ตลงทุนจริง  
2. ฝึกใช้ ข้อมูลจริง + Data Science Tools (Python, Pandas, NumPy, CVXPY, PyPortfolioOpt)  
3. เรียนรู้ Risk Management แบบใช้งานได้จริง  
---

## 2️⃣ DSLC Roadmap (Data Science Life Cycle – Practical Version)

### 1. Problem Definition
**วัตถุประสงค์ (Goal)**
- กำหนดเป้าหมายทางการเงินที่ชัดเจนก่อนเริ่มทำโปรเจกต์  
- ตัวอย่าง: ต้องการ เงินใช้เดือนละ 5,000 บาท หรือ ปีละ 60,000 บาท  
- เป้าหมายนี้จะถูกใช้เป็น benchmark สำหรับการเลือกพอร์ตและคำนวณเงินต้นที่ต้องลงทุน  
**ข้อจำกัด / ความเสี่ยง (Constraints / Risk Limits)**
- ระบุความเสี่ยงสูงสุดที่ยอมรับได้ เช่น Max Drawdown ≤ 20%  
- Max Drawdown คือ ขาดทุนสูงสุดจากจุดสูงสุดของพอร์ต  
    - ตัวอย่าง: พอร์ตมีมูลค่า 1,000,000 บาท → หาก MaxDD = 20% หมายถึงยอมให้พอร์ตลดลงสูงสุด 200,000 บาท ก่อนปรับกลยุทธ์  
**เหตุผลสำคัญ**  
- การกำหนดเป้าหมายและข้อจำกัดตั้งแต่แรก ทำให้ขั้นตอนต่อ ๆ ไปของ DSLC มีกรอบชัดเจน  
- ช่วยให้เลือก สินทรัพย์, โมเดล, และวิธี optimization ได้เหมาะสมกับเป้าหมายและความเสี่ยง  

### 2. Data Collection
- สินทรัพย์: S&P500(ETF)  
- ข้อมูลย้อนหลัง: 5–10 ปี  
- แหล่งข้อมูล: Yahoo Finance, SETTRADE API  

### 3. Preprocessing
- ลบ missing values, ตรวจ outliers (ข้อมูลสะอาด ไม่มี missing / outliers)  
- Align date → ทำให้ series ของทุกสินทรัพย์ตรงกัน/เปรียบเทียบกันได้  
- สร้าง features:
    - Returns: \( R_t = \frac{P_t - P_{t-1}}{P_{t-1}} \)  
    - Volatility (annualized): std × √freq  
    - Rolling mean / vol: 6M, 12M  
    - Drawdown: peak-to-trough loss  

### 4. Exploratory Data Analysis (EDA)
- Price chart + returns → ตรวจทิศทางราคา  
- Correlation heatmap → ตรวจดู diversification  
- Market regimes → แยก high / low volatility  

### 5. Modeling & Optimization (ใช้จริง)
| Model | จุดเด่น | เหมาะกับ | Notes |
|-------|---------|-----------|-------|
| MPT (Markowitz) | Max Sharpe | ต้องการผลตอบแทนคุ้มความเสี่ยงสูงสุด | Sensitive ต่อ estimation error ของ μ, Σ |
| HRP | Robust ต่อ noisy data | เสถียร, ลด estimation error | ใช้ clustering + recursive allocation |
| CVaR | Minimize tail risk | ลด extreme loss | เหมาะกับ asset ผันผวนสูง เช่น Crypto |

### 6. Backtesting & Evaluation
- Metrics: CAGR, Volatility, Sharpe/Sortino, Max Drawdown, Turnover  
- Input: Returns series + portfolio weights  
- ตรวจว่าพอร์ตสามารถทำตามเป้าหมายได้หรือไม่  

### 7. Deployment
- Notebook + Dashboard (เช่น Streamlit) → ให้ผู้ใช้งานเลือกสินทรัพย์, เป้าหมายเงินใช้, ความเสี่ยง  
- Workflow: fetch data → preprocess → optimize → backtest → export results  
---

## 3️⃣ Goals → Money

**เป้าหมายการลงทุน:** เงินใช้เดือนละ 5,000 บาท → ปีละ 60,000 บาท  

**เงินต้นที่ต้องใช้ (คาดหวังผลตอบแทน 6%):**
เงินต้น ≈ รายได้ต่อปี ÷ ผลตอบแทนที่คาดหวัง
       = 60,000 ÷ 0.06
       = 1,000,000 บาท

**Asset Allocation แบบ Balanced / Growth:**
|   สัดส่วน  |   สินทรัพย์  |
|--------- |------------|
|   40%    | Global Equity ETF (S&P500, MSCI World) |
|   20%    | SET50 ETF |
|   30%    | Bond Fund/ตราสารหนี้ |
|   10%    | Gold ETF |

- ผลตอบแทนเฉลี่ย: ~6–7% ต่อปี → รายได้ ~60k–70k บาท/ปี  

## 4️⃣ Data & Preprocessing

- แหล่งข้อมูล: Yahoo Finance / SETTRADE API  
- ไฟล์สำคัญ:  
  - Daily → สำหรับ preprocessing, feature engineering  
  - Monthly → สำหรับ modeling, optimization, backtesting  

| Feature | ใช้กับ MPT | ใช้กับ HRP | ใช้กับ CVaR | Notes |
|---------|------------|------------|-------------|-------|
| Returns | ✅ จำเป็น | ✅ จำเป็น | ✅ จำเป็น | ทุกโมเดลต้องใช้คำนวณผลตอบแทนพอร์ต |
| Annualized Volatility | ✅ จำเป็น | ✅ จำเป็น | ❌ ไม่จำเป็นโดยตรง | MPT ใช้คำนวณ variance, HRP ใช้สร้าง covariance/distance matrix |
| Rolling mean/vol (6M, 12M) | ❌ ไม่จำเป็น | ✅ ช่วยปรับ allocation dynamic | ✅ ช่วยวิเคราะห์ tail trend | ใช้ปรับพอร์ตตาม trend ถ้าต้องการ |
| Drawdown | ❌ ไม่จำเป็น | ❌ ไม่จำเป็น | ✅ สำคัญ | CVaR ใช้สำหรับควบคุม tail risk / Max Drawdown |

- **EDA Tools:** Price chart, correlation heatmap, market regimes analysis  
- **เลือกใช้ได้:** Market regimes analysis (สำหรับ insight เพิ่มเติมหรือปรับพอร์ตเชิง dynamic)  

## 5️⃣ Portfolio Optimization (โมเดลหลัก)


| Model | จุดเด่น | เหมาะกับ | Notes |
|-------|---------|-----------|-------|
| MPT | Max Sharpe | ต้องการผลตอบแทนคุ้มความเสี่ยงสูงสุด | ต้องประมาณ μ, Σ ให้แม่น |
| HRP | Robust ต่อ noisy data | เสถียร, ลด estimation error | ใช้ clustering + recursive allocation |
| CVaR | Minimize tail risk | ลด extreme loss | ดีสำหรับ asset fat-tail |

**Parameter Calibration:**  
- **MPT:** ตรวจสอบ μ (expected returns) และ Σ (covariance matrix) ให้ realistic  
    - μ = ค่าคาดหมายผลตอบแทนของแต่ละสินทรัพย์  
        - ถ้าประเมินสูงเกินไป → พอร์ตอาจ risk สูงจริง  
        - ถ้าต่ำเกินไป → พอร์ต conservative มากไป  
    - Σ = Covariance matrix ของสินทรัพย์  
        - แสดงความสัมพันธ์ความเสี่ยงระหว่างสินทรัพย์  
        - ใช้เทคนิค robust estimation (เช่น Ledoit–Wolf) ลดผลกระทบ outliers  
- เป้าหมาย: หา weights ที่ maximize Sharpe Ratio หรือ minimize variance ภายใต้เงื่อนไข ∑w=1 และ w_i ≥ 0  

- **HRP:** เลือกวิธี clustering:  
    - Single linkage → ดู nearest neighbor  
    - Complete linkage → ดู maximum distance ระหว่างคลัสเตอร์  
    - Ward linkage → ลด variance ภายใน cluster, tree structure สมดุล  
- หลักการ: จัดสินทรัพย์เป็น cluster ตาม correlation → กระจายความเสี่ยงในแต่ละ cluster → ลด sensitivity ต่อ estimation errors ของ covariance  

- **CVaR:** เลือกระดับ confidence α (เช่น 95%) → ลดความเสียหายจาก extreme events (crashes)  

**ตัดออก:** EW, RP, BL → ใช้ baseline / เปรียบเทียบเท่านั้น  

## 6️⃣ Backtesting & Evaluation

| Metric | ความหมาย | ใช้ทำอะไร |
|--------|----------|-----------|
| CAGR | ผลตอบแทนเฉลี่ยต่อปีแบบทบต้น | วัด performance ระยะยาวของพอร์ต |
| Volatility (σ) | ความผันผวนของผลตอบแทน | วัดความเสี่ยงโดยรวมของพอร์ต |
| Sharpe Ratio | (ผลตอบแทน - risk-free rate)/σ | วัดผลตอบแทนต่อความเสี่ยงทั้งหมด |
| Sortino Ratio | ใช้ downside volatility แทน σ | วัดผลตอบแทนต่อความเสี่ยงจาก downside เท่านั้น |
| Max Drawdown (MaxDD) | ขาดทุนสูงสุดจาก peak-to-trough | วัด worst-case loss ของพอร์ต |
| Turnover | ความถี่ในการปรับน้ำหนักพอร์ต | วัดค่าใช้จ่าย transaction cost และความถี่ rebalancing |

**Input:**  
- Returns series: ผลตอบแทนรายเดือน/รายวันของแต่ละสินทรัพย์  
- Portfolio weights: น้ำหนักแต่ละสินทรัพย์ในพอร์ต  

## 7️⃣ Rebalancing & Monitoring

| วิธี | ลักษณะ | ข้อดี/ข้อควรระวัง |
|------|--------|-------------------|
| Calendar-based | ปรับพอร์ตตามเวลาที่กำหนด เช่น ทุกเดือน, ทุกไตรมาส | ง่ายต่อการจัดการ แต่บางครั้งอาจไม่ตอบสนองตลาดทัน |
| Threshold-based | ปรับพอร์ตเมื่อเบี่ยงเบนจาก target weight เกินค่าเกณฑ์ เช่น ±10% | ปรับพอร์ตเมื่อจำเป็นจริง ลด turnover แต่ต้องเฝ้าดูน้ำหนักต่อเนื่อง |
| Hybrid | รวมทั้งสองวิธี | สมดุลทั้งความถี่และความจำเป็น แต่ซับซ้อนกว่า |

**ตัวอย่างการใช้งาน:**  
- กำหนด target weight ของพอร์ตจาก MPT, HRP, CVaR  
- ตรวจสอบน้ำหนักทุกเดือน (Calendar)  
- ถ้าน้ำหนักใดเบี่ยงเบนจาก target >10% → ปรับกลับ (Threshold)  
- คำนวณ transaction cost และบันทึก Turnover ทุกครั้ง  
**Monitoring สิ่งที่ต้องติดตาม:**  
1. น้ำหนักจริงของแต่ละสินทรัพย์  
2. ผลตอบแทนสะสม (Equity curve)  
3. ค่าใช้จ่ายจากการปรับพอร์ต (Transaction cost)  
4. Max Drawdown / Volatility  
5. แจ้งเตือน เมื่อ MaxDD เกินเกณฑ์ หรือ vol พุ่งสูง  

## 8️⃣ Visualization & EDA Tools

- **Heatmap:** แสดง correlation ระหว่างสินทรัพย์ (BTC, SPX, SET)  
  - ช่วยดูว่าพอร์ตกระจายความเสี่ยงดีหรือไม่  
  - ใช้ประกอบการตัดสินใจว่า asset ไหนควรถือมาก/น้อย  
- **Price / Returns chart:**  
  - Price chart: ดูแนวโน้มราคาของแต่ละสินทรัพย์  
  - Returns chart: ดูความผันผวนและผลตอบแทน  
- **Drawdown chart:** แสดง worst-case loss (peak-to-trough) ของพอร์ตหรือ asset  

## 9️⃣ Environment & Setup

- **Language:** Python  
- **Libraries:**  
   * pandas, numpy → data manipulation ( จำเป็น สำหรับจัดการข้อมูล, คำนวณ returns, volatility ) 
    * matplotlib, seaborn → visualization (แนะนะ สำหรับ visualize graph, correlation heatmap, drawdown)
    * cvxpy → optimization solver ( ถ้าใช้ MPT/CVaR ถ้า optimize แบบ manual ต้องใช้; แต่ PyPortfolioOpt อาจซ่อน solver ให้PyPortfolioOpt → portfolio optimization ) *          *streamlit (สำหรับ dashboard interactive)ไม่จำเป็นแต่ดี  
 
**Workflow:**  
1.     1. Fetch data → 2. Preprocess → 3. Optimize (MPT/HRP/CVaR) → 4. Backtest → จำเป็นทุกขั้นตอน 5. Export / Dashboard 

## 1️⃣1️⃣ Assumptions, Limits, Ethics

* ใช้ Total Return Index → รวมปันผล
    * Total Return Index คือดัชนีที่ รวมผลตอบแทนจากราคาหุ้น + ปันผล
    * เหตุผล: ถ้าใช้แค่ราคาหุ้น จะได้ผลตอบแทนต่ำกว่าความเป็นจริง เพราะไม่ได้รวมเงินปันผล
    * ตัวอย่าง: S&P500 Total Return (SPTR) vs S&P500 Price Index (SPX)
* ผลตอบแทนและความเสี่ยงในอดีตเป็นตัวแทนของอนาคต
    * assumption นี้สำคัญสำหรับ MPT, HRP, CVaR
    * จริง ๆ อนาคตไม่แน่นอน แต่ต้องใช้ข้อมูลอดีตเป็น base 
* Limits (ข้อจำกัด / Bias)   - Survivorship Bias
    * ข้อมูลย้อนหลังอาจตัดบริษัทที่ล้มละลายไป → ทำให้ผลตอบแทนดูดีเกินจริง
    * วิธีลด: ใช้ดัชนีรวมบริษัททั้งหมดในช่วงเวลานั้น - Lookahead Bias
    * ใช้ข้อมูลที่ ณ เวลานั้นยังไม่รู้ → ทำให้ backtest ดีเกินจริง
    * วิธีลด: ใช้ข้อมูล ณ เวลาที่สามารถรู้จริงเท่านั้น -Estimation Error / Model Risk
    * MPT sensitive ต่อค่า expected return (μ) และ covariance matrix (Σ)
    * HRP ลดปัญหาได้บ้าง แต่ไม่ 100% -Market Regime Changes
    * ผลตอบแทนและความเสี่ยงเปลี่ยนตามช่วงตลาด → past data อาจไม่ตรงกับอนาคต
* Ethics (จริยธรรม) - ผลลัพธ์เป็นการศึกษา / Prototype เท่านั้น
    * ไม่ใช่คำแนะนำลงทุนจริง
    * แค่โชว์ วิธีการจัดพอร์ต / Risk Management / Optimization - ไม่ทำให้ผู้อื่นเข้าใจผิดว่าเป็น financial advice
    * ทุกผลลัพธ์ต้องมี disclaimer - Transparency
    * ระบุ assumptions, limits, methodology ให้ชัดเจน 
* ใช้ Total Return Index เพื่อให้ผลตอบแทนใกล้เคียงจริง
* ระวัง bias ทั้ง survivorship และ lookahead
* ผลลัพธ์เป็น prototype / study → ไม่ใช่คำแนะนำลงทุน
* ชี้แจง assumptions และ limits ให้ชัดเจนใน presentation  


## 1️⃣2️⃣ References

*  Markowitz, H. (1952) – Portfolio Selection
* เนื้อหา:
    * แนะนำ Modern Portfolio Theory (MPT)
    * แนวคิด mean-variance optimization → หาสัดส่วนสินทรัพย์ที่ maximize expected return ต่อความเสี่ยง
* ความสำคัญ:
    * เป็น ทฤษฎีพื้นฐาน ของการจัดพอร์ตทุกแบบ
    * ใช้ในการ optimize แบบ maximize Sharpe ratio หรือ minimize variance 
* Ledoit-Wolf (2004) – Covariance Shrinkage
* เนื้อหา:
    * วิธี ลด estimation error ของ covariance matrix
    * Shrink covariance → เพิ่มความเสถียรของพอร์ตเมื่อ asset เยอะหรือข้อมูล noisy
* ความสำคัญ:
    * ใช้ร่วมกับ MPT / HRP
    * ทำให้พอร์ต robust ต่อ noisy data 
* PyPortfolioOpt Documentation
* เนื้อหา:
    * คู่มือใช้งาน Python library สำหรับ portfolio optimization
    * มี function สำเร็จรูปสำหรับ MPT, HRP, CVaR, Black-Litterman
* ความสำคัญ:
    * ลดเวลา coding
    * สามารถทดลองหลายโมเดลง่าย ๆ
    * เหมาะกับ prototype / academic project 
* Investopedia
* เนื้อหา:
    * แหล่งความรู้เรื่องการเงินพื้นฐานและ advanced concepts
    * Topics: Diversification, Sharpe Ratio, Risk Parity, Tail Risk
* ความสำคัญ:
    * ใช้อ้างอิงแนวคิด, คำจำกัดความ, และตัวอย่างใน presentation
    * ช่วยให้คนอ่าน/ผู้ฟังเข้าใจ ศัพท์การเงินง่ายขึ้น
