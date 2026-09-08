# Thiên Mộ Kể Chuyện — Video Workflow OS + InkOS Bridge

## Tóm tắt

Một production operating system cho video kể chuyện dài: nội dung được khóa,
voice trở thành clock của timeline, asset có manifest/hash, render có review và
master riêng, còn YouTube release là gate độc lập.

## Workflow

    intent
      → script_locked
      → voice_locked
      → continuity_locked
      → visual_plan_locked
      → assets_approved
      → timeline_locked
      → review_rendered
      → master_rendered
      → released

## Tôi đã giải quyết

- Tách source script và spoken script; giữ hash, editorial summary và điều
  kiện fail-closed khi file đổi sau lock.
- Giữ voice/timeline/SRT/shot list/render đồng bộ; không dùng chia đều thời
  lượng làm master clock.
- Tách generated khỏi approved; chỉ asset approved mới được render.
- Xây contract InkOS cho script_locked → voice_locked → assets_approved →
  review_rendered → master_rendered, có history để audit và resume.
- Tách orchestration khỏi render worker: InkOS điều phối contract, worker
  FFmpeg/Remotion xử lý codec và output.
- Bắt buộc technical QA và human playback/listening review trước khi gọi
  master/release là hoàn tất.

## Giá trị kỹ thuật

Đây là ví dụ về việc biến quy trình sáng tạo nhiều bước thành hệ thống có
state, evidence, versioning, approval gates và recovery — phù hợp với workflow
AI nhưng vẫn giữ quyền quyết định của người biên tập.

## Công nghệ

TypeScript/Node.js, InkOS, Remotion, FFmpeg/ffprobe, JSON manifests, SHA-256,
local workers và YouTube Studio release checklist.

## Attribution và trạng thái công khai

Portfolio chỉ mô tả lớp workflow/integration trong workspace riêng. InkOS base
được ghi nhận theo repo/upstream và license của nó; source story, media, secrets,
approval record và output sản xuất không được copy vào repo công khai.
