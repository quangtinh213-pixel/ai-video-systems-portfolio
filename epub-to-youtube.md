# EPUB → YouTube Story Video

## Tóm tắt

Pipeline Python biến một file EPUB thành video kể chuyện có thể chạy lại từ
điểm dừng:

    EPUB → chapter/paragraph extraction → scene split → Edge TTS
        → word timestamps → AI/local image → ASS subtitles
        → FFmpeg Ken Burns → thumbnail/metadata → optional YouTube upload

## Tôi đã xây dựng

- EPUB reader có đường dự phòng đọc trực tiếp từ ZIP khi parser chính không
  đáp ứng.
- Scene splitter giữ chapter context và giới hạn độ dài để cân bằng nhịp đọc,
  số ảnh và chi phí render.
- TTS tạo audio cùng word timestamps để subtitle bám theo lời đọc.
- Image gateway có retry/payload fallback và gradient fallback để pipeline
  không chết khi image service local chưa sẵn sàng.
- FFmpeg compose tạo clip từng cảnh, concat, zoom Ken Burns, burn subtitle,
  thumbnail và metadata.
- Cache audio/ảnh/clip cho phép chạy tiếp sau gián đoạn hoặc chỉ render lại
  phần cần đổi.
- YouTube upload dùng OAuth riêng và mặc định không public tự động.

## Bằng chứng kỹ thuật

Workspace có video mẫu đã render tại output/Đao_Khách_Băng_Hà/, cùng các module
riêng cho extraction, scenes, TTS, image generation, subtitles, compose và
upload.

## Công nghệ

Python, edge-tts, BeautifulSoup/EPUB parsing, JSON word timing, ASS subtitle,
FFmpeg/ffprobe và YouTube Data API v3.

## Trạng thái công khai

Case study only. EPUB, nội dung truyện, credential OAuth, audio và ảnh generated
không được publish tự động; chỉ source đã được kiểm tra quyền sử dụng mới phù
hợp để mở repo.
