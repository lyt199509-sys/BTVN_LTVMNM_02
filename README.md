# BTVN_LTVMNM_02
# Sinh viên: Nguyễn Khánh Duy - K225480106008
# BTVN 02
# Bài làm
## Vẽ tay DB

<img width="974" height="557" alt="image" src="https://github.com/user-attachments/assets/7c042532-287e-44e0-a4b5-7c4342fcc7c0" />

## 1. TẠO THƯ MỤC VÀ DOCKER
SSH sang vs code edit cho dễ

<img width="376" height="28" alt="image" src="https://github.com/user-attachments/assets/d8433319-0d0a-411e-94fb-582f35fc1332" />

a) Tạo file requirements.txt:

<img width="300" height="103" alt="image" src="https://github.com/user-attachments/assets/b2f3a06c-d6fe-43ef-b89a-d1fa58772111" />

b) Tạo Dockerfile: 

<img width="894" height="384" alt="image" src="https://github.com/user-attachments/assets/64cc976a-f9c9-4d5e-9964-9f4760aee577" />

c) Tạo docker-compose.yml

<img width="705" height="913" alt="image" src="https://github.com/user-attachments/assets/db21346c-6e7a-4890-9c34-9696f58e3940" />

Chạy lệnh: docker compose up -d --build

## 2. CẤU HÌNH DJANGO FRAMEWORK

1. Tạo project config và application pawn_app:

<img width="741" height="76" alt="image" src="https://github.com/user-attachments/assets/770ab6cf-8df8-4ffc-a8d7-141478e3d6b7" />

<img width="326" height="213" alt="image" src="https://github.com/user-attachments/assets/6ab1b9d6-c1e9-4a2b-ad6c-693605bf0984" />

2. Chỉnh sửa nano config/settings.py để kết nối với MariaDB:
ALLOWED_HOSTS = ['*']

INSTALLED_APPS = ['pawn_app']

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'pawnshop_db',
        'USER': 'pawnadmin',
        'PASSWORD': 'pawnpassword',
        'HOST': 'db',
        'PORT': '3306',
    }
}

## 3. THIẾT KẾ CSDL (MODELS) VÀ ĐỒNG BỘ

1. Code FILE MODELS (pawn_app/models.py)

<img width="796" height="711" alt="image" src="https://github.com/user-attachments/assets/9e1edc39-e1de-48de-afd7-abaae603ada8" />

2. Code FILE ADMIN (pawn_app/admin.py)

<img width="923" height="327" alt="image" src="https://github.com/user-attachments/assets/39ef6d47-3f6b-4fa9-9545-b0f8eaa2981b" />

3. LỆNH ĐỒNG BỘ CSDL (Terminal)

docker compose exec web python manage.py makemigrations pawn_app

docker compose exec web python manage.py migrate

docker compose exec web python manage.py createsuperuser

Tài khoản: duy, pw: khanhduy2004

Đăng nhập local để kiểm tra: 
<img width="1919" height="604" alt="image" src="https://github.com/user-attachments/assets/45020410-ef5d-4218-ae81-4f7b967a59e8" />

## 4. Tích hợp giao diện và URL
1. Code FILE VIEWS (pawn_app/views.py)

<img width="999" height="576" alt="image" src="https://github.com/user-attachments/assets/a42c2b74-1713-411a-a54f-4bd7ef9a9a43" />

2. Code FILE URLS (config/urls.py)

<img width="661" height="264" alt="image" src="https://github.com/user-attachments/assets/cf7ef72a-3ebc-4569-8e40-871cf965d5d2" />

3. Tạo FILE GIAO DIỆN (pawn_app/templates/home.html)

Thêm code html cho file home.html

<img width="365" height="190" alt="image" src="https://github.com/user-attachments/assets/c12eadab-5d3d-495c-b8f3-2591019189a7" />

Khởi động lại hệ thống: docker compose restart web

## 5. Test bằng local

Truy cập bằng Ip_máy_server với các port sau:

8002(Kiểm tra template):

<img width="1919" height="417" alt="image" src="https://github.com/user-attachments/assets/10e234a7-ec3e-48a3-add8-1356aee35a6c" />

8002/admin(Kiểm tra Django): 

<img width="1919" height="646" alt="image" src="https://github.com/user-attachments/assets/e0787425-3591-4202-896a-38307c5da98a" />

8082(kiểm tra phpadmin): 

<img width="1918" height="861" alt="image" src="https://github.com/user-attachments/assets/7cfdaba5-7561-4b2d-a0f3-8f288c61b67a" />

## 6. Triển khai trên Internet

1. Cấu hình lại docker-compose.yml, thêm như sau:

<img width="917" height="363" alt="image" src="https://github.com/user-attachments/assets/a752bc52-e1f2-4de0-a5d9-8ab76796c40d" />

2. Docker-compose up -d, Thêm dữ liệu và truy cập: https://camdo.nguyenkhanhduy04.id.vn/ để kiểm tra:

<img width="1912" height="623" alt="image" src="https://github.com/user-attachments/assets/b9a6fe0f-bdf4-40f7-8c7e-a1a83e987232" />



