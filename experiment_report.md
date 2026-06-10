# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600701
**Name:** Phạm Văn Sơn
**Date:** 10/06/2026

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Agent đã xác định chính xác sản phẩm điện tử có giá cao nhất. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Agent đã bị đánh lừa bởi giá trị ngoại lai cực đại không phải là sản phẩm điện tử hợp lệ. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi chạy với bộ dữ liệu "rác" (Garbage Data), kết quả của AI Agent bị sai lệch hoàn toàn là do chất lượng dữ liệu đầu vào quá kém. Đầu tiên, xuất hiện giá trị cực trị (Extreme Outlier) như "Nuclear Reactor" với giá trị $999999, khiến thuật toán tìm giá trị lớn nhất (idxmax) lựa chọn sai sản phẩm. Thứ hai, các dòng thiếu dữ liệu (Null values) và dữ liệu sai định dạng (Wrong type) cũng có thể làm cho model nhầm lẫn trong quá trình tổng hợp thông tin hoặc sinh lỗi khi convert type. Agent phụ thuộc rất lớn vào dữ liệu, "Garbage In, Garbage Out", nên khi đầu vào bị hỏng, đầu ra cũng sẽ bị hỏng theo.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** (Đồng ý hay không? Giải thích ngắn gọn.)

Đồng ý. Cho dù prompt có tốt đến đâu, nếu dữ liệu cung cấp cho mô hình ngôn ngữ (hoặc Agent) là dữ liệu sai lệch, ngoại lai, hoặc thiếu sót, mô hình sẽ không thể đưa ra một đáp án chính xác. Chất lượng dữ liệu quyết định giới hạn độ chính xác của câu trả lời, prompt chỉ giúp định dạng hoặc điều hướng câu trả lời đó. Do đó, việc xây dựng một đường ống xử lý dữ liệu (ETL pipeline) chuẩn xác để đảm bảo Data Observability và Data Quality là ưu tiên hàng đầu trước khi áp dụng AI.
