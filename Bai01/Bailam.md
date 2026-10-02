Câu 1: Value Types vs Reference Types (Bộ nhớ)

-Value Types (struct, int,...): Giá trị lưu trực tiếp trên Stack. Bản sao độc lập khi gán.

-Reference Types (class, string,...): Stack chỉ giữ địa chỉ (con trỏ), dữ liệu thật nằm trên Heap. Cùng trỏ vào một vùng nhớ khi gán.

Câu 2: Init-only (init) vs set thông thường

-Khác biệt: set cho sửa giá trị mọi lúc; init chỉ cho gán lúc tạo đối tượng (Object Initializer/Constructor), sau đó trở thành Read-only (Bất biến).

-Thực tế: Dùng cho các đối tượng truyền dữ liệu (DTO), cấu hình hệ thống cần đảm bảo an toàn, không bị sửa đổi lung tung.

Câu 3: virtual (Cha) vs override (Con)

-virtual: Định nghĩa ở lớp cha, chứa mã mặc định và mở cổng cho phép lớp con ghi đè.

-override: Viết lại mã ở lớp con, thay thế hàm của cha để thực thi tính đa hình khi chạy (Runtime).

Câu 4: Tại sao static không gọi qua Instance (new)?

-Vì static thuộc về Lớp, không thuộc về Đối tượng.

-Nó dùng chung cho toàn bộ chương trình và được nạp ngay khi tải lớp. Đối tượng tạo bằng new là một bản thể độc lập trên Heap, nên không thể đại diện hay truy xuất cho thành phần dùng chung của Lớp.
