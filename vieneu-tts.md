# VieNeu-TTS — On-Device Vietnamese Speech

## Tóm tắt

VieNeu-TTS là dự án TTS tiếng Việt chạy local, hỗ trợ voice cloning tức thì,
đường ONNX/CPU torch-free, GPU path, preset voices, emotion tags và streaming
cho ứng dụng realtime.

## Điểm nổi bật

- Tối ưu đường CPU/ONNX cho macOS và môi trường không có GPU.
- Có backend GPU cho batch throughput khi cần tổng hợp khối lượng lớn.
- Voice cloning từ audio reference ngắn và API Python đơn giản.
- Streaming theo frame cho ứng dụng tương tác với time-to-first-audio thấp.
- Có web UI, Python SDK, model/runtime packaging và tài liệu cài đặt đa nền
  tảng.

## Liên kết

- [GitHub repository](https://github.com/pnnbao97/VieNeu-TTS)
- [Hugging Face VieNeu-TTS-v2](https://huggingface.co/pnnbao-ump/VieNeu-TTS-v2)

## Portfolio framing

Đây là dự án công khai riêng, được đưa vào portfolio như một sản phẩm/model
engineering có thể tái sử dụng trong các pipeline video. Khi nói về các dự án
video, VieNeu-TTS được ghi nhận là lớp speech engine/integration, không gộp
nhầm với Remotion hoặc workflow production.
