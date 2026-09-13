# Thiên Cơ Số

> Ứng dụng Android hiện đại dành cho việc phân tích và thống kê kết quả **Xổ số Kiến thiết Miền Bắc (XSMB)**, với hệ thống tính điểm và xếp hạng 00–99 dựa trên dữ liệu lịch sử.

![Platform](https://img.shields.io/badge/Platform-Android-green?logo=android)
![Language](https://img.shields.io/badge/Language-Kotlin-7F52FF?logo=kotlin)
![UI](https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?logo=jetpackcompose)
![Architecture](https://img.shields.io/badge/Architecture-MVVM-orange)
![Min SDK](https://img.shields.io/badge/Min%20SDK-24+-blue)
![License](https://img.shields.io/badge/License-Private-lightgrey)

---

## Giới thiệu

**Thiên cơ số** là chương trình phân tích thống kê, được viết hoàn toàn bằng **Kotlin + Jetpack Compose** theo kiến trúc **MVVM**. Ứng dụng giúp người dùng:

- Tính điểm và xếp hạng 100 con số (00–99) dựa trên nhiều thuật toán thống kê lịch sử.
- Phân tích chuyên sâu kết quả XSMB (Lô gan, tần suất, đầu–đuôi…).
- Backtest hiệu suất thuật toán trên dữ liệu thực tế nhiều ngày.
- Giả lập đặt cược để kiểm tra chiến lược.

Ứng dụng tích hợp sẵn **hơn 7.500 ngày kết quả XSMB** (từ năm 2005 đến nay) và hỗ trợ đồng bộ dữ liệu mới từ server GitHub.

> **Lưu ý quan trọng**: Ứng dụng mang tính chất **phân tích thống kê & giải trí**. Kết quả dự đoán không đảm bảo chính xác 100%. Người dùng cần sử dụng có trách nhiệm.

---

## Tính năng chính

### 1. Dự đoán & Bảng xếp hạng điểm (Main Prediction)

- Mỗi con số 00–99 bắt đầu với **điểm gốc 100.0**.
- Các thuật toán cộng/trừ điểm dựa trên dữ liệu lịch sử **trước ngày dự đoán**.
- Hiển thị nổi bật:
  - **TOP 3 Golden Picks** (con số có điểm cao nhất)
  - Top 5 và Top 10
- Tự động đối chiếu với kết quả thực tế (nếu đã có):
  - Số nháy trúng (1 nháy, 2 nháy…)
  - Giải Đặc biệt
- Bộ lọc, tìm kiếm số và sắp xếp theo:
  - Điểm tăng/giảm
  - Thứ tự số 00–99

### 2. Quản lý & Tối ưu thuật toán (Algorithm Manager + Backtesting)

Ứng dụng hỗ trợ **4 thuật toán lõi** có thể bật/tắt và điều chỉnh trọng số (0.1x – 3.0x):

| # | Tên thuật toán | Mô tả ngắn |
|---|----------------|------------|
| 01 | **Điểm Xuất Hiện & Tần Suất (V13)** | Chu kỳ 7/30 ngày, tần suất ngắn/dài hạn, láng giềng giải ĐB, phạt lặp Top 3 |
| 02 | **Số Ngày Chưa Về & Mốc Thưởng** | Lô gan, thưởng mốc 3/7/10/15 ngày, cộng dồn tiến trình |
| 03 | **Phạt Vị Trí Giải Thưởng** | Trừ điểm dựa trên vị trí giải hôm trước (giải cao bị trừ nhiều hơn) |
| 04 | **Phạt/Thưởng Tần Suất 30 Ngày** | Trừ điểm số ít xuất hiện, thưởng số chưa về lần nào trong 30 ngày |

**Tính năng Backtest**:
- Đánh giá tỷ lệ trúng thực tế trong **7 / 14 / 30 / 60 ngày**.
- Bảng kết quả chi tiết từng ngày.
- Hỗ trợ xuất kết quả đánh giá.

Người dùng có thể tùy chỉnh chi tiết từng tham số của thuật toán.

### 3. Xem Kết quả XSMB & Phân tích chuyên sâu

- Bảng kết quả đầy đủ **27 giải** truyền thống (từ Giải Đặc biệt đến Giải Bảy).
- Thống kê **Đầu – Đuôi** lô tô từ 0–9.
- Phân tích chuyên sâu:
  - Top 10 **Lô Gan** (số ngày vắng mặt lâu nhất)
  - Top 10 số về **nhiều nhất** / **ít nhất** trong 30 / 60 / 90 ngày

### 4. Đồng bộ dữ liệu & Hướng dẫn



- Cơ sở dữ liệu tích hợp sẵn > 7.500 ngày kết quả XSMB.
- Đồng bộ kết quả mới nhất từ repository GitHub công khai.
- Tài liệu hướng dẫn chi tiết nguyên lý từng thuật toán ngay trong app.

---

## Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| Ngôn ngữ | **Kotlin** |
| Giao diện | **Jetpack Compose** + Material Design 3 |
| Kiến trúc | **MVVM** + StateFlow + Coroutines |
| Xử lý dữ liệu | Local JSON + đồng bộ online |
| Nền tảng | Android SDK 36, AGP 9.x, Java 21 |
| Quyền | Internet + Network State (để sync dữ liệu) |

### Cấu trúc màn hình chính

```
Thiên cơ số
├── Dự Đoán          → Bảng điểm 00-99 + Golden Picks
├── Thuật Toán       → Bật/tắt, chỉnh trọng số, Backtest
├── Xem KQXS         → Kết quả + thống kê chuyên sâu
├── Chơi Thử         → Giả lập cược
└── Cài Đặt          → Hướng dẫn + Sync dữ liệu
```

---

## Thuật toán chi tiết

### Thuật toán 01 – Điểm Xuất Hiện & Tần Suất (V13)

- Phân tích tần suất ngắn hạn (mặc định 45 ngày) và dài hạn (180 ngày).
- Thưởng chu kỳ 7 ngày / 30 ngày.
- Bonus láng giềng giải Đặc biệt.
- Phạt số xuất hiện liên tục trong Top 3 gần đây.
- Nhiều tham số có thể tinh chỉnh (short_term_days, neighbor_bonus, cycle_7_bonus…).

### Thuật toán 02 – Số Ngày Chưa Về & Mốc Thưởng

- Tính số ngày một con số chưa về (Lô gan).
- Thưởng mốc quan trọng: 3, 7, 10, 15 ngày.
- Cộng dồn tiến trình khi số ngày vắng mặt tăng cao.

### Thuật toán 03 – Phạt Vị Trí Giải Thưởng

- Dựa trên 27 vị trí giải của ngày gần nhất.
- Giải Đặc biệt bị trừ nhiều nhất, giải thấp bị trừ ít hơn.
- Mục tiêu giảm điểm các số vừa xuất hiện ở vị trí cao.

### Thuật toán 04 – Phạt/Thưởng Tần Suất 30 Ngày

- Thưởng các số **chưa xuất hiện lần nào** trong 30 ngày.
- Phạt các nhóm số xuất hiện ít (tăng dần mức phạt).

Tất cả thuật toán trả về **delta điểm** (cộng/trừ so với điểm gốc 100.0). Hệ thống kết hợp theo trọng số người dùng đã cấu hình.

---

## Dữ liệu

- File dữ liệu chính: `xsmb-2-digits.json`
- Nguồn đồng bộ mặc định:  
  `https://raw.githubusercontent.com/khiemdoan/vietnam-lottery-xsmb-analysis/main/data/xsmb-2-digits.json`
- Dữ liệu được lưu trong `assets` của app và có thể cập nhật online.

---



### Cấu trúc thư mục quan trọng

```
app/
├── src/main/
│   ├── java/com/example/lotterypredictor/
│   │   ├── algorithms/          # 4 thuật toán + PredictionEngine
│   │   ├── data/                # Model + Repository
│   │   ├── ui/
│   │   │   ├── screens/         # 5 màn hình chính
│   │   │   └── theme/
│   │   └── MainActivity.kt
│   ├── assets/
│   │   └── xsmb-2-digits.json   # Dữ liệu lịch sử
│   └── res/
└── build.gradle.kts
```

---

## Screenshot / Demo

> Thêm ảnh demo vào thư mục `demo/` hoặc `screenshots/` và cập nhật link bên dưới.

| Màn hình | Mô tả |
|----------|-------|
| Dự đoán | Bảng điểm + Top 3 Golden Picks |
| Thuật toán | Bật/tắt + chỉnh trọng số + Backtest |
| Xem KQXS | Bảng 27 giải + thống kê |
| Cài đặt | Hướng dẫn + Sync |

<img src="https://raw.githubusercontent.com/junlangzi/Thien-co-so/refs/heads/main/demo/1.jpg" alt="Mành hình chính" width="30%"> <img src="https://raw.githubusercontent.com/junlangzi/Thien-co-so/refs/heads/main/demo/2.jpg" alt="Thuật toán" width="30%"> <img src="https://raw.githubusercontent.com/junlangzi/Thien-co-so/refs/heads/main/demo/3.jpg" alt="Kết quả" width="30%"> <img src="https://raw.githubusercontent.com/junlangzi/Thien-co-so/refs/heads/main/demo/4.jpg" alt="Chơi thử" width="30%"> <img src="https://raw.githubusercontent.com/junlangzi/Thien-co-so/refs/heads/main/demo/5.jpg" alt="Cài đặt" width="30%">


---

## Roadmap / Tính năng dự kiến

- [ ] Thêm nhiều thuật toán mới (có thể load động)
- [ ] Xuất báo cáo Backtest ra file
- [ ] Dark mode hoàn chỉnh hơn
- [ ] Widget màn hình chính
- [ ] Thông báo kết quả hàng ngày

---

## Lưu ý pháp lý & trách nhiệm

- Ứng dụng **không khuyến khích** đánh bạc.
- Kết quả dự đoán chỉ mang tính chất **thống kê lịch sử**, không phải lời khuyên tài chính.
- Người dùng tự chịu trách nhiệm với quyết định của mình.
- Dữ liệu XSMB được lấy từ nguồn công khai.

---

## Tác giả & Đóng góp

Dự án được chuyển thể từ hệ thống phân tích thống kê gốc sang nền tảng Android hiện đại với Jetpack Compose.

Nếu bạn muốn đóng góp:
1. Fork repository
2. Tạo nhánh feature
3. Gửi Pull Request kèm mô tả rõ ràng

---

## Liên hệ & Phản hồi

Nếu phát hiện lỗi, có đề xuất cải thiện hoặc cần hỗ trợ, vui lòng mở **Issue** trên repository hoặc liên hệ trực tiếp:

**Email:** `Luvideez@outlook.com`

---

**Thiên Cơ Số** – Phân tích dữ liệu rõ ràng, trực quan và có trách nhiệm.

*Phiên bản Android • Kotlin • Jetpack Compose*
