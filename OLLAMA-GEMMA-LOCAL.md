# Chạy AI miễn phí trên máy mình bằng Ollama + Gemma 3

Dành cho ai có **máy đủ khỏe** và muốn AI chạy hoàn toàn trên máy: miễn phí tuyệt đối, không quota, không cần thẻ, dữ liệu khách hàng **không ra khỏi máy**. Đổi lại chỉ chạy được trên chính máy đang bật Ollama (không chia sẻ cho người khác qua link được — muốn chia sẻ thì dùng Groq).

## Máy cần khỏe cỡ nào

Chọn model theo cấu hình (mức nén Q4 mặc định của Ollama):

| Model Ollama | VRAM/RAM cần | Phù hợp |
|---|---|---|
| `gemma3:4b`  | ~3 GB  | Máy yếu, không GPU rời — vẫn chạy nhưng chất lượng vừa |
| `gemma3:12b` | ~7 GB  | GPU 8–12GB (RTX 3060/4060...) — **khuyên dùng**, cân bằng tốt |
| `gemma3:27b` | ~15 GB | GPU 16GB+ — chất lượng cao nhất |

Không có GPU rời vẫn chạy được bằng RAM + CPU, nhưng chậm hơn nhiều. Máy yếu thì dùng `gemma3:4b` hoặc quay lại Groq.

## Cài đặt (3 bước)

1. Tải Ollama: https://ollama.com/download (Windows/Mac/Linux), cài như app thường.
2. Mở Terminal / Command Prompt, tải model:
   ```
   ollama pull gemma3:12b
   ```
   (đổi `12b` thành `4b` hoặc `27b` tùy máy)
3. Chạy thử cho chắc:
   ```
   ollama run gemma3:12b
   ```
   Gõ vài câu thấy trả lời là được. Gõ `/bye` để thoát. Ollama vẫn chạy nền ở cổng `11434`.

## Cho phép tool gọi vào Ollama (bắt buộc 1 lần)

Trình duyệt chặn gọi vào Ollama vì khác nguồn (CORS). Cần bật `OLLAMA_ORIGINS`:

- **Windows:** mở Command Prompt:
  ```
  setx OLLAMA_ORIGINS "*"
  ```
  Rồi thoát Ollama ở khay hệ thống và mở lại.
- **Mac/Linux:** chạy `launchctl setenv OLLAMA_ORIGINS "*"` (Mac) hoặc thêm `OLLAMA_ORIGINS=*` vào biến môi trường rồi khởi động lại Ollama.

## Trỏ tool vào Ollama

Trong `sale-cockpit.html` → tab **Cài đặt → Kết nối AI**:

- Chế độ: **Groq / OpenAI-compatible**
- Base URL: `http://localhost:11434/v1`
- API key: **để trống**
- Model: `gemma3:12b` (đúng tên model đã pull)

Bấm **Lưu → Kiểm tra kết nối**.

> Quan trọng: khi dùng Ollama, hãy **mở tool bằng file trên máy** (mở trực tiếp `sale-cockpit.html`), đừng mở qua link `https://...github.io`. Trang `https` không gọi được `http://localhost` (trình duyệt chặn mixed-content).

## Khi nào dùng cái nào

- **Ollama + Gemma 3:** riêng bạn, máy khỏe, cần riêng tư, không quota. Phần text rất tốt.
- **Groq:** chia sẻ cả team qua link, không cần thẻ, không cần máy khỏe.
- **Gemini:** khi cần phân tích **ghi âm/audio** (Ollama và Groq trong bản này chỉ xử lý text).
