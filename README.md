# portfolio-construction-asset-allocation-and-optimization
A toolkit for portfolio construction, optimization, and asset allocation. Includes models to find the optimal risk/return tradeoff by visualizing the Efficient Frontier and maximizing the Sharpe Ratio, plus tools for quantitative risk analysis and strategy backtesting.

# Flowchart: Portfolio & Asset Allocation Optimization (TDSB Framework) 
          ┌─────────────────────────────┐
          │   T = Trend Analysis        │  วิเคราะห์แนวโน้มตลาด & สินทรัพย์
          └──────────────┬──────────────┘
                         │
     ┌───────────────────┴────────────────────┐
     │                                        │
1. กำหนดเป้าหมายลงทุน               2. วิเคราะห์แนวโน้มตลาด  
   • กระแสเงินสด                       • หุ้น, พันธบัตร, Crypto  
   • การเติบโต                         • S&P500, Bitcoin, SET Index  
   • ลดความเสี่ยง                     • ปัจจัยเศรษฐกิจมหภาค  
     │
     ▼
┌─────────────────────────────┐
│   D = Data Analysis         │   วิเคราะห์ข้อมูลเชิงปริมาณ
└──────────────┬──────────────┘
               │
     ┌─────────┴───────────┐
     │                     │
3. รวบรวมข้อมูลย้อนหลัง  4. วิเคราะห์สถิติพื้นฐาน
   • ราคาย้อนหลัง 3,5,10 ปี     • ผลตอบแทนเฉลี่ย (Mean Return)  
   • ใช้ Yahoo Finance / API     • ความผันผวน (Volatility)  
                                 • Correlation Matrix
                                 • Sharpe Ratio, Max Drawdown
     │
     ▼
┌─────────────────────────────┐
│   S = Strategy Development  │   วางกลยุทธ์ & จัดพอร์ต
└──────────────┬──────────────┘
               │
     ┌─────────┴───────────┐
     │                     │
5. กำหนดระดับความเสี่ยง   6. เลือก Asset Allocation Model
   • Aggressive / Moderate /      • Strategic (คงที่)  
     Conservative                • Tactical (ตามตลาด)  
                                 • Dynamic (อัตโนมัติ)
     │                     │
     └─────────────┬───────┘
                   │
7. Portfolio Optimization  
   • Markowitz (Mean-Variance)  
   • Black-Litterman  
   • Monte Carlo Simulation  
   • หาจุด **Efficient Frontier**  
     │
     ▼
┌─────────────────────────────┐
│   B = Backtesting          │   ทดสอบพอร์ตย้อนหลัง
└──────────────┬──────────────┘
               │
     ┌─────────┴───────────┐
     │                     │
8. ทดสอบกับ Historical Data  
   • CAGR, Sharpe Ratio  
   • Sortino Ratio  
   • Max Drawdown
     │
9. เปรียบเทียบ Benchmark  
   • S&P500, SET Index, Bitcoin
     │
10. ปรับกลยุทธ์ & Rebalancing  
   • ปรับพอร์ตทุก 3-6 เดือน  
   • ปรับเมื่อสินทรัพย์เบี่ยงเบนจากแผน
     │
     ▼
 ┌────────────────────────────┐
 │  ✅ พอร์ตที่เหมาะสมพร้อมใช้งานจริง │
 └────────────────────────────┘

📌 Portfolio and Asset Allocation and Optimization
โปรเจค: วิเคราะห์และสร้างพอร์ตการลงทุนที่เหมาะสม โดยใช้ ข้อมูลจริง และเทคนิคการทำ Asset Allocation และ Portfolio Optimization ร่วมกับการสร้างโมเดล Machine Learning/Optimization
📖 Table of Contents
1. Project Overview
2. Objectives
3. Data Science Life Cycle
3.1 Problem Definition
3.2 Data Collection
3.3 Data Preprocessing
3.4 Exploratory Data Analysis (EDA)
3.5 Modeling & Portfolio Optimization
3.6 Evaluation & Backtesting
3.7 Deployment & Visualization
4. Models Used
5. Datasets
6. Tools & Libraries
7. Expected Outcomes
8. References

1. Project Overview
โปรเจคนี้เกี่ยวข้องกับการ สร้างและปรับพอร์ตการลงทุน โดยใช้ข้อมูลจริงของ Bitcoin, S&P 500, SET Index และสินทรัพย์อื่น ๆ มาวิเคราะห์เพื่อหากลยุทธ์การจัดสรรสินทรัพย์ (Asset Allocation) และหาพอร์ตที่ให้ผลตอบแทนดีที่สุดภายใต้ความเสี่ยงที่ยอมรับได้ (Portfolio Optimization)

2. Objectives
ทำความเข้าใจ Portfolio, Asset Allocation, Optimization และเหตุผลที่ต้องใช้
วิเคราะห์ผลตอบแทนและความเสี่ยงของสินทรัพย์ เช่น Bitcoin, S&P 500, SET Index
ออกแบบกลยุทธ์การลงทุนทั้ง ระยะสั้น และ ระยะยาว
คำนวณว่าต้องใช้เงินลงทุนเท่าไหร่เพื่อให้บรรลุเป้าหมาย
ทำ Backtesting และ Simulation เพื่อตรวจสอบความถูกต้องของกลยุทธ์
เปรียบเทียบผลลัพธ์ของโมเดลและเลือกวิธีที่เหมาะสมที่สุด

3. Data Science Life Cycle
3.1 Problem Definition
โจทย์:
“วิเคราะห์ข้อมูลสินทรัพย์ย้อนหลัง 10 ปี และสร้างพอร์ตการลงทุนที่เหมาะสม พร้อมคำนวณผลตอบแทน, ความเสี่ยง และกลยุทธ์การปรับพอร์ต”
สิ่งที่ต้องตอบให้ได้:
ต้องลงทุนเงินเท่าไหร่เพื่อให้ได้กำไรตามเป้าหมาย
จะเลือกลงทุนในสินทรัพย์อะไรบ้าง เช่น Bitcoin, หุ้นไทย, หุ้นสหรัฐ, พันธบัตร ฯลฯ
พอร์ตที่เหมาะสมที่สุดใน 3 มุมมอง:
ความเสี่ยงต่ำ → เน้นความปลอดภัย
ความเสี่ยงปานกลาง → ผลตอบแทนพอสมควร
ความเสี่ยงสูง → ลุ้นกำไรสูง

3.2 Data Collection
แหล่งข้อมูลหลัก:
Yahoo Finance → ใช้ yfinance API ดึงข้อมูลราคา
SET Index Thailand → ดัชนีตลาดหุ้นไทย
[CoinMarketCap / Binance API] → ข้อมูล Bitcoin และ Crypto อื่น ๆ
ข้อมูลที่ต้องใช้:
ราคาปิดรายวัน (Close Price)
ปริมาณซื้อขาย (Volume)
ผลตอบแทนรายวัน / รายเดือน (Returns)
ดัชนีตลาดและตัวชี้วัดเศรษฐกิจที่เกี่ยวข้อง
ช่วงเวลา:
ย้อนหลัง 10 ปี, 5 ปี, และ 3 ปี

3.3 Data Preprocessing
Cleaning → จัดการ Missing Values, Outliers
Feature Engineering → สร้างคอลัมน์ใหม่ เช่น Daily Return, Volatility
Normalization / Scaling → ทำให้ข้อมูลอยู่ในสเกลเดียวกัน
Handling Time Series → จัดเรียงข้อมูลตามเวลา

3.4 Exploratory Data Analysis (EDA)
วิเคราะห์ความสัมพันธ์ระหว่างสินทรัพย์
ดู Distribution ของผลตอบแทน
วิเคราะห์ Risk vs Return Trade-off
Visualization ตัวอย่าง:
กราฟราคาย้อนหลัง
Histogram ของผลตอบแทน
Correlation Heatmap

3.5 Modeling & Portfolio Optimization
🔹 ขั้นตอนการสร้างโมเดล
คำนวณผลตอบแทนและความเสี่ยง
Expected Return (ค่าเฉลี่ยของผลตอบแทน)
Covariance & Correlation Matrix
Volatility (ความผันผวน)
ทำ Asset Allocation
จัดสรรสัดส่วนการลงทุนในสินทรัพย์ต่าง ๆ
Portfolio Optimization
ใช้โมเดล Machine Learning / Optimization:
Modern Portfolio Theory (MPT) → ของ Markowitz
Black-Litterman Model → รวมมุมมองนักลงทุน
Monte Carlo Simulation → จำลองผลลัพธ์หลาย ๆ สถานการณ์
Risk Parity → จัดพอร์ตให้แต่ละสินทรัพย์มีความเสี่ยงใกล้เคียงกัน

3.6 Evaluation & Backtesting
ใช้ข้อมูลย้อนหลังทดสอบโมเดล
ตัวชี้วัดที่ใช้ประเมิน:
CAGR → ผลตอบแทนเฉลี่ยต่อปี
Sharpe Ratio → ผลตอบแทนต่อความเสี่ยง
Sortino Ratio → คล้าย Sharpe แต่เน้น Downside Risk
Maximum Drawdown → ขาดทุนสูงสุดที่เคยเกิดขึ้น
เปรียบเทียบ พอร์ตที่ได้ กับ Benchmark:
S&P 500
SET Index
Bitcoin

3.7 Deployment & Visualization
ทำ Dashboard ด้วย Streamlit / Plotly Dash
แสดงข้อมูลสำคัญ:
ผลตอบแทนและความเสี่ยง
พอร์ตที่เหมาะสมที่สุด
กราฟพัฒนาการของพอร์ต
ตารางแสดงสัดส่วนการลงทุน

4. Models Used
Model	ใช้ทำอะไร	ข้อดี	ข้อเสีย
MPT (Markowitz)	หาพอร์ตที่ให้ผลตอบแทนสูงสุดที่ความเสี่ยงต่ำสุด	เข้าใจง่าย ใช้งานจริงได้	สมมติว่า returns เป็นปกติ ซึ่งไม่เสมอไป
Black-Litterman	รวมมุมมองนักลงทุนกับข้อมูลตลาด	ยืดหยุ่นสูง	คำนวณซับซ้อน
Monte Carlo	จำลองหลายสถานการณ์เพื่อคาดการณ์ผลลัพธ์	เหมาะกับข้อมูลที่ไม่แน่นอน	ต้องใช้คอมพิวเตอร์ประมวลผลสูง
Risk Parity	จัดพอร์ตให้ทุกสินทรัพย์มีความเสี่ยงใกล้กัน	ลดการกระจุกตัว	ไม่เหมาะกับสินทรัพย์ที่มี correlation สูง

5. Datasets
Dataset	Source	Frequency	Period
Bitcoin Price	Binance API / Yahoo	Daily	2015 - 2025
S&P 500 Index	Yahoo Finance	Daily	2010 - 2025
SET Index	SET.or.th	Daily	2010 - 2025

6. Tools & Libraries
Python
pandas, numpy → จัดการข้อมูล
matplotlib, seaborn, plotly → Visualization
scikit-learn → Machine Learning
cvxpy / PyPortfolioOpt → Portfolio Optimization
yfinance → ดึงข้อมูลหุ้น
Dashboard → Streamlit / Dash
Database → PostgreSQL / SQLite

7. Expected Outcomes
พอร์ตการลงทุนที่เหมาะสมที่สุดภายใต้ระดับความเสี่ยงที่ยอมรับได้
Dashboard แสดงข้อมูลผลตอบแทน, ความเสี่ยง และการจัดสรรพอร์ต
ความเข้าใจเชิงลึกเกี่ยวกับ Asset Allocation & Optimization
Insight จากการวิเคราะห์ Bitcoin, S&P500, และ SET Index

8. References
Yahoo Finance API
PyPortfolioOpt Docs
Markowitz Portfolio Theory
Black-Litterman Model
