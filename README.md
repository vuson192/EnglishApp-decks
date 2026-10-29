# Thư viện bộ từ online (`library-decks/`)

Thư mục này giữ nội dung của thư viện online mà app tải về qua mạng (tab Thư viện), và nguồn của bộ 3000 từ có sẵn. Không file nào ở đây được đóng gói vào app.

## Bố cục

| Đường dẫn | Nội dung | Đẩy lên repo `vuson192/EnglishApp-decks` |
|---|---|---|
| `manifest.json` | Danh sách các bộ (`schemaVersion: 2`): `family-home`, `food-cooking`, `travel`, `health` | Có, ở gốc repo |
| `decks/<id>.json` | 4 bộ chủ đề, mỗi bộ 70–90 từ, mỗi từ một dòng | Có, ở `decks/` |
| `repo-README.md` | README của repo thư viện (các bộ, giấy phép) | Có, đổi tên thành `README.md` ở gốc repo |
| `README.md` | File này: bố cục, cách đẩy, nguồn bộ 3000 từ | Không |
| `source/` | Nguồn và công cụ dựng bộ 3000 từ | Không |

Test `__tests__/libraryDecks.test.ts` kiểm toàn bộ nội dung: manifest và từng file bộ hợp lệ, manifest khớp file, 70–90 từ mỗi bộ, file ≤ 200 KB, không trùng từ (trong bộ, giữa các bộ, và với bộ 3000 từ kể cả dạng biến đổi), `id` hợp lệ, IPA giữa hai dấu `/`, câu ví dụ có từ, giải thích tiếng Anh không dùng chính từ đó (từ nhiều chữ hoặc có gạch nối thì cũng không dùng phần nào của nó, trừ in, of, the, and, law), `description` ghi giấy phép.

## Giấy phép

Nội dung thư viện (`manifest.json`, `decks/`) do AI soạn, phát hành theo giấy phép CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). `description` của mỗi bộ kết thúc bằng "Nội dung do AI soạn. Giấy phép CC BY-SA 4.0.".

## Cách đẩy lên repo thư viện

Chỉ đẩy khi `npx.cmd jest` qua. App đọc thư viện từ nhánh `main` của repo public `vuson192/EnglishApp-decks`.

1. Lần đầu: trên trình duyệt, tạo repo **public** tên `EnglishApp-decks` trong tài khoản `vuson192` (không thêm file nào).
2. Clone repo về một thư mục **ngoài** project này, ví dụ `D:\WorkSpace\Personal\EnglishApp-decks`:
   ```
   git clone https://github.com/vuson192/EnglishApp-decks.git
   ```
3. Chép vào gốc repo vừa clone:
   - `library-decks/manifest.json` thành `manifest.json`
   - cả thư mục `library-decks/decks/` thành `decks/`
   - `library-decks/repo-README.md` thành `README.md`

   Không chép `library-decks/README.md` và `library-decks/source/`.
4. Trong thư mục repo thư viện:
   ```
   git add manifest.json decks README.md
   git commit -m "feat: add library decks"
   git branch -M main
   git push -u origin main
   ```
   Khi Git hỏi đăng nhập, đăng nhập GitHub bằng trình duyệt (Git Credential Manager mở cửa sổ). Không ghi token hay mật khẩu vào file nào.
5. Mở `https://raw.githubusercontent.com/vuson192/EnglishApp-decks/main/manifest.json` trên trình duyệt: phải thấy đúng nội dung `manifest.json`. GitHub raw có thể giữ bản cũ vài phút sau khi đẩy; chờ rồi tải lại trang.

Khi sửa một bộ: sửa trong `library-decks/` của project này, tăng `version` ở cả file bộ và mục tương ứng trong `manifest.json`, cập nhật `wordCount` nếu số từ đổi, chạy `npx.cmd jest`, rồi chép lại và đẩy như bước 3–5.

## Nguồn của bộ 3000 từ (`source/`)

`source/` không được đóng gói vào app; nó giữ nguồn và công cụ dựng `assets/decks/ngsl-3000.json`:

- `source/NGSL_12_stats.csv`: danh sách NGSL 1.2 chính thức (2.809 từ, xếp theo `SFI Rank`), tải ngày 2026-10-27 từ https://www.newgeneralservicelist.com/s/NGSL_12_stats.csv, giấy phép CC BY-SA 4.0.
- `source/build-ngsl-order.js`: script Node. `node library-decks/source/build-ngsl-order.js` báo chỗ bộ 3000 từ lệch với file CSV; thêm `--write` thì dựng lại bộ: hạng 1 đến 2.809 là đúng các từ NGSL theo thứ tự CSV, hạng 2.810 đến 3.000 là các từ trong `source/extra-order.txt`.
- `source/ngsl-new-words.jsonl`: nội dung (đủ 7 trường) cho các từ NGSL chưa có trong bộ trước đây, và các dòng sửa riêng một trường của từ đã có.
- `source/extra-order.txt`: 191 từ ngoài NGSL, theo thứ tự trong bộ.
# EnglishApp-decks
