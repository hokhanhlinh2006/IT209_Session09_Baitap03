# Bài 3: Viết Dockerfile 3 dòng đóng gói trang Web HTML tĩnh

- **Môn học:** IT209 - Session 09
- **Học viên:** Hồ Khánh Linh

---

## 1. Mục tiêu
Tự viết Dockerfile ngắn gọn để đóng gói trang web HTML tĩnh cá nhân vào Docker Image sử dụng web server Nginx (phiên bản `nginx:alpine`).

---

## 2. Cấu trúc thư mục
```text
homework/session_09/ex3/
├── Dockerfile
├── index.html
└── README.md
```

---

## 3. Nội dung các tệp tin

### `index.html`
```html
<h1>Hello Docker Session 09!</h1>
```

### `Dockerfile`
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

---

## 4. Hướng dẫn Build và Khởi chạy Container

### Bước 1: Build Docker Image
Chạy lệnh build Docker image với tên `my-html-app:v1`:
```bash
docker build -t my-html-app:v1 .
```

### Bước 2: Khởi chạy Container
Khởi chạy container ở chế độ detached (`-d`), ánh xạ cổng host `8081` tới cổng `80` của Nginx container, đặt tên là `html-app`:
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```

### Bước 3: Kiểm tra hoạt động
Kiểm tra phản hồi HTTP từ web server qua `curl`:
```bash
curl http://localhost:8081
```

**Kết quả trả về:**
```html
<h1>Hello Docker Session 09!</h1>
```

---

## 5. Kết luận
- Trang web tĩnh đã được đóng gói thành công vào Docker image `my-html-app:v1`.
- Container khởi chạy và phục vụ nội dung HTML qua cổng `8081` chính xác theo yêu cầu.
