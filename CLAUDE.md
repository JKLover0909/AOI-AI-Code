# CLAUDE.md

## Tổng quan
AOI-AI-Code là thử nghiệm AOI (Automated Optical Inspection) phát hiện lỗi bằng YOLO11 (Ultralytics) trên ảnh bo mạch/linh kiện, dữ liệu gán nhãn lấy từ Roboflow (project `aoi-2023`, version 2, định dạng `yolov11`).

## Cấu trúc
- `Code.ipynb` — notebook chính (kernel `yolov11`): tải dataset từ Roboflow, huấn luyện/suy luận YOLO11 bằng `ultralytics` + `torch`, xử lý ảnh bằng `cv2`/`PIL`.
- `Dataafter/` — ~800 ảnh `.bmp` đã xử lý/cắt (≈25MB), dùng làm dữ liệu mẫu.
- `Test1.bmp`, `Test2.bmp`, `Test3.bmp`, `Test1_resized.bmp`, `Test3_resized.bmp`, `Oridata.jpg` — ảnh kiểm thử/ảnh gốc.
- `yolo11n.pt` — trọng số YOLO11n pretrained của Ultralytics (tải lại tự động được; giấy phép AGPL-3.0 của Ultralytics).

## Môi trường
Python + `ultralytics roboflow torch opencv-python pillow numpy`, Jupyter.

## Biến môi trường
- `ROBOFLOW_API_KEY` — API key Roboflow. **Không hard-code** vào notebook (từng bị lộ trong lịch sử git, phải xoay key).

## Quy tắc khi làm việc
- Không commit API key/token; đọc từ biến môi trường.
- Notebook còn đường dẫn tuyệt đối của máy tác giả (`D:\SonCode\AOI-2023-Yolov11\...`) — đổi sang đường dẫn tương đối khi được yêu cầu.
- Thư mục dataset Roboflow tải về (`AOI-2023-*`) và `runs/` đã nằm trong `.gitignore`, không commit.
- Dữ liệu ảnh/trọng số là tài sản của dự án: không xóa hay đổi tên hàng loạt khi chưa được phép.
