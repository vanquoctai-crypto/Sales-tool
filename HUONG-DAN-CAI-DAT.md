# HƯỚNG DẪN DÙNG SALES TOOL (cho người không rành công nghệ)

Tool là 1 file duy nhất: `sale-cockpit.html`. Bấm đúp vào nó là mở bằng trình duyệt (Chrome/Edge). Dữ liệu tự lưu trong máy bạn.

---

## BƯỚC 1 — Dùng ngay (không cần cài gì)

1. Bấm đúp `sale-cockpit.html`.
2. Vào tab **Khách hàng** → **+ Thêm KH** → điền thông tin → **Lưu**.
3. Tab **Tổng quan** tự tính số liệu cho bạn.

Mẹo an toàn: thỉnh thoảng vào **Cài đặt → Export** để lưu 1 bản dự phòng. (Lỡ xóa lịch sử trình duyệt là mất dữ liệu.)

---

## BƯỚC 2 — Bật AI (miễn phí, không cần thẻ ngân hàng)

Làm 1 lần. Dùng Groq.

1. Mở trang **console.groq.com** → đăng nhập bằng Google.
2. Bấm **API Keys** → **Create API Key** → bấm copy (chuỗi bắt đầu bằng `gsk_...`).
3. Quay lại tool → tab **Cài đặt**:
   - Ô **Chế độ**: chọn **Groq / OpenAI-compatible**.
   - Ô **API key**: dán chuỗi `gsk_...` vừa copy.
   - Ô **Model**: để `llama-3.3-70b-versatile`.
4. Bấm **Lưu** → bấm **Kiểm tra kết nối**. Thấy chữ "OK" là xong.

---

## BƯỚC 3 — Nạp kiến thức cho AI (để AI tư vấn đúng)

1. Mở file **`KIEN-THUC-AI-TOM-TAT.md`** (bấm đúp, hoặc mở bằng Notepad).
2. Bôi đen toàn bộ → Copy (Ctrl+A rồi Ctrl+C).
3. Trong tool → **Cài đặt** → ô **Kiến thức cho AI** → dán vào (Ctrl+V) → bấm **Lưu cài đặt**.

> Đây là bản tóm tắt gọn nên AI đọc không bị quá tải. **Đừng** dán nguyên cả 6 file dài vào — sẽ báo lỗi "quá token".

Cẩm nang xử lý từ chối: vào tab **Thư viện từ chối** → mục **Nạp cẩm nang xử lý từ chối** → chọn file cẩm nang → bấm **Phân tích & lưu key**. AI sẽ tóm tắt và lưu lại.

Hồ sơ cá nhân: **Cài đặt → Hồ sơ cá nhân hóa** → dán hồ sơ sale của bạn vào → **Lưu**. AI sẽ tư vấn theo đúng phong cách của bạn.

---

## BƯỚC 4 — Chia sẻ cho đồng nghiệp

Mục tiêu: gửi 1 đường link, ai bấm cũng mở được.

1. Mở **github.com** → đăng ký (miễn phí).
2. Bấm **New repository** → đặt tên (vd `sales-tool`) → chọn **Public** → **Create**.
3. Bấm **Add file → Upload files** → kéo thả `sale-cockpit.html` vào → bấm **Commit changes**.
4. Bấm **Settings → Pages** → mục Source chọn **main** và **/ (root)** → **Save**. Chờ 1–2 phút.
5. Trang hiện ra link dạng `https://tênbạn.github.io/sales-tool/sale-cockpit.html`. Copy gửi Zalo cho cả team.

Lưu ý:
- Mỗi người có dữ liệu khách hàng **riêng** trên máy họ. Không ai thấy KH của ai.
- Mỗi người tự làm **Bước 2** (dán Groq key của họ) là dùng được AI.
- Khi bạn sửa tool: upload lại file ở Bước 4.3, cả team tự có bản mới.

---

## TÙY CHỌN — Máy khỏe muốn AI chạy riêng tư, không giới hạn

Xem file **`OLLAMA-GEMMA-LOCAL.md`**. Dành cho ai có máy mạnh (card đồ họa ~8GB trở lên), muốn AI chạy ngay trên máy, không tốn gì.

---

## KHI GẶP LỖI

- **"Request too large / quá token"**: Kiến thức dán quá dài. Bấm **🗑 Xóa riêng Kiến thức cho AI** rồi dán lại bản `KIEN-THUC-AI-TOM-TAT.md`. Hoặc đổi Model sang `llama-3.1-8b-instant`.
- **AI không chạy**: kiểm tra lại đã dán đúng key `gsk_...` và bấm **Kiểm tra kết nối** chưa.
- **Mất dữ liệu khi đổi máy/trình duyệt**: dữ liệu nằm theo từng trình duyệt. Chuyển máy thì dùng **Export** (máy cũ) rồi **Import** (máy mới).
- **Video nền không hiện**: cần có mạng internet. Không có mạng vẫn dùng tool bình thường, chỉ là nền tối.
- **Phân tích ghi âm**: chỉ chạy khi dùng Gemini (Groq không nghe được audio).
