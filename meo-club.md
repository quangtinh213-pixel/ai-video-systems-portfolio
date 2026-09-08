# MEO CLUB — Interactive TikTok LIVE Control Room

## Tóm tắt

Một hệ thống local nối TikTok LIVE với OBS: gift thật được chuẩn hóa, cộng
điểm cho 5 mèo AI, kích hoạt video interaction/solo/group dance và cập nhật
leaderboard realtime.

## Kiến trúc

    TikTok LIVE
          ↓
    Node.js gateway
      ↙     ↓       ↘
    gift  WebSocket  state
    tier    hub      recovery
      ↓      ↙  ↘
    OBS player   leaderboard
          ↑
        Admin UI

## Tôi đã giải quyết

- Map gift theo gift ID, tên hoặc chuỗi tên; ưu tiên effect và fallback về tier
  mặc định.
- Giữ UI ổn định khi gift đến thành burst bằng coalescing và chính sách
  backpressure.
- Chặn slow client: bỏ message ưu tiên thấp, giữ event critical và terminate
  client bị nghẽn không phục hồi.
- Khôi phục điểm sau crash/tắt nhầm bằng state normalization và atomic JSON
  write.
- Bảo vệ local control surface bằng Origin check, asset validation và backup
  cấu hình trước lần lưu đầu tiên.
- Cung cấp admin UI, simulator, load smoke và asset checker để vận hành mà
  không cần Electron hay OBS WebSocket.

## Bằng chứng kỹ thuật

- npm test: 9/9 test pass.
- npm run check: syntax/ID/config/assets pass; 15 video được cấu hình đủ.
- Test bao phủ burst coalescing, slow-client policy, critical event, Origin,
  state normalization, goal progression và atomic write.

## Công nghệ

Node.js 20+, tiktok-live-connector, ws, HTML/CSS/JavaScript, OBS Browser
Source.

## Trạng thái công khai

Đây là case study từ workspace local. Media livestream và cấu hình kênh không
được đưa vào portfolio repo; source đầy đủ có thể tách thành một repo riêng sau
khi sanitize config và kiểm tra quyền sử dụng asset.
