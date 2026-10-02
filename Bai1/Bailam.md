Câu 1: Trình bày sự khác nhau giữa Value Types (Kiểu giá trị) và Reference Types
(Kiểu tham chiếu) trong C# về cơ chế lưu trữ vùng nhớ (Stack vs Heap).
Câu 2: Tính năng Init-only Properties (init) trong C# 9/10 khác gì so với thuộc tính
có set thông thường? Nêu trường hợp sử dụng thực tế.
Câu 3: Phân biệt sự khác nhau giữa phương thức virtual ở lớp cha và phương
thức override ở lớp con khi triển khai tính Đa hình (Polymorphism).
Câu 4: Tại sao một thành phần được khai báo là static trong Lớp (Class) lại không thể
truy xuất thông qua một thể hiện (Object Instance) được tạo bằng toán tử new?
Câu 1:
Value Types (Kiểu giá trị - như int, float, bool, struct):
	-Cơ chế lưu trữ: Lưu trữ trực tiếp giá trị thực tế của biến. Nếu biến được khai báo cục bộ trong phương thức, nó được lưu hoàn toàn trên vùng nhớ Stack (Ngăn xếp).
	-Đặc điểm: Kích thước nhỏ, tốc độ truy xuất rất nhanh, tự động giải phóng khi ra khỏi phạm vi hàm (scope). Khi gán cho biến khác, dữ liệu được sao chép thành một bản sao hoàn toàn độc lập.
Reference Types (Kiểu tham chiếu - như class, string, array, object):
	-Cơ chế lưu trữ: Vùng nhớ Stack chỉ chứa địa chỉ tham chiếu (con trỏ) dẫn đến vùng nhớ thực tế, còn dữ liệu thật sự của đối tượng nằm trên vùng nhớ Heap (Vùng nhớ động).
	-Đặc điểm: Kích thước lớn hơn, quản lý bởi bộ thu gom rác (Garbage Collector - GC). Khi gán cho biến khác, chỉ có địa chỉ tham chiếu được sao chép; cả hai biến cùng trỏ đến một vùng dữ liệu trên Heap.
Câu 2:
Khác biệt:
	-Thuộc tính có set thông thường cho phép thay đổi giá trị của thuộc tính bất cứ lúc nào sau khi đối tượng đã được khởi tạo.
	-Thuộc tính dùng init (C# 9/10) chỉ cho phép gán giá trị trong quá trình khởi tạo đối tượng (ví dụ qua object initializer hoặc constructor). Sau khi khởi tạo xong, thuộc tính trở thành read-only (không thể thay đổi giá trị nữa), giúp đảm bảo tính bất biến (immutability).
Trường hợp sử dụng thực tế:
	-Dùng cho các đối tượng DTO (Data Transfer Object), các cấu hình (Config) ứng dụng, hoặc các kiểu dữ liệu record / class cần giữ trạng thái bất biến sau khi tạo ra để tránh việc dữ liệu bị thay đổi ngoài ý muốn trong quá trình chạy chương trình (Thread-safe hơn và an toàn hơn).
Câu 3:
Phương thức virtual ở lớp cha:
	-Được khai báo tại lớp cơ sở (base class) để cho phép các lớp con có quyền ghi đè (override) phương thức này.
	-Bản thân virtual vẫn có một thân hàm (implementation) mặc định để lớp con có thể dùng lại nếu không muốn viết lại.
Phương thức override ở lớp con:
  -Được khai báo tại lớp dẫn xuất (derived class) nhằm thay thế hoặc mở rộng lại nội dung của phương thức virtual (hoặc abstract) đã có ở lớp cha.
  -Giúp thực thi tính đa hình (Polymorphism): Khi gọi phương thức qua tham chiếu của lớp cha nhưng trỏ tới thể hiện của lớp con, phiên bản hàm ở lớp override của lớp con sẽ được thực thi lúc chạy (runtime).
Câu 4:
Thành phần static (biến hoặc hàm tĩnh) thuộc về chính lớp (Class) đó chứ không thuộc về bất kỳ đối tượng cụ thể nào được sinh ra.
Nó được cấp phát bộ nhớ ngay khi chương trình nạp lớp lên (tại vùng nhớ Static Area/High-Frequency Heap), tồn tại xuyên suốt vòng đời ứng dụng và được dùng chung cho tất cả các thể hiện.
Trong khi đó, toán tử new tạo ra một thể hiện riêng biệt (Object Instance) nằm trên Heap. Vì thành phần static không gắn liền với cá thể riêng lẻ nào, trình biên dịch C# không cho phép gọi instance.StaticMember để tránh nhầm lẫn về mặt ngữ nghĩa và kiến trúc bộ nhớ. Bạn bắt buộc phải gọi trực tiếp thông qua tên lớp: ClassName.StaticMember.
