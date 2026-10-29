# Thư viện bộ từ của 4English

Repo này chứa các bộ từ mà app 4English tải về qua mạng (tab Thư viện). App đọc `manifest.json` và các file trong `decks/` từ nhánh `main` qua địa chỉ `https://raw.githubusercontent.com/vuson192/EnglishApp-decks/main/`.

## Các bộ có trong thư viện

| Bộ | File | Số từ | Nội dung |
|---|---|---|---|
| Gia đình và nhà cửa | `decks/family-home.json` | 82 | Người thân, các phòng và đồ dùng trong nhà, việc nhà |
| Đồ ăn và nấu ăn | `decks/food-cooking.json` | 88 | Thực phẩm, gia vị, món ăn, dụng cụ bếp, cách nấu |
| Du lịch | `decks/travel.json` | 83 | Sân bay, khách sạn, đi lại, tham quan, dã ngoại |
| Sức khoẻ | `decks/health.json` | 86 | Triệu chứng, bệnh thường gặp, thuốc, khám chữa bệnh, cơ thể, lối sống |

Các bộ chỉ gồm từ chưa có trong bộ 3000 từ có sẵn của app. Mỗi từ có đủ: từ, từ loại, phiên âm IPA (Anh-Mỹ), nghĩa tiếng Việt, giải thích tiếng Anh, câu ví dụ và bản dịch.

## Định dạng

- `manifest.json`: `schemaVersion: 2` và danh sách `decks`, mỗi mục có `id`, `version`, `schemaVersion`, `file`, `name`, `description`, `level`, `wordCount`.
- `decks/<id>.json`: `schemaVersion: 2`, `id`, `version`, `name`, `description`, `level` và mảng `words`; mỗi từ có `word`, `explanationEn`, `meaningVi`, `ipa`, `partOfSpeech`, `example`, `exampleVi`, `rank`.

App kiểm mọi file tải về; file sai định dạng sẽ không được nhập.

## Giấy phép

Nội dung của thư viện (`manifest.json` và các file trong `decks/`) do AI soạn và được phát hành theo giấy phép **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)**: https://creativecommons.org/licenses/by-sa/4.0/

Bạn được chia sẻ và sửa nội dung, kể cả cho mục đích thương mại, miễn là ghi nguồn và phát hành bản sửa theo cùng giấy phép. Vì nội dung do AI soạn, nghĩa, phiên âm hoặc câu ví dụ có thể còn chỗ chưa chính xác.
