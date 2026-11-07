# Cẩm nang sống đáng giá — website ebook tĩnh

Site HTML thuần (không framework, không JavaScript bắt buộc) dựng từ bản dịch
tiếng Việt của HowToLiveBetter (CC BY 4.0).

## Cấu trúc

- `index.html` — bìa, giới thiệu, mục lục đầy đủ, nút tải EPUB, ghi công.
- `chuong-01.html` … `chuong-34.html` — 34 chương; mỗi chương có mục lục nhỏ
  ở đầu trang, mỗi mục có neo `#muc-<số>` và link cố định ¶, cuối trang có
  điều hướng Chương trước / Mục lục / Chương sau.
- `bai-<slug>.html` — 9 bài viết dài.
- `loi-dich-gia.html`, `boi-canh.html`, `thuat-ngu.html`, `an-ban.html` —
  các trang phần đầu sách.
- `style.css` — stylesheet dùng chung.
- `HowToLiveBetter-vi.epub`, `HowToLiveBetter.epub` — file EPUB để tải.

## Dựng lại

```
~/workspace/.venvs/ebook/bin/python ~/workspace/howtolivebetter/build_ebook_site.py
```

Script đọc nguồn Markdown tại `~/workspace/howtolivebetter/src-vi/vi/`
(book/, docs/, front/), loại bỏ dòng quay về mục lục ở đầu file và các
comment HTML metadata, chuyển link nội bộ .md thành link trang HTML tương
ứng, rồi ghi ra thư mục này.

## Deploy tĩnh

Thư mục này deploy được lên bất kỳ static host nào:

- GitHub Pages: đẩy cả thư mục lên một repo, bật Pages từ nhánh chính
  (file `.nojekyll` đã có sẵn để Pages không xử lý Jekyll).
- Vercel/Netlify/Cloudflare Pages: chọn thư mục này làm root, không cần
  build command, output directory là chính thư mục.
- Máy chủ tĩnh bất kỳ: chép toàn bộ thư mục lên và phục vụ trực tiếp.
