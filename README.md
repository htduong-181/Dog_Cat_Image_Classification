Dog and Cat Image Classification

1. Giới thiệu

Dự án xây dựng mô hình Convolutional Neural Network (CNN) để phân loại hình ảnh thành hai lớp:

Cat – Mèo

Dog – Chó

Dự án được thực hiện bằng Python và PyTorch, bao gồm các bước: kiểm tra dữ liệu, tiền xử lý ảnh, chia tập Train/Validation, xây dựng CNN, huấn luyện và đánh giá mô hình.

2. Công nghệ sử dụng

Python

PyTorch

NumPy

Pandas

PIL / Pillow

Scikit-learn

Matplotlib

Jupyter Notebook

3. Dataset

Dataset được tổ chức thành hai thư mục:

PetImages/
├── Cat/
└── Dog/

Trong notebook hiện tại:

Tổng số ảnh: 200

Ảnh mèo: 100

Ảnh chó: 100

File ảnh không đọc được bị bỏ qua: 0

Dữ liệu được chia theo tỷ lệ:

80% Train

20% Validation

Việc chia dữ liệu sử dụng stratify để duy trì tỷ lệ giữa hai lớp.

4. Tiền xử lý dữ liệu

Ảnh được xử lý bằng PIL và NumPy:

Chuyển ảnh sang định dạng RGB.

Resize về kích thước 150 × 150.

Chuyển ảnh sang NumPy array.

Chuẩn hóa giá trị pixel từ [0, 255] về [0, 1].

Normalize về khoảng [-1, 1].

Chuyển thứ tự chiều ảnh từ HWC sang CHW để phù hợp với PyTorch.

Batch size được thiết lập là 32.

Project cũng kiểm tra file ảnh trước khi đưa vào dataset và loại bỏ các file ảnh bị lỗi hoặc không đọc được.

5. Kiến trúc mô hình CNN

Mô hình gồm 3 khối Convolutional:

Input (3 × 150 × 150)
        ↓
Conv2D: 3 → 32, kernel 3×3
ReLU
MaxPool 2×2
Dropout 0.2
        ↓
Conv2D: 32 → 64, kernel 3×3
ReLU
MaxPool 2×2
Dropout 0.2
        ↓
Conv2D: 64 → 128, kernel 3×3
ReLU
MaxPool 2×2
Dropout 0.2
        ↓
Flatten
        ↓
Linear: 41472 → 128
ReLU
        ↓
Linear: 128 → 2
        ↓
Cat / Dog

Dropout

Mỗi khối Convolutional sử dụng Dropout(0.2) nhằm giảm nguy cơ overfitting trong quá trình huấn luyện.

6. Huấn luyện mô hình

Các thiết lập chính:

Loss function: CrossEntropyLoss

Optimizer: Adam

Learning rate: 0.001

Epochs: 15

Batch size: 32

Device: CPU/GPU tùy theo thiết bị khả dụng

Mô hình được đánh giá trên cả tập Train và Validation sau mỗi epoch.

7. Kết quả

Kết quả cuối cùng của lần huấn luyện trong notebook:

Chỉ số

Kết quả

Train Accuracy

75.62%

Validation Accuracy

50.00%

Kết quả cho thấy mô hình đạt 75.62% accuracy trên tập Train, trong khi Validation Accuracy đạt 50.00% ở epoch cuối.

Notebook có trực quan hóa:

Training Loss và Validation Loss

Training Accuracy và Validation Accuracy

Một số dự đoán đúng

Một số dự đoán sai

Các hình ảnh kết quả được lưu dưới dạng:

cnn_training_curves.png
cnn_correct_predictions.png
cnn_wrong_prediction.png

8. Cấu trúc project

Dog_Cat_Image_Classification/
│
├── Dog_Cat_Classification.ipynb
│
├── PetImages/
│   ├── Cat/
│   └── Dog/
│
├── cnn_training_curves.png
├── cnn_correct_predictions.png
└── cnn_wrong_prediction.png

9. Cách chạy project

Clone repository

git clone https://github.com/htduong-181/Dog_Cat_Image_Classification.git

Mở notebook

Mở file:

Dog_Cat_Classification.ipynb

bằng Jupyter Notebook hoặc Visual Studio Code.

Chạy project

Chạy lần lượt các cell trong notebook để thực hiện:

Đọc và kiểm tra dữ liệu.

Tiền xử lý ảnh.

Chia Train/Validation.

Xây dựng mô hình CNN.

Huấn luyện mô hình.

Đánh giá kết quả.

Trực quan hóa dự đoán.

10. Tác giả

Hoàng Thùy Dương

GitHub: https://github.com/htduong-181