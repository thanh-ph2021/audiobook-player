# Audiobook Player

Trình phát audiobook chạy trên máy tính. Chọn một thư mục chứa file audio, app tự sắp xếp theo tên thành danh sách có ảnh bìa, rồi phát và nhớ bạn đang nghe tới đâu.

Chạy hoàn toàn offline: file audio chỉ được đọc ngay trên máy, không upload đi đâu.

## Tính năng

- Chọn thư mục, tự sắp xếp file theo tên (Chương 2 đứng trước Chương 10), hoặc theo ngày sửa.
- Danh sách có thumbnail cho từng file, lấy theo thứ tự:
  1. Ảnh trùng tên với file audio.
  2. Ảnh bìa nhúng trong file (mp3, m4a, m4b).
  3. Ảnh `cover.jpg`, `folder.jpg`... trong cùng thư mục.
  4. Ô màu kèm số thứ tự nếu không có ảnh.
- Hỗ trợ các định dạng: mp3, m4a, m4b, aac, wav, flac, ogg, opus.
- Player: phát/dừng, bài trước/sau, tua ±15 giây, tốc độ 0.75× đến 2×, âm lượng.
- Nhớ file đang nghe và vị trí (theo giây) cho từng thư mục, mở lại là nghe tiếp.
- Mục "Thư mục gần đây" để mở lại thư mục không cần chọn lại.
- Tìm kiếm theo tên (gõ không dấu cũng tìm được), đổi cỡ thumbnail.
- Giao diện sáng/tối.
- Hẹn giờ tắt (15 đến 60 phút hoặc hết file đang nghe).
- Phím tắt: `Space` phát/dừng, `←` `→` tua 15 giây.

## Chạy thử

Cần cài [Node.js](https://nodejs.org) (bản LTS).

```bash
npm install
npm start
```

Chỉ muốn dùng nhanh mà không cài gì: mở thẳng file `index.html` bằng Chrome hoặc Edge.

## Đóng gói ra file .exe

```bash
npm run dist
```

Kết quả nằm trong thư mục `dist/`:

- `Audiobook Player Setup x.y.z.exe`: bản cài đặt (mở nhanh hơn, có shortcut).
- `Audiobook Player x.y.z.exe`: bản portable, chạy thẳng không cần cài (mỗi lần mở phải giải nén nên chậm hơn).

Lưu ý khi build trên Windows:

- Nếu gặp lỗi "Cannot create symbolic link", hãy chạy terminal bằng quyền Administrator hoặc bật Developer Mode rồi build lại.
- Windows SmartScreen có thể cảnh báo "Unknown publisher" vì app chưa được ký số. Bấm **More info** rồi **Run anyway**.

## Cấu trúc dự án

```
├── index.html       Giao diện và toàn bộ logic của trình phát
├── main.js          Mở cửa sổ Electron
├── package.json     Cấu hình dự án và đóng gói
├── icon.ico         Icon của app
└── .gitignore
```

## Lưu ý

- Thư mục gần đây và vị trí đang nghe được lưu trong bộ nhớ của trình duyệt (hoặc của Electron) trên máy đang dùng, nên không đi theo file `.exe` sang máy khác.
- Với ổ cứng di động: nếu rút ổ trong lúc đang nghe, app sẽ báo không đọc được file. Cắm lại ổ và mở lại thư mục từ mục "Gần đây".
- Khi chạy trên Chrome/Edge, đừng chọn thẳng gốc ổ đĩa (ví dụ `E:\`) vì trình duyệt chặn. Hãy chọn thư mục con chứa sách.
