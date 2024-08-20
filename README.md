<p align="center">
<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&center=true&vCenter=true&random=false&width=450&lines=Pencil+Sketch+Project" alt="Typing SVG" /></a>
</p>
<div align="center">
<img alt="GitHub code size in bytes" src="https://img.shields.io/github/languages/code-size/CptDat9/pencil_sketch?labelColor=7AA2E3&color=97E7E1">
</div>


Project này là một công cụ xử lý ảnh bằng Python, cho phép chuyển đổi bất kỳ ảnh nào thành tranh vẽ chì. Sử dụng thư viện OpenCV, chương trình sẽ nhận vào một ảnh và biến nó thành một hình ảnh thang độ xám, mô phỏng lại vẻ ngoài của một bản vẽ chì.

## Cách Hoạt Động

1. **Đọc Ảnh**:
    - Chương trình bắt đầu bằng cách đọc ảnh đầu vào sử dụng `cv2.imread(image_path)`, với `image_path` là đường dẫn đến tệp ảnh bạn muốn chuyển đổi.

2. **Chuyển Đổi Thành Thang Độ Xám**:
    - Ảnh sau đó được chuyển đổi thành ảnh thang độ xám bằng `cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)`, giúp đơn giản hóa ảnh bằng cách loại bỏ thông tin màu, chỉ giữ lại độ sáng.

3. **Đảo Ngược Ảnh Thang Độ Xám**:
    - Ảnh thang độ xám được đảo ngược sử dụng `cv2.bitwise_not(gray_image)`. Kỹ thuật đảo ngược này là cách phổ biến để tăng cường hiệu ứng tranh vẽ chì, vì nó làm nổi bật sự tương phản trong ảnh.

4. **Làm Mờ Ảnh**:
    - Ảnh thang độ xám đảo ngược được làm mờ bằng `cv2.GaussianBlur(inverted_gray_image, (21,21), 0)`. Làm mờ Gaussian giúp làm mịn ảnh, tạo ra hiệu ứng nét vẽ tự nhiên hơn trong sản phẩm cuối cùng.

5. **Đảo Ngược Ảnh Đã Làm Mờ**:
    - Ảnh đã làm mờ sau đó được đảo ngược một lần nữa sử dụng `cv2.bitwise_not(blurred_image)`.

6. **Tạo Tranh Vẽ Chì**:
    - Cuối cùng, chương trình kết hợp ảnh thang độ xám và ảnh đã đảo ngược hai lần bằng `cv2.divide(gray_image, inverted_blurred_image, scale=256.0)`. Bước chia này tạo cho ảnh cuối cùng vẻ ngoài giống như tranh vẽ chì.

7. **Lưu Và Hiển Thị Ảnh**:
    - Tranh vẽ chì được lưu vào đường dẫn đầu ra đã chỉ định sử dụng `cv2.imwrite(output_path, pencil_sketch_image)`, và tranh vẽ chì này được hiển thị trong một cửa sổ sử dụng `cv2.imshow('Pencil Sketch', pencil_sketch_image)`.

## Cách Chạy

Để chạy chương trình, thực hiện theo các bước sau:

1. **Đảm bảo bạn đã cài đặt Python và OpenCV**:
    - Bạn có thể cài đặt OpenCV bằng pip nếu chưa cài đặt:
    ```bash
    pip install opencv-python
    ```

2. **Đặt ảnh vào cùng thư mục với script**:
    - Đảm bảo ảnh bạn muốn chuyển đổi nằm trong cùng thư mục với script Python và được đặt tên tương ứng trong script.
    P/s: Trong mã nguồn tôi đã dùng luôn địa chỉ của ảnh cho tiện :D

3. **Chạy script**:
    - Thực hiện script Python sử dụng lệnh:
    ```bash
    python pencil_sketch.py
    ```
    - Ảnh đầu ra sẽ được lưu trong cùng thư mục với tên `_sketch` được thêm vào sau tên gốc.

## Ví Dụ

**Ảnh Gốc:**

![garnacho1 jpg](https://github.com/user-attachments/assets/831ce619-afa4-40f5-b006-c657276e4dc3)


**Tranh Vẽ Chì:**

![garnacho1](https://github.com/user-attachments/assets/f6064486-3ebb-4051-ab96-270dcf0bec24)

## Yêu Cầu

- **Python 3.x**: Đảm bảo Python đã được cài đặt trên hệ thống của bạn.
- **Thư viện OpenCV (`cv2`)**: Cần thiết để thực hiện các tác vụ xử lý ảnh.
