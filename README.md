[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112757&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** mnt250723@gmail.com
**Name:** Phạm Văn Sơn

---

## Mô tả

Bài lab này tập trung vào việc xây dựng một Data Pipeline (ETL) đơn giản để làm sạch dữ liệu và kiểm chứng vai trò quan trọng của dữ liệu sạch đối với hiệu năng của một AI Agent. Chúng ta thực hiện:
- Extract, Validate, Transform, Load để xử lý file raw_data.json thành processed_data.csv.
- Sinh dữ liệu Garbage Data để so sánh.
- Chạy Agent Simulation để thấy rằng "Garbage in, Garbage out" - dữ liệu tồi sẽ làm suy giảm nghiêm trọng độ chính xác của AI Agent.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chạy ETL Pipeline
```bash
python solution.py
```

### Chạy Agent Simulation (Stress Test)
```bash
# Tạo file garbage_data.csv trước khi chạy
python generate_garbage.py
python agent_simulation.py
```

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output của pipeline
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Kết quả

Pipeline đã chạy thành công. Quá trình xử lý lọc ra 2 bản ghi không hợp lệ (một sản phẩm có giá âm và một sản phẩm không có phân loại). Kết quả: 3 records được lưu vào `processed_data.csv`. Agent chạy trên tập Clean Data đưa ra câu trả lời chính xác, trong khi trên tập Garbage Data bị đánh lừa bởi dữ liệu outlier cực trị ("Nuclear Reactor" với giá $999999).
