# Bí Kíp Sinh Tồn Research: Từ Thợ Xây Thành Kiến Trúc Sư

> [!IMPORTANT]
> **Quy tắc Tối thượng:** Không ai tìm ra ý tưởng A* chỉ bằng cách đọc nhiều paper. Ý tưởng xuất hiện ở sự đứt gãy giữa các assumption, và được mài giũa bằng cọ xát thực tế (toán/code).

## 1. Mindset Shift (Đổi Góc Nhìn)
*   **Đừng tìm paper để "viết theo":** Nếu có bài giống hệt để copy, direction đó đã bão hòa. Bạn đang tìm *công cụ* (ví dụ: data augmentation trick) để giải quyết *lỗ hổng* (gap), chứ không tìm bài mẫu.
*   **AI = Thợ, Advisor = La bàn, Bạn = Người mở đường:** AI chỉ nội suy (nối các điểm đã có). Advisor nhìn thấy khoảng trống vĩ mô. Bạn là người phải đi vào khoảng trống đó, chứng minh toán học và chịu đựng bug.

## 2. The Reading Filter (Cách Đọc Paper)
Ngừng đọc để "nạp kiến thức". Đọc để **BUỘC TỘI**. Trả lời 3 câu hỏi cho mọi paper:
1.  **Shared Assumption:** Họ đang ngầm coi điều gì là hoàn hảo? *(VD: Score function là chuẩn xác 100%).*
2.  **Reality Clash:** Thực tế đập vỡ giả định đó ở đâu? *(VD: Ở vùng đuôi long-tailed, data ít, score không thể chuẩn xác).*
3.  **Cross-field Fix:** Chuyên ngành khác giải quyết sự đứt gãy này bằng tool gì? *(VD: SDE, Levy process).*

## 3. Quản lý Ý tưởng (Graveyard Matrix)
Đừng để ý tưởng trôi nổi trong đầu. Kẻ 1 file Excel.
*   **Cột 1:** Tên Paper
*   **Cột 2:** Giả định cốt lõi (Cái họ cho là đúng)
*   **Cột 3:** Sự đứt gãy (Nó sai ở đâu trong thực tế?)
*   **Cột 4:** Ý tưởng của bạn (Structural Fix)
*   **Cột 5:** Thử nghiệm 1 tuần (Toy code/Math derivation)

> [!TIP]
> Nhìn dọc Cột 3 của 10 bài báo, bạn sẽ thấy Pattern. Nhìn dọc Cột 4, bạn sẽ ra được Direction của riêng mình.

## 4. Khai thác Advisor (Anh Nghĩa)
*   **Không báo cáo tiến độ suông:** Đừng nói "Tuần này em đọc 5 bài này".
*   **Mang "Cú vấp" vào phòng họp:** "Anh ơi, bài bị reject kia em thấy nó vướng ở chỗ giả định X. Nếu mình dùng hướng Y để bẻ X thì toán bị kẹt ở đạo hàm này. Anh thấy sao?"
*   **Mượn tầm nhìn:** Bạn chưa đủ trình độ để thấy structural gap. Việc của bạn là lấy direction từ Advisor, sau đó *execute* nó đến mức nó biến thành của bạn.

## 5. The Execution Loop (Vòng Lặp Chân Lý)
Trình tự duy nhất tạo ra bài A*:
1.  **Lấy Direction:** (Từ Advisor hoặc từ Cột 3 của Excel).
2.  **Viết Toán / Toy Model 1D ngay lập tức:** Đừng scale up lên CIFAR/ImageNet vội.
3.  **Tìm cái sai:** Mô hình 1D sẽ nổ. Phương trình sẽ vô nghiệm.
4.  **Giải quyết cái sai đó:** Lời giải cho cái sai ở bước 3 CHÍNH LÀ *Contribution* cốt lõi cho bài báo A* của bạn.

---
*Ghi nhớ: Arbitrage lớn nhất của bạn không nằm ở Quant Finance. Nó nằm ở việc bạn biết dùng Advisor để tìm Gap, tự mình Formulate toán học, và dùng AI để rà soát code.*