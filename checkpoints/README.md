🇬🇧 🇫🇷 English-to-French Neural Machine Translation
Dự án này xây dựng mô hình Dịch máy (Machine Translation) từ tiếng Anh sang tiếng Pháp sử dụng kỹ thuật Deep Learning với thư viện PyTorch.

Dự án bao gồm việc triển khai và so sánh hiệu năng giữa hai kiến trúc mô hình:

Baseline Model: Seq2Seq với LSTM (Encoder-Decoder truyền thống).

Attention Model: Seq2Seq với GRU kết hợp cơ chế Bahdanau Attention (Additive Attention).

📂 Cấu trúc Dự án
Để dự án chạy mượt mà trên cả Google Colab và máy Local, vui lòng tuân thủ cấu trúc thư mục sau:

Plaintext

NLP_Project/
├── checkpoints/              # Nơi lưu model (.pth) và logs training (.csv)
│   ├── model_baseline_best.pth
│   ├── model_attention_best.pth
│   └── ...
├── data/                     # Thư mục chứa dữ liệu
│   ├── raw/                  # CHỨA DỮ LIỆU GỐC (.gz) - Copy file vào đây
│   │   ├── train.en.gz
│   │   ├── train.fr.gz
│   │   └── ... (các file val, test)
│   └── processed/            # Chứa file cache sau khi xử lý (.pth)
│       └── processed_data.pth
├── notebooks/                # Mã nguồn chính
│   └── NLPProject.ipynb      # File Notebook chạy dự án
├── src/                      # (Tùy chọn) Mã nguồn phụ trợ
└── requirements.txt          # Danh sách thư viện cần thiết
🚀 Hướng dẫn Cài đặt & Chạy
Cách 1: Chạy trên Google Colab (Khuyên dùng)
Đây là cách nhanh nhất để tận dụng GPU miễn phí.

Upload Dữ liệu:

Tạo thư mục trên Google Drive: My Drive/NLPProject/.

Tạo thư mục con data/raw và upload toàn bộ các file .gz (train, val, test) vào đó.

Chạy Notebook:

Upload file NLPProject.ipynb lên Google Colab.

Chạy Cell 1 và Cell 2 đầu tiên.

Hệ thống sẽ yêu cầu cấp quyền truy cập Google Drive. Sau khi cấp quyền, code sẽ tự động nhận diện và load dữ liệu từ folder bạn đã tạo.

Cách 2: Chạy trên máy Local (Windows/Mac/Linux)
Yêu cầu: Python 3.8+, PyTorch (khuyến khích có GPU NVIDIA).

Clone/Download dự án: Tải source code về máy và giải nén.

Cài đặt thư viện: Mở terminal tại thư mục gốc dự án và chạy:

Bash

pip install -r requirements.txt
Nếu chưa có file requirements.txt, xem phần phụ lục bên dưới.

Tải Model ngôn ngữ cho Spacy: Cần tải 2 gói ngôn ngữ Anh và Pháp để tokenization:

Bash

python -m spacy download en_core_web_sm
python -m spacy download fr_core_news_sm
Chuẩn bị Dữ liệu:

Đảm bảo bạn đã tạo thư mục data/raw/.

Copy các file .gz (train.en.gz, train.fr.gz,...) vào trong data/raw/.

Chạy Notebook: Mở Jupyter Notebook hoặc VS Code:

Bash

jupyter notebook notebooks/NLPProject.ipynb
Chạy lần lượt các cell từ trên xuống dưới.

📊 Quy trình Huấn luyện & Đánh giá
Notebook được thiết kế theo các bước sau:

Setup & Preprocessing: Tải dữ liệu, xây dựng từ điển (Vocabulary), và tạo DataLoaders.

Train Baseline: Huấn luyện model Seq2Seq LSTM cơ bản.

Train Attention: Huấn luyện model Seq2Seq GRU có Attention.

Lưu ý: Quá trình train có thể mất từ 30-60 phút tùy vào GPU (mặc định 20 epochs).

Model tốt nhất (_best.pth) sẽ tự động được lưu vào thư mục checkpoints/.

Inference (Dịch thử): Dịch một câu tiếng Anh bất kỳ sang tiếng Pháp.

Evaluation: Tính điểm BLEU Score trên các tập Test (2016, 2017, 2018).

Visualization: Vẽ biểu đồ so sánh Loss giữa 2 model.

📈 Kết quả Kỳ vọng
Baseline Model: Thường gặp khó khăn với các câu dài, điểm BLEU thấp hơn.

Attention Model: Có khả năng "chú ý" vào các phần quan trọng của câu nguồn, cho câu dịch mượt mà hơn và điểm BLEU cao hơn đáng kể.

🛠 Phụ lục: requirements.txt
Nếu bạn chưa có file requirements.txt, hãy tạo một file với nội dung sau:

Plaintext

torch
torchtext
torchvision
torchaudio
spacy
numpy
pandas
matplotlib
jupyter
portalocker>=2.0.0
Tác giả: [La Hoành Nghiệp] Liên hệ: [https://www.facebook.com/lahoanhnghiep]