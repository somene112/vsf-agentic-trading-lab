---
id: autonomous-trading-agents-research-notes
title: "Autonomous Trading Agents - Research Notes"
sidebar_label: "Autonomous Trading Agents"
description: "Ghi chú nghiên cứu ban đầu về autonomous trading agents thông qua 3 paper: LLM agent survey, FinRL và TradingAgents."
tags:
  - AI
  - Finance
  - Trading
  - LLM Agent
  - Reinforcement Learning
  - Multi-Agent
---

# Báo cáo tìm hiểu: Autonomous Trading Agents

**Người thực hiện:** Phúc  
**Ngày báo cáo:** 25/05/2026  
**Mục tiêu:** Ghi lại những gì đã tìm hiểu ban đầu về chủ đề **autonomous trading agents** để dễ tra cứu lại sau này.

---

## 1. Bối cảnh tìm hiểu

Hôm nay em đã tìm hiểu sơ bộ về chủ đề **autonomous trading agents** thông qua 3 paper chính:

1. **Large Language Model Agent in Financial Trading: A Survey**
2. **FinRL: Deep Reinforcement Learning Framework to Automate Trading in Quantitative Finance**
3. **TradingAgents: Multi-Agents LLM Financial Trading Framework**

Mục tiêu hiện tại chưa phải là xây dựng hệ thống hoàn chỉnh ngay, mà là nắm được bức tranh tổng quan: autonomous trading agent là gì, các hướng tiếp cận phổ biến, và điểm khác nhau giữa agent dựa trên **reinforcement learning** và agent dựa trên **LLM/multi-agent**.

---

## 2. Autonomous Trading Agents là gì?

**Autonomous trading agents** có thể hiểu là các hệ thống AI có khả năng tự động hỗ trợ hoặc thực hiện một phần quy trình giao dịch tài chính, ví dụ:

- Thu thập dữ liệu thị trường.
- Phân tích tin tức, giá, chỉ báo kỹ thuật hoặc dữ liệu cơ bản của doanh nghiệp.
- Đưa ra nhận định về xu hướng thị trường.
- Đề xuất hành động như mua, bán, giữ, hoặc phân bổ danh mục.
- Đánh giá rủi ro trước khi ra quyết định.

Điểm quan trọng là agent không chỉ trả lời câu hỏi đơn lẻ, mà thường được thiết kế theo một vòng lặp gồm:

```text
Observe → Analyze → Decide → Act → Evaluate
```

Trong đó:

- **Observe:** thu thập dữ liệu như giá, volume, tin tức, báo cáo tài chính, sentiment.
- **Analyze:** phân tích dữ liệu bằng mô hình AI/ML, LLM, chỉ báo kỹ thuật hoặc luật tài chính.
- **Decide:** đưa ra quyết định giao dịch hoặc khuyến nghị.
- **Act:** thực hiện lệnh hoặc tạo tín hiệu giao dịch.
- **Evaluate:** backtest, đo hiệu quả, đánh giá rủi ro và cải thiện chiến lược.

:::caution
Các paper được tìm hiểu chủ yếu phục vụ mục tiêu nghiên cứu và hiểu kiến trúc hệ thống. Nội dung này không phải lời khuyên đầu tư.
:::

---

## 3. Paper 1: Large Language Model Agent in Financial Trading: A Survey

### 3.1. Mục tiêu của paper

Paper này là một bài **survey** về việc sử dụng **Large Language Model agents** trong giao dịch tài chính. Bài viết giúp tổng hợp:

- Các kiến trúc phổ biến của LLM trading agents.
- Các loại dữ liệu đầu vào thường dùng.
- Cách các agent được đánh giá bằng backtesting.
- Các thách thức và hướng nghiên cứu tiếp theo.

### 3.2. Ý chính em hiểu được

LLM có tiềm năng trong trading vì tài chính không chỉ phụ thuộc vào dữ liệu giá, mà còn phụ thuộc vào rất nhiều thông tin dạng ngôn ngữ như:

- Tin tức thị trường.
- Báo cáo tài chính.
- Thông báo của doanh nghiệp.
- Bình luận của chuyên gia.
- Sentiment từ mạng xã hội.
- Sự kiện kinh tế, chính trị, vĩ mô.

LLM agent có thể đọc, tóm tắt, suy luận và kết hợp các nguồn thông tin này để hỗ trợ quyết định giao dịch.

### 3.3. Kiến trúc thường gặp của LLM trading agent

Một kiến trúc LLM trading agent thường có các thành phần:

```text
Market Data / News / Reports
        ↓
Information Retrieval
        ↓
LLM Reasoning / Analysis
        ↓
Trading Decision
        ↓
Backtesting / Evaluation
```

Trong đó, LLM đóng vai trò như một bộ phận phân tích và suy luận, còn dữ liệu thị trường, tin tức và kết quả backtest là nguồn thông tin hỗ trợ ra quyết định.

### 3.4. Điểm đáng chú ý

Điểm quan trọng nhất của paper này là nó cho thấy hướng **LLM agent trong trading** vẫn đang ở giai đoạn nghiên cứu mạnh, có tiềm năng nhưng cũng còn nhiều rủi ro:

- LLM có thể hallucinate.
- Kết quả backtest có thể chưa phản ánh đúng thị trường thật.
- Dữ liệu tài chính dễ bị nhiễu và thay đổi nhanh.
- Trading là bài toán có rủi ro cao, không thể chỉ dựa vào khả năng sinh ngôn ngữ của LLM.
- Cần có risk management, kiểm chứng thực nghiệm và cơ chế giám sát.

---

## 4. Paper 2: FinRL: Deep Reinforcement Learning Framework to Automate Trading in Quantitative Finance

### 4.1. Mục tiêu của paper

FinRL là một framework mã nguồn mở dùng **Deep Reinforcement Learning** để tự động hóa giao dịch định lượng.

Khác với LLM agent, FinRL tập trung vào hướng:

```text
Agent học từ môi trường giao dịch → thử hành động → nhận reward → tối ưu chiến lược
```

### 4.2. Ý chính em hiểu được

FinRL coi trading là một bài toán reinforcement learning, trong đó:

- **State:** trạng thái thị trường, ví dụ giá, volume, indicator, số dư, số cổ phiếu đang nắm giữ.
- **Action:** hành động của agent, ví dụ mua, bán, giữ, phân bổ danh mục.
- **Reward:** phần thưởng, thường liên quan đến lợi nhuận, rủi ro hoặc giá trị danh mục.
- **Environment:** môi trường mô phỏng thị trường dựa trên dữ liệu lịch sử.

Agent sẽ học cách tối ưu hành động thông qua quá trình tương tác với môi trường.

### 4.3. Pipeline cơ bản của FinRL

Có thể hiểu pipeline của FinRL như sau:

```text
Data Layer → Environment Layer → Agent Layer → Backtesting / Trading
```

Trong đó:

- **Data Layer:** lấy và xử lý dữ liệu thị trường.
- **Environment Layer:** tạo môi trường mô phỏng trading.
- **Agent Layer:** huấn luyện agent bằng các thuật toán DRL.
- **Backtesting:** kiểm tra chiến lược trên dữ liệu lịch sử.
- **Trading:** có thể mở rộng sang paper/live trading.

### 4.4. Điểm đáng chú ý

FinRL hữu ích vì nó cung cấp một framework đầy đủ, giúp giảm độ khó khi xây dựng hệ thống trading bằng reinforcement learning.

Tuy nhiên, hướng DRL cũng có các thách thức:

- Dễ overfit vào dữ liệu lịch sử.
- Reward design khó.
- Thị trường thay đổi liên tục, nên chiến lược học được trong quá khứ có thể không còn hiệu quả.
- Cần tính đến phí giao dịch, thanh khoản, trượt giá và quản trị rủi ro.

---

## 5. Paper 3: TradingAgents: Multi-Agents LLM Financial Trading Framework

### 5.1. Mục tiêu của paper

TradingAgents đề xuất một framework giao dịch tài chính dùng **multi-agent LLM**, mô phỏng cách một công ty trading hoạt động với nhiều vai trò chuyên biệt.

Thay vì chỉ có một agent đưa ra quyết định, hệ thống chia thành nhiều agent, ví dụ:

- Fundamental analyst.
- Sentiment analyst.
- Technical analyst.
- Bull researcher.
- Bear researcher.
- Trader.
- Risk management team.

### 5.2. Ý chính em hiểu được

Điểm hay của TradingAgents là nó không để một LLM tự quyết định toàn bộ, mà tổ chức các agent thành một quy trình thảo luận và phản biện.

Ví dụ:

```text
Dữ liệu thị trường + tin tức + báo cáo
        ↓
Các analyst agent phân tích theo từng góc nhìn
        ↓
Bull/Bear researcher tranh luận
        ↓
Trader tổng hợp thông tin
        ↓
Risk manager kiểm tra rủi ro
        ↓
Quyết định giao dịch cuối cùng
```

Cách này giống một workflow trong công ty tài chính, nơi nhiều nhóm cùng phân tích trước khi ra quyết định.

### 5.3. Điểm đáng chú ý

TradingAgents cho thấy hướng multi-agent có thể phù hợp với trading vì trading là bài toán cần nhiều góc nhìn:

- Góc nhìn kỹ thuật.
- Góc nhìn cơ bản.
- Góc nhìn tin tức/sentiment.
- Góc nhìn rủi ro.
- Góc nhìn phản biện giữa phe lạc quan và bi quan.

Điểm em thấy quan trọng là **multi-agent không chỉ để chia việc**, mà còn để tạo cơ chế phản biện trước khi ra quyết định.

---

## 6. So sánh nhanh 3 paper

| Paper | Hướng tiếp cận chính | Vai trò trong bức tranh autonomous trading agents | Điểm em rút ra |
|---|---|---|---|
| **Large Language Model Agent in Financial Trading: A Survey** | Survey về LLM agents trong trading | Giúp hiểu tổng quan lĩnh vực, kiến trúc, dữ liệu, thách thức | LLM có tiềm năng xử lý dữ liệu ngôn ngữ tài chính nhưng cần kiểm soát hallucination và rủi ro |
| **FinRL** | Deep Reinforcement Learning | Cung cấp framework để huấn luyện agent học chiến lược trading từ dữ liệu lịch sử | Trading có thể mô hình hóa thành bài toán RL với state, action, reward, environment |
| **TradingAgents** | Multi-agent LLM framework | Mô phỏng công ty trading với nhiều agent phân tích, tranh luận và quản trị rủi ro | Multi-agent phù hợp với trading vì cần nhiều góc nhìn và cơ chế phản biện |

---

## 7. Những ý em đã nắm được sau hôm nay

Sau khi đọc 3 paper, em hiểu được một số ý cơ bản:

1. **Autonomous trading agent** là hệ thống AI có thể hỗ trợ hoặc tự động hóa một phần quá trình phân tích và ra quyết định giao dịch.
2. Có ít nhất hai hướng chính:
   - **DRL-based trading agents:** học chiến lược thông qua tương tác với môi trường giao dịch.
   - **LLM-based trading agents:** dùng LLM để đọc hiểu, phân tích và suy luận từ dữ liệu tài chính.
3. Hướng **multi-agent** đang nổi lên vì trading là bài toán phức tạp, cần nhiều vai trò như analyst, trader và risk manager.
4. Backtesting rất quan trọng, nhưng không đủ để chứng minh hệ thống hoạt động tốt trong thị trường thật.
5. Risk management là phần bắt buộc nếu muốn đưa trading agent đến gần ứng dụng thực tế.
6. Các hệ thống này hiện vẫn mang tính nghiên cứu nhiều, cần kiểm chứng kỹ trước khi áp dụng thực tế.

---

## 8. Các câu hỏi cần research tiếp

Một số câu hỏi em nghĩ nên tìm hiểu tiếp:

### 8.1. Về kỹ thuật

- Làm thế nào để đánh giá một trading agent một cách công bằng?
- Backtest cần tránh những lỗi nào như data leakage, look-ahead bias, survivorship bias?
- Có nên kết hợp LLM với reinforcement learning không?
- LLM agent nên dùng dữ liệu nào: news, price, financial report, social sentiment, hay tất cả?
- Làm sao để kiểm soát hallucination trong quyết định tài chính?

### 8.2. Về kiến trúc hệ thống

- Một trading agent thực tế cần những module nào?
- Cần thiết kế memory cho agent ra sao?
- Có nên dùng RAG để truy xuất tin tức và báo cáo tài chính không?
- Risk manager agent nên kiểm tra những gì trước khi cho phép giao dịch?
- Nên dùng single-agent hay multi-agent trong giai đoạn prototype?

### 8.3. Về thực nghiệm

- Dataset nào phù hợp để thử nghiệm ban đầu?
- Metric nào nên dùng ngoài lợi nhuận?
- Cách tính Sharpe ratio, maximum drawdown, cumulative return như thế nào?
- Làm sao so sánh agent với baseline như buy-and-hold hoặc moving average strategy?

---

## 9. Hướng phát triển tiếp theo

Nếu tiếp tục research chủ đề này, em nghĩ có thể đi theo các bước:

1. **Đọc thêm survey** để nắm taxonomy của LLM/agent trong finance.
2. **Tìm hiểu FinRL ở mức code** để hiểu cách xây environment, reward và backtest.
3. **Đọc kỹ TradingAgents** để hiểu workflow multi-agent và cách các agent giao tiếp.
4. **Làm một prototype nhỏ**, ví dụ:
   - Input: dữ liệu giá + tin tức.
   - Agent 1: technical analysis.
   - Agent 2: sentiment/news analysis.
   - Agent 3: risk check.
   - Agent cuối: đưa ra quyết định buy/sell/hold.
5. **Đánh giá bằng backtest** trên dữ liệu lịch sử và so sánh với baseline đơn giản.

---

## 10. Takeaway ngắn gọn để tra cứu nhanh

- **FinRL** đại diện cho hướng **reinforcement learning trading agent**.
- **LLM Trading Agent Survey** giúp hiểu tổng quan hướng **LLM agent trong trading**.
- **TradingAgents** đại diện cho hướng **multi-agent LLM trading framework**.
- Autonomous trading agent không chỉ là model dự đoán giá, mà là một hệ thống gồm dữ liệu, phân tích, quyết định, hành động, backtest và quản trị rủi ro.
- Muốn làm nghiêm túc cần đặc biệt chú ý: data quality, backtest validity, risk management, hallucination control và comparison với baseline.

---

## 11. Tài liệu tham khảo

1. Han Ding, Yinheng Li, Junhao Wang, Hang Chen. **Large Language Model Agent in Financial Trading: A Survey**. arXiv:2408.06361.  
   Link: https://arxiv.org/abs/2408.06361

2. Xiao-Yang Liu, Hongyang Yang, Jiechao Gao, Christina Dan Wang. **FinRL: Deep Reinforcement Learning Framework to Automate Trading in Quantitative Finance**. arXiv:2111.09395.  
   Link: https://arxiv.org/abs/2111.09395

3. Yijia Xiao, Edward Sun, Di Luo, Wei Wang. **TradingAgents: Multi-Agents LLM Financial Trading Framework**. arXiv:2412.20138.  
   Link: https://arxiv.org/abs/2412.20138

4. TradingAgents project page.  
   Link: https://tradingagents-ai.github.io/

5. TradingAgents GitHub repository.  
   Link: https://github.com/tauricresearch/tradingagents
