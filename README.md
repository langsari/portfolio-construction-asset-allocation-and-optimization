# portfolio-construction-asset-allocation-and-optimization
A toolkit for portfolio construction, optimization, and asset allocation. Includes models to find the optimal risk/return tradeoff by visualizing the Efficient Frontier and maximizing the Sharpe Ratio, plus tools for quantitative risk analysis and strategy backtesting.

📌 Portfolio and Asset Allocation and Optimization

1) What & Why (คืออะไร / ทำไมต้องทำ)
🔹 Portfolio, Asset Allocation, Optimization คืออะไร
Portfolio: ชุดของสินทรัพย์ที่ลงทุนร่วมกัน (เช่น BTC, S&P500, SET)
Asset Allocation: การกำหนด “สัดส่วน” เงินลงทุนในแต่ละสินทรัพย์เพื่อให้เหมาะกับความเสี่ยง/เป้าหมาย
Optimization: คณิตศาสตร์/อัลกอริทึมเพื่อ “ค้นหาสัดส่วนที่ดีที่สุด” ภายใต้เงื่อนไข เช่น max Sharpe, min risk
🔹 ทำไมต้องทำโปรเจกต์นี้
แปลง เป้าหมายการเงิน → เป็น สัดส่วนพอร์ตที่ปฏิบัติได้
ฝึกใช้ ข้อมูลจริง + เทคนิครวมสถิติ/ML/Optimization
เรียนรู้ การจัดการความเสี่ยง (risk management) แบบใช้งานจริง

2) DSLC Roadmap (กรอบการทำงานแบบ Data Science Life Cycle)
   ( โปรเจคนี้ใช้กรอบการทำงาน Data Science Life Cycle (DSLC) ในการวิเคราะห์การสร้างพอร์ตการลงทุน, 
     การจัดสัดส่วนสินทรัพย์ และการหาสัดส่วนที่เหมาะสมที่สุด โดยใช้ข้อมูลย้อนหลังของ BTC, S&P500 และ SET เพื่อหา กลยุทธ์การลงทุนที่ให้ผลตอบแทนสูงสุดภายใต้ความเสี่ยงที่ยอมรับได้ )

   - Problem Definition: (การกำหนดปัญหา) ระบุเป้าหมาย/ความเสี่ยง/ข้อจำกัด
     (ในขั้นตอนนี้เราจะ:
     ระบุ เป้าหมายของการลงทุน → เช่น ต้องการผลตอบแทนเฉลี่ยต่อปีเท่าไร, ความเสี่ยงที่รับได้
     ระบุ ความเสี่ยงที่ยอมรับได้ → เช่น ขาดทุนสูงสุดไม่เกิน 20%
     กำหนด ข้อจำกัด → เช่น งบลงทุน, สินทรัพย์ที่ลงทุนได้, ความถี่การปรับพอร์ต
     ผลลัพธ์ที่ได้:
     ขอบเขตของโปรเจค
     ตัวชี้วัดความสำเร็จ (KPIs) เช่น CAGR, Sharpe Ratio)
     
  - Data Collection:(การเก็บข้อมูล) ดึงข้อมูลย้อนหลังของ BTC, S&P500, SET (10/5/3 ปี)
    ในขั้นตอนนี้เราจะ:
    ดึงข้อมูลย้อนหลังของสินทรัพย์ที่สนใจ เช่น BTC, S&P500, SET
    ระบุช่วงเวลาข้อมูล 10 ปี / 5 ปี / 3 ปี
    ข้อมูลที่เก็บ:
    วันที่ (Date)
    ราคาปิด (Close Price)
    ปริมาณซื้อขาย (Volume)
    ผลลัพธ์ที่ได้:
    ไฟล์ CSV/Parquet ของข้อมูลราคา
    โค้ดสำหรับดึงข้อมูลด้วย Python เช่น yfinance, pandas_datareader

Preprocessing:(การเตรียมข้อมูล) Clean, align time index, สร้างฟีเจอร์ (returns, vol, rolling stats)
 - ขั้นตอนนี้คือการทำให้ข้อมูล พร้อมสำหรับการวิเคราะห์และ Modeling
 - Clean Data → ลบค่า Missing, จัดการ Outliers
 - Align Time Index → ทำให้ทุกสินทรัพย์มีวันที่ตรงกัน
 - สร้างฟีเจอร์ใหม่ (Feature Engineering) เช่น:
 - Daily Returns →  (Pt−Pt−1)/Pt−1 
​ - Volatility → ความผันผวน
 - Rolling Statistics → ค่าเฉลี่ยหรือความผันผวนเคลื่อนที่
   ผลลัพธ์ที่ได้:
   DataFrame พร้อมสำหรับ EDA และ Modeling

EDA: ดู distribution, correlation, regimes
  ในขั้นตอนนี้เราจะ:
 - วิเคราะห์ข้อมูลเบื้องต้น
 - สร้างกราฟและสรุป Insight
 - สิ่งที่ควรดู:
 - Distribution ของผลตอบแทน
 - Correlation ระหว่างสินทรัพย์
 - Market Regimes → ขาขึ้น ขาลง Sideway
   ผลลัพธ์ที่ได้:
   กราฟ Histogram, Heatmap, Rolling Volatility
   ตาราง Correlation
   Insight สำหรับ Modeling

Modeling & Optimization: EW, Risk Parity, Markowitz, HRP, BL, CVaR
เราจะสร้างและทดสอบ โมเดล Portfolio Optimization หลายแบบ เช่น:

   โมเดล	                                   แนวคิด	                      ความซับซ้อน
 EW (Equal Weight)  	                จัดสัดส่วนเท่ากันทุกสินทรัพย์	                  ง่าย
 Risk Parity	                       กระจายความเสี่ยงให้เท่ากัน	                 ปานกลาง
 Markowitz	                   หาสัดส่วนที่ดีที่สุดระหว่างผลตอบแทนและความเสี่ยง	        ยาก
 HRP	ใช้ Clustering                    วิเคราะห์ความสัมพันธ์	                 ปานกลาง-ยาก
  BL (Black-Litterman)	         ผสมข้อมูลตลาดกับความเห็นผู้เชี่ยวชาญ              	ยาก
  CVaR	                               ควบคุมความเสี่ยงกรณีตลาด Crash	         ยากมาก
 ผลลัพธ์ที่ได้:
 ตาราง Optimal Weights
 Efficient Frontier Graph
 เปรียบเทียบผลลัพธ์แต่ละโมเดล


Backtesting & Evaluation: (ทดสอบย้อนหลังและประเมินผล)  CAGR, Sharpe/Sortino, MaxDD, turnover, costs
ขั้นตอนนี้คือการทดสอบโมเดลกับ ข้อมูลย้อนหลัง และวัดประสิทธิภาพ
 ตัวชี้วัดสำคัญ:
 - CAGR → ผลตอบแทนเฉลี่ยต่อปี
 - Sharpe / Sortino Ratio → วัดผลตอบแทนต่อความเสี่ยง
 - Max Drawdown → การขาดทุนสูงสุด
 - Turnover → ความถี่การซื้อขาย
 - Costs → ค่าธรรมเนียม
   ผลลัพธ์ที่ได้:
   ตารางเปรียบเทียบ Performance 
   กราฟ Equity Curve

Deployment: โน้ตบุ๊ก/สคริปต์ + Dashboard + README + แผน rebalancing
ในขั้นตอนนี้เราจะ:
- จัดทำ Notebook / Script สำหรับรันวิเคราะห์
- สร้าง Dashboard แสดงผลลัพธ์ Portfolio Optimization และ Backtest
- จัดทำ README.md อธิบายขั้นตอน, วิธีใช้งาน และผลลัพธ์
- เขียน แผน Rebalancing → ปรับพอร์ตตามรอบเวลา


4) Goals → Money (ตั้งเป้าหมายการลงทุน & คำนวณเงินที่ต้องใช้)
3.1 ระบุเป้าหมาย
รายได้ต่อปี/เดือนที่อยากได้ (เช่น 60,000 บาท/ปี)
ขอบเขตความเสี่ยง: อนุญาตให้ขาดทุนชั่วคราวได้เท่าไร (เช่น MaxDD ≤ 20%)
ขอบเขตเวลา: 3/5/10 ปี
3.2 คำนวณเงินที่ต้องใช้ (ตัวอย่างแนวคิด)
เป้ารายได้ต่อปีด้วยอัตราถอน (withdrawal rate)
เงินต้นที่ต้องมี ≈ รายได้ต่อปี / อัตราถอน
ตัวอย่าง: 60,000 / 0.04 ≈ 1,500,000 บาท
ด้วยคาดการณ์ผลตอบแทนเฉลี่ยต่อปี (μ)
ถ้าต้องการรายได้ 60,000 และคาดหวัง μ = 6% → เงินต้น ~ 1,000,000 (ไม่รวมความผันผวน/ภาษี)
ด้วย Dividend Yield/คูปองพันธบัตร
รายได้=เงินต้น×yield → เงินต้น≈รายได้/ผลตอบแทนจากกระแสเงินสด
ใช้ Monte Carlo เพื่อแจกแจงความน่าจะเป็นของผลลัพธ์ (ไม่ยึดค่ากลางอย่างเดียว)

5) Data (แหล่งข้อมูล & โครงสร้างข้อมูล)
4.1 แหล่งข้อมูล
Bitcoin (BTC-USD): Yahoo Finance / Exchange API
S&P 500: ^GSPC (ราคา) หรือ ^SP500TR (รวมเงินปันผล)
SET Index: SET / SETTRADE
ความถี่: รายวัน (แนะนำ resample เป็น รายเดือน เวลา optimize เพื่อลด noise)

6) Preprocess & Features (การเตรียมข้อมูล/ฟีเจอร์)
จัดการ missing values, ปรับ timezone, ตรวจ outliers
จัดให้ index ตรงกัน (inner join บนวันที่ร่วมกัน)
สร้าง ผลตอบแทน:
รายวัน/เดือน: ret_t = P_t/P_{t-1} - 1
Annualize: mean×freq, cov×freq (freq=12 สำหรับรายเดือน, 252 สำหรับรายวัน)
ฟีเจอร์เสริม: rolling mean/vol (เช่น 6M, 12M), drawdown, z-score
ใช้ robust covariance (เช่น Ledoit–Wolf) ลดผลกระทบ extreme moves

7) EDA (สำรวจและทำความเข้าใจข้อมูล)
สิ่งที่ควรทำ:
กราฟราคาและผลตอบแทน (10/5/3 ปี)
Distribution ของผลตอบแทน (fat tails, skew)
Correlation heatmap (ระหว่าง BTC/SPX/SET)
ระบบ market regimes เบื้องต้น (เช่น high/low vol) เพื่อเข้าใจพฤติกรรมช่วงต่างๆ

8) Asset Allocation (การจัดสัดส่วนสินทรัพย์)
เป้าหมาย: กระจายความเสี่ยงให้เหมาะกับเป้าหมาย/ข้อจำกัด
วิธีพื้นฐาน:
Equal Weight (EW): เท่า ๆ กันทุกสินทรัพย์
Volatility Targeting: ให้น้ำหนักแปรผกผันกับความผันผวน
Risk Parity: ให้ “ส่วนแบ่งความเสี่ยง” ของแต่ละสินทรัพย์ใกล้เคียงกัน
Constraints ตัวอย่าง: no shorting, weight bounds, sector caps, turnover limit

9) Portfolio Optimization (การหาพอร์ตที่เหมาะสมที่สุด)
8.1 Markowitz Mean-Variance (MPT)
maximize Sharpe หรือ minimize variance ที่คุม return
สูตร:
R_p = w·μ
σ_p^2 = wᵀΣw
เงื่อนไข: ∑w=1, 0≤w_i≤1 (no short)

8.2 CVaR / Mean-CVaR (จัดการหางความเสี่ยง)
ลดผลกระทบเหตุการณ์ tail risk มากกว่า variance
ใช้ cvxpy หรือ PyPortfolioOpt ทำ optimization แบบ CVaR ได้
8.3 Hierarchical Risk Parity (HRP)
จัดกลุ่มสินทรัพย์ด้วย clustering แล้วเฉลี่ยความเสี่ยงตามลำดับชั้น
robust ต่อ estimation error ของ covariance
8.4 Black-Litterman (BL)
ผสม “มุมมองของนักลงทุน” เข้ากับ “สมดุลตลาด”
เหมาะเมื่อมีความเห็นเฉพาะเกี่ยวกับสินทรัพย์บางตัว
แนะนำทดลอง อย่างน้อย 6 โมเดล: EW, Vol-Target, Risk Parity, MPT (Max Sharpe), HRP, CVaR; (ถ้าเวลาพอ เพิ่ม BL)

9) Backtesting & Evaluation (ทดสอบย้อนหลัง & ประเมินผล)
9.1 หน้าต่างทดสอบ
ระยะเวลา: 10 ปี, 5 ปี, 3 ปี
ความถี่ rebalancing: รายเดือน/ไตรมาส
ใส่ ต้นทุนธุรกรรม (เช่น 10–30 bps ต่อการปรับ) และ slippage
9.2 Metrics หลัก
CAGR: ((1+R_total)^(1/years))-1
Volatility (ann.): std(ret)*sqrt(freq)
Sharpe: (μ_p - r_f)/σ_p (ตั้ง r_f≈0 ได้ถ้าไม่มีข้อมูล)
Sortino: ใช้ downside σ แทน
Max Drawdown: min( (peak - trough)/peak )
Calmar: CAGR/|MaxDD|
Turnover: ค่าเฉลี่ย sum(|w_t - w_{t-1}|)

10) Rebalancing & Monitoring (ติดตามและปรับพอร์ต)
วิธีปรับพอร์ต
Calendar: ทุกเดือน/ไตรมาส/ปี
Threshold: เมื่อเบี่ยงเบนเกิน ±x% จาก target
Hybrid: Calendar + Threshold 


|        โมเดล                | แนวคิด                  การจัดการความเสี่ยง              เหมาะกับ                 ข้อจำกัด                 
| -------------------- | ---------------------- | ------------------------- | --------------------   --------------------
| **EW**               | เท่า ๆ กัน               | กระจายแบบง่าย               | มือใหม่/เบสไลน์          | ไม่คำนึง vol/corr        
| **Vol-Target**       | w ∝ 1/σ                | ลด exposure สินทรัพย์ผันผวน    | ตลาดผันผวนสูง           | เพิกเฉย correlation      
| **Risk Parity**      | เท่า risk contribution  | ลดการกระจุกตัวความเสี่ยง       | พอร์ตหลากหลาย          | ประมาณการ σ/Σ สำคัญ      
| **MPT (Max Sharpe)** | mean-var               | จาก Σ และ μ                | เมื่อตลาดนิ่งพอ           | overfit/fragile          
| **HRP**              | tree-clustering        | robust ต่อ error            | สินทรัพย์หลายตัว          | พึ่งพาโครงสร้างคลัสเตอร์ 
| **CVaR**             | minimize tail loss     | คุมด้านหาง                   | tail risk concern     | คำนวณหนัก                
| **BL**               | รวมมุมมอง               | กำหนดความเชื่อ (τ,Ω)          | ผู้มีวิวเชิงคาดการณ์        | ตั้งค่าพารามิเตอร์ยาก    

12) Investor Playbooks (นักลงทุนจะลงทุนยังไง)
ระยะสั้น (1–2 ปี): EW / Vol-Target, Rebalance ถี่กว่า, เน้นคุม MaxDD
ระยะกลาง (3–5 ปี): Risk Parity / HRP, เน้นเสถียรภาพ, Threshold Rebalancing
ระยะยาว (5–10 ปี): MPT/BL + tilt สินทรัพย์เติบโต (SPX, ส่วนหนึ่ง BTC), ใส่กติกา MaxDD
การตัดสินใจวันนี้ & อนาคต – ใช้ข้อมูลแบบไหน
วันนี้: ระดับราคา/ผลตอบแทนล่าสุด, vol ล่าสุด, correlation ปัจจุบัน, macro high-level (เงินเฟ้อ/ดอกเบี้ย)
อนาคต: ภาพรวม valuation, momentum/mean-reversion, risk regime, scenario analysis (shock rates, crisis)

13) Folder Structure (โครงสร้างโปรเจกต์)
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




