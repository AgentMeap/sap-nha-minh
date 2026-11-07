# Sạp Nhà Mình Live – Hướng dẫn cài đặt

Thư mục gồm:

| File | Dùng để |
|---|---|
| `index.html` | Toàn bộ game (host + người chơi) |
| `config.js` | Nơi dán cấu hình Firebase của bạn |
| `database.rules.json` | Luật bảo mật dán vào Realtime Database |
| `HUONG-DAN.md` | File này |

Người chơi **không cần tài khoản**: quét QR hoặc nhập mã phòng là vào chơi.

---

## Bước 1. Tạo project Firebase (miễn phí)

1. Vào https://console.firebase.google.com, đăng nhập bằng tài khoản Google.
2. Bấm **Create a project** (Tạo dự án), đặt tên, ví dụ `sap-nha-minh`. Có thể tắt Google Analytics. Bấm tạo.

## Bước 2. Bật đăng nhập ẩn danh

1. Menu trái: **Build → Authentication → Get started**.
2. Tab **Sign-in method** → chọn **Anonymous** → bật **Enable** → **Save**.

## Bước 3. Tạo Realtime Database

1. Menu trái: **Build → Realtime Database → Create database**.
2. Chọn vị trí **Singapore (asia-southeast1)** cho nhanh ở Việt Nam.
3. Chọn **Start in locked mode** → **Enable**.
4. Mở tab **Rules**, xóa hết nội dung cũ, dán toàn bộ nội dung file `database.rules.json` → **Publish**.

## Bước 4. Lấy cấu hình và dán vào `config.js`

1. Bấm biểu tượng bánh răng ⚙ cạnh **Project Overview → Project settings**.
2. Kéo xuống **Your apps** → bấm biểu tượng **Web `</>`** → đặt tên app → **Register app** (không cần bật Hosting).
3. Firebase hiện đoạn `const firebaseConfig = { ... }`. Copy các giá trị `apiKey`, `authDomain`, `databaseURL`, `projectId`, `storageBucket`, `messagingSenderId`, `appId` dán vào đúng vị trí trong `config.js`.
4. Kiểm tra `databaseURL` có dạng `https://...asia-southeast1.firebasedatabase.app`. Nếu đoạn cấu hình thiếu `databaseURL`, copy địa chỉ hiện ở đầu trang Realtime Database.

> `apiKey` của Firebase web là thông tin công khai, đưa lên mạng không sao. Dữ liệu được bảo vệ bằng luật ở Bước 3.

## Bước 5. Đưa game lên mạng (chọn một cách)

**Cách A – Netlify (dễ nhất, kéo thả)**
1. Tạo tài khoản miễn phí tại https://app.netlify.com.
2. Vào **Sites → Add new site → Deploy manually**, kéo cả thư mục `sap-nha-minh` vào.
3. Netlify cho link dạng `https://ten-ngau-nhien.netlify.app`. Có thể đổi tên trong **Site configuration → Change site name**.

**Cách B – GitHub Pages**
1. Tạo repository mới (Public) trên GitHub, bấm **Add file → Upload files**, tải lên 4 file.
2. **Settings → Pages → Branch: main / (root) → Save**. Sau 1–2 phút có link `https://<tên>.github.io/<repo>/`.

> Nếu khi mở trang báo lỗi tên miền chưa được phép, vào Firebase **Authentication → Settings → Authorized domains → Add domain**, thêm tên miền Netlify/GitHub của bạn.

## Bước 6. Chạy thử trước buổi học

1. Mở link trên máy tính → bấm **Tạo phòng mới (host)**. Máy này trở thành host, màn hình hiện mã phòng 4 số và QR.
2. Dùng 2–3 điện thoại quét QR, nhập tên, chọn nhân vật.
3. Trên máy host bấm **Bắt đầu** và chơi thử hết 6 vòng.
4. Bấm **Vòng mới** để xóa trạng thái trước khi cả lớp chơi.

## Trên lớp

- Máy host nối máy chiếu. Nếu lỡ đóng trang, mở lại link → **Mở lại phòng ####** (cùng trình duyệt).
- Bấm **Bật nhạc** nếu muốn có nhạc nền (chỉ phát trên máy host).
- **Chơi thử (tab mới)** mở một tab người chơi để bạn tự chơi cùng.
- Mỗi vòng: lựa chọn tình huống 15 giây → câu hỏi lý thuyết 12 giây → câu hỏi "Chuyện thật" 12 giây (vòng 2 có thêm mini game 15 giây). Hết giờ hoặc cả lớp trả lời xong thì tự chuyển.
- Thang điểm 1.000: Hài hòa lợi ích 400 · Lý thuyết 6 câu 300 · Chuyện thật 5 câu 300. Bằng điểm xét số câu lý thuyết đúng, rồi câu số liệu, rồi tổng thời gian trả lời.
- Cuối game: bục vinh danh top 1–3 và bảng xếp hạng đầy đủ để trao thưởng.

## Giới hạn gói miễn phí (Spark)

Realtime Database miễn phí cho tối đa 100 kết nối cùng lúc, 1 GB lưu trữ, 10 GB tải/tháng: dư cho một lớp 50 người chơi nhiều lần.
