# Dự án: PHÂN LOẠI ÂM THANH MÔI TRƯỜNG
## Nhóm dự án
* Le Huu Son - B22DCVT439 - 05
* Nguyen Tien Sang - B23DCVT369 - 05
* Vu Trong Kien - B23DCDT152 -05
---

## Giới thiệu

Dự án này tập trung vào việc xây dựng một hệ thống tự động phân loại các loại âm thanh môi trường (Environmental Sound Classification - ESC) sử dụng sự kết hợp giữa kỹ thuật Xử lý Tín hiệu số (Digital Signal Processing - DSP) và Học sâu (Deep Learning). Mục tiêu là chuyển đổi tín hiệu âm thanh thô thành các đặc trưng có ý nghĩa và sử dụng Mạng nơ-ron tích chập (Convolutional Neural Network - CNN) để nhận diện chính xác các sự kiện âm thanh khác nhau.

## Mục tiêu Dự án

*   **Trích xuất Đặc trưng:** Áp dụng các kỹ thuật DSP (đặc biệt là Mel-spectrogram) để chuyển đổi dữ liệu âm thanh dạng sóng thành các biểu diễn tần số-thời gian phù hợp cho các mô hình học sâu.
*   **Xây dựng Mô hình AI:** Thiết kế, huấn luyện và đánh giá một mô hình CNN bằng PyTorch để phân loại các đặc trưng âm thanh.
*   **Đánh giá Hiệu suất:** Đánh giá khả năng phân loại của mô hình trên tập dữ liệu chưa từng thấy bằng các chỉ số như độ chính xác, báo cáo phân loại và ma trận nhầm lẫn.
*   **Triển khai:** Thực hiện toàn bộ dự án trên nền tảng điện toán đám mây Google Colab.

## Cấu trúc Thư mục Dự án
environmental_sound_classification/

├── data/

│ ├── raw/ # Chứa dữ liệu âm thanh gốc (ESC-50-master.zip và thư mục giải nén)

│ └── features/ # Chứa các đặc trưng đã trích xuất (Mel-spectrograms dưới dạng .npy files và processed_metadata.csv)

│ └── esc50_mel_specs/

├── models/ # Chứa các mô hình đã huấn luyện (.pth files)

├── README.md # File hướng dẫn này

├── ESC_Project_Notebook.ipynb # File Google Colab Notebook chính (là toàn bộ mã nguồn)

└── (Các file báo cáo hoặc tài liệu khác nếu có)


## Cách Chạy Dự án

Dự án này được thiết kế để chạy trên **Google Colab** để tận dụng tài nguyên GPU miễn phí và môi trường đã cấu hình sẵn.

**Bước 1: Chuẩn bị Môi trường Colab**

1.  Mở trình duyệt web của bạn và truy cập [https://colab.research.google.com/](https://colab.research.google.com/).
2.  Đăng nhập bằng tài khoản Google của bạn.
3.  Tạo một Notebook mới (File -> New Notebook) hoặc tải lên file `ESC_Project_Notebook.ipynb` của bạn.
4.  **Quan trọng:** Thay đổi Runtime thành GPU. Đi tới `Runtime` -> `Change runtime type`, chọn `GPU` dưới mục `Hardware accelerator`, và nhấn `Save`.
5.  Trong Notebook, chạy ô code đầu tiên (**Bước 1: Thiết lập môi trường Google Colab**) để kiểm tra GPU, cài đặt thư viện và gắn kết Google Drive. Bạn sẽ cần xác thực Google Drive khi được yêu cầu.

**Bước 2: Tải và Chuẩn bị Dữ liệu (ESC-50)**

1.  **Tải file ESC-50-master.zip về máy tính cá nhân của bạn:**
    *   Truy cập [https://github.com/karolpiczak/ESC-50](https://github.com/karolpiczak/ESC-50).
    *   Nhấp vào nút "Code" (màu xanh lá cây) và chọn "Download ZIP".
2.  **Upload file `ESC-50-master.zip` lên Google Drive:**
    *   Truy cập Google Drive của bạn (qua trình duyệt).
    *   Điều hướng đến thư mục dự án bạn đã tạo: `MyDrive/ESC_Project/data/raw`.
    *   Tải file `ESC-50-master.zip` vào thư mục này.
3.  **Chạy ô code "Bước 2: Thu thập và Chuẩn bị Dữ liệu (ESC-50)"** trong Notebook. Code này sẽ giải nén file ZIP từ Drive vào môi trường Colab.

**Bước 3: Trích xuất Đặc trưng (DSP - Mel-spectrograms)**

1.  Chạy ô code **"Bước 3: Trích xuất Đặc trưng (DSP - Mel-spectrograms)"** trong Notebook.
2.  Bước này sẽ đọc các file âm thanh, tính toán Mel-spectrograms, chuẩn hóa chúng và lưu các đặc trưng dưới dạng file `.npy` vào thư mục `data/features/esc50_mel_specs/` trên Google Drive. Nó cũng sẽ tạo một file `esc50_processed_metadata.csv`.
3.  Quá trình này có thể mất một thời gian tùy thuộc vào kích thước tập dữ liệu và tài nguyên GPU.

**Bước 4: Định nghĩa và Huấn luyện Mô hình AI (CNN)**

1.  Chạy ô code **"Bước 4: Định nghĩa và Huấn luyện Mô hình AI (CNN)"** trong Notebook.
2.  Bước này sẽ định nghĩa kiến trúc CNN (AudioCNN) bằng PyTorch, chuẩn bị dữ liệu cho huấn luyện (chia tập train/val/test), và bắt đầu quá trình huấn luyện mô hình.
3.  Mô hình đã huấn luyện sẽ được lưu vào thư mục `models/` trên Google Drive dưới dạng file `.pth`.

**Bước 5: Đánh giá Mô hình**

1.  Chạy ô code **"Bước 5: Đánh giá Mô hình"** trong Notebook.
2.  Bước này sẽ tải mô hình đã huấn luyện và đánh giá hiệu suất của nó trên tập kiểm thử. Các chỉ số như độ chính xác tổng thể, báo cáo phân loại (precision, recall, F1-score) và ma trận nhầm lẫn sẽ được hiển thị.

**Bước 6: Dự đoán trên File Âm thanh Mới (Inference)**

1.  Chạy ô code **"Bước 6: Dự đoán trên File Âm thanh Mới (Inference)"** trong Notebook.
2.  Bạn có thể thay đổi biến `NEW_AUDIO_PATH` trong ô code này để chỉ định file âm thanh bạn muốn dự đoán.
3.  Bước này sẽ tiền xử lý file âm thanh mới và sử dụng mô hình đã huấn luyện để dự đoán lớp của nó.

## Kết quả Chính (Dự kiến)

*   **Độ chính xác trên tập kiểm thử:** [Ví dụ: ~75-80% cho ESC-50].
*   **Biểu đồ Loss & Accuracy:** Sẽ hiển thị quá trình hội tụ của mô hình.
*   **Báo cáo phân loại và Ma trận nhầm lẫn:** Cung cấp thông tin chi tiết về hiệu suất cho từng lớp và các trường hợp nhầm lẫn của mô hình.

## Yêu cầu Hệ thống

*   **Google Colab:** Môi trường được khuyến nghị.
*   **GPU:** Bắt buộc để huấn luyện mô hình học sâu một cách hiệu quả. (Được cung cấp miễn phí bởi Google Colab).
*   **Google Drive:** Cần không gian trống (khoảng 1 GB) để lưu trữ dữ liệu và mô hình.

## Thư viện Python

Dự án này sử dụng các thư viện Python chính sau:

*   `torch`: PyTorch Deep Learning Framework
*   `librosa`: Xử lý và phân tích âm thanh
*   `numpy`: Tính toán khoa học
*   `pandas`: Phân tích và thao tác dữ liệu
*   `scikit-learn`: Tiền xử lý dữ liệu và đánh giá mô hình
*   `matplotlib`, `seaborn`: Trực quan hóa dữ liệu
*   `tqdm`: Hiển thị thanh tiến độ

Tất cả các thư viện này sẽ được cài đặt tự động (hoặc đã có sẵn) khi bạn chạy ô code thiết lập môi trường trong Notebook.

