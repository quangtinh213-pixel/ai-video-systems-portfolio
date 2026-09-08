# AI Video & Creative Systems Portfolio

Production-oriented systems for Vietnamese storytelling, short-form video
automation, on-device speech, and interactive livestreams.

Tôi xây dựng các hệ thống đi từ nội dung thô đến sản phẩm có thể kiểm tra:
tiếp nhận nguồn, biên tập, giọng đọc, hình ảnh, timeline, render, QA và phát
hành. Portfolio này tập trung vào cách giải bài toán và bằng chứng kỹ thuật,
không phải một bản sao của các workspace sản xuất có dữ liệu riêng tư.

## Các dự án tiêu biểu

| Dự án | Tôi đã xây dựng | Bằng chứng chính |
|---|---|---|
| [MEO CLUB](projects/meo-club.md) | Điều phối TikTok LIVE → OBS cho 5 mèo AI, quà tặng kích hoạt media, bảng điểm realtime và trang quản trị local | Node.js, WebSocket, state recovery, backpressure, atomic write; 9/9 test pass và kiểm tra tích hợp local pass |
| [Create Video with AI](projects/create-video-with-ai.md) | Pipeline 8 bước từ context/bài báo đến video Remotion có voiceover và phụ đề theo timeline | Remotion, TTS/STT, source evidence, template router; 12 test file, 40/40 test pass |
| [EPUB → YouTube Story Video](projects/epub-to-youtube.md) | Chuyển EPUB thành video kể chuyện: tách cảnh, TTS, ảnh, phụ đề ASS, Ken Burns, thumbnail và metadata | Python, Edge TTS, FFmpeg/ffprobe, cache có thể chạy tiếp; đã có video mẫu render |
| [Thiên Mộ Kể Chuyện / Video Workflow OS](projects/thien-mo-video-os.md) | Hệ thống sản xuất truyện dài có stage gate, voice làm clock, manifest/hash, review/master và YouTube release prep | InkOS bridge, Remotion, FFmpeg, QA fail-closed, human review gates |
| [VieNeu-TTS](projects/vieneu-tts.md) | Sản phẩm TTS tiếng Việt chạy local với voice cloning, ONNX/CPU, GPU path và streaming | Repo công khai: [pnnbao97/VieNeu-TTS](https://github.com/pnnbao97/VieNeu-TTS) |
| [YouTube View Ngoại](projects/youtube-view-ngoai.md) | Biến workflow kể chuyện thành pipeline international-English với inheritance, target-language adaptation và release gates | Python scripts, cấu hình kế thừa, voice/timeline/asset/master gates |

## Năng lực nổi bật

- Thiết kế pipeline có trạng thái, checkpoint, artifact và điều kiện chuyển
  stage rõ ràng.
- Xây backend realtime chịu được burst event: coalescing, backpressure,
  giới hạn client, lọc Origin và lưu state an toàn.
- Kết hợp TTS/STT local với provider fallback mà không để credential lọt vào
  mã nguồn.
- Dựng video bằng Remotion/FFmpeg, giữ voice làm nguồn thời gian duy nhất và
  kiểm tra output bằng report/hash/ffprobe.
- Đưa các quyết định biên tập và chất lượng vào workflow thay vì chỉ tạo ra
  một file MP4 cuối cùng.

## Cách tôi đo chất lượng

1. Kiểm tra source, schema, quyền sử dụng và phạm vi.
2. Khóa script/voice/timeline trước các bước phụ thuộc.
3. Chỉ render asset đã qua kiểm tra; giữ version cũ và artifact có hash.
4. Chạy test, lint/typecheck hoặc script QA phù hợp với từng dự án.
5. Tách technical pass khỏi human review: nghe voice, xem video và duyệt phát
   hành vẫn là các cổng riêng.

## Phạm vi công khai

Repo này là lớp portfolio/case study. Các source workspace chứa secret local,
audio mẫu, output lớn, tài liệu sản xuất, nội dung truyện và media có quyền
hạn chế sẽ không được copy tự động vào repo công khai. Với dự án dựa trên
upstream, portfolio ghi rõ vai trò tích hợp hoặc mở rộng thay vì nhận toàn bộ
codebase là sản phẩm gốc.

Xem thêm: [quy tắc đóng gói và attribution](projects/publishing-scope.md).
