# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600306
**Name:** Trần Quốc Khánh
**Date:** 15-04-2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Agent trả về chính xác giá laptop trong processed_data.csv |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 0 | Agent trả về giá của Nuclear Reactor thay vì giá laptop |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Sai lệch kiểu dữ liệu (Wrong Data Types): Nếu cột giá tiền bị lẫn lộn giữa định dạng chuỗi (string) và số (numeric), Agent có thể thực hiện phép so sánh dựa trên bảng chữ cái thay vì giá trị toán học. Điều này khiến các con số lớn bị nhận diện sai hoặc tính toán nhầm lẫn.
Khi nhiều bản ghi có cùng một ID nhưng thông tin khác nhau, Agent sẽ rơi vào tình trạng xung đột dữ liệu. Nó có thể ghi đè dữ liệu đúng bằng dữ liệu rác hoặc lấy ngẫu nhiên một bản ghi không chính xác.
Nếu các trường dữ liệu quan trọng bị trống, Agent thường cố gắng "lấp đầy" khoảng trống bằng cách suy luận dựa trên dữ liệu gần nhất hoặc dữ liệu có sẵn. Trong trường hợp này, khi không tìm thấy thông tin Laptop hợp lệ do lỗi định dạng, nó đã chọn thực thể khả thi nhất còn sót lại trong bộ nhớ—chính là chiếc lò phản ứng hạt nhân.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Tôi đồng ý, để xây dựng một Agent tin cậy, việc làm sạch và quản trị dữ liệu (Data Cleaning) phải được ưu tiên trước khi tối ưu hóa câu lệnh. Một Prompt trung bình trên một bộ dữ liệu sạch luôn mang lại giá trị thực tế cao hơn một Prompt hoàn hảo trên một bộ dữ liệu rác.
