
### 1. Phân tích nguyên nhân & Test Cases

* **Dòng lệnh sai:**

```javascript
rawTicketCode.trim();
rawTicketCode.toUpperCase();
```

* **Nguyên nhân kỹ thuật:** Trong JavaScript, chuỗi có tính bất biến (**String Immutability**). Các phương thức như `trim()` và `toUpperCase()` không thay đổi chuỗi gốc mà trả về một chuỗi mới. Do không gán giá trị trả về vào biến mới, `rawTicketCode` vẫn giữ nguyên chuỗi cũ có khoảng trắng và chữ thường (`"   med-card-0428-ut   "`), dẫn đến các bước kiểm tra và cắt chuỗi phía sau đều sai.

#### Bảng Test Case



| **Trường hợp kiểm thử**              | **Dữ liệu đầu vào** | **Kết quả sai thực tế**                                   | **Kết quả đúng mong đợi**                             |
| ----------------------------------------------- | ------------------------------ | ------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Mã hợp lệ có khoảng trắng thừa** | `"   med-card-0428-ut   "`   | - Hợp lệ:`false`- Khoa:` -c`- In:` med \| card \| 0428 \| ut ` | - Hợp lệ:`true`- Khoa:`CARD`- In:`MED \| CARD \| 0428 \| UT` |
| **Mã thường không ưu tiên**         | `"  med-dent-1012-no  "`     | - Hợp lệ:`false`- Khoa:`  m`- In:`med \| dent \| 1012 \| no`   | - Hợp lệ:`true`- Khoa:`DENT`- In:`MED \| DENT \| 1012 \| NO` |
