# Create Video with AI — Modular Short-Video Pipeline

## Tóm tắt

Một pipeline Remotion có thể nhận context hoặc URL bài báo công khai và đi qua
đủ các bước:

    Setup → Planner → Teller → TTS → STT → Spec → Coder → Render

Kết quả là video dọc/ngang có voiceover, subtitle theo timeline, template hoặc
scene custom và artifact đủ để render lại.

## Điểm khác biệt

- URL bài báo được phân tích để lấy text, media và source evidence trước khi
  chọn template.
- Chỉ media trích xuất được từ nguồn mới đi vào video; nếu không có media phù
  hợp, pipeline dùng fallback đã định nghĩa thay vì tự bịa nguồn.
- TTS hỗ trợ Gemini, local VieNeu-TTS và fallback theo cấu hình; STT ưu tiên
  Faster-Whisper local rồi mới xét provider dự phòng.
- Web UI cho preview/render lại project đã có và Publish Center tách khỏi thao
  tác upload nền tảng.
- Template registry bao phủ nhóm creative, news và source-led; thêm template
  bằng package sync thay vì sửa pipeline lõi.

## Vai trò của tôi

Thiết kế pipeline/state, contract cho script và media, router template, lớp
TTS/STT, source evidence, render entry, QA scripts và test contract.

## Bằng chứng kỹ thuật

- npm test: 12 test file pass, tổng 40/40 test.
- Có test cho media manifest, news-short contract, TTS, slug, pipeline,
  transition/template và product-promo types.
- README và docs mô tả rõ credential boundary: .env, token và output lớn
  không commit.

## Công nghệ

TypeScript/React, Remotion, Node.js, Vitest, Playwright, FFmpeg, Gemini TTS,
VieNeu-TTS và Faster-Whisper.

## Trạng thái công khai

Case study này mô tả workflow local đã có output render. Repo portfolio không
copy .env, voice profile, API token, generated media hay các template package
riêng tư.
