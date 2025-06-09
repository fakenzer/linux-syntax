# Hướng dẫn các lệnh Linux

## Mục lục
1. [Lệnh cơ bản](#lệnh-cơ-bản)
2. [Quản lý file và thư mục](#quản-lý-file-và-thư-mục)
3. [Xem và chỉnh sửa file](#xem-và-chỉnh-sửa-file)
4. [Tìm kiếm](#tìm-kiếm)
5. [Quyền và sở hữu](#quyền-và-sở-hữu)
6. [Quản lý process](#quản-lý-process)
7. [Mạng](#mạng)
8. [Nén và giải nén](#nén-và-giải-nén)
9. [Hệ thống](#hệ-thống)
10. [Lệnh nâng cao](#lệnh-nâng-cao)

---

## Lệnh cơ bản

### pwd - Hiển thị thư mục hiện tại
```bash
pwd
# Hiển thị đường dẫn đầy đủ của thư mục hiện tại
```

### ls - Liệt kê file và thư mục
```bash
ls                  # Liệt kê file và thư mục
ls -l              # Hiển thị chi tiết (long format)
ls -la             # Hiển thị tất cả file (bao gồm ẩn)
ls -lh             # Hiển thị kích thước dễ đọc
ls -lt             # Sắp xếp theo thời gian
ls -lS             # Sắp xếp theo kích thước
ls *.txt           # Liệt kê file có đuôi .txt
```

### cd - Chuyển thư mục
```bash
cd /path/to/dir    # Chuyển đến thư mục cụ thể
cd ~               # Chuyển về home directory
cd ..              # Chuyển lên thư mục cha
cd -               # Chuyển về thư mục trước đó
cd                 # Chuyển về home directory
```

---

## Quản lý file và thư mục

### mkdir - Tạo thư mục
```bash
mkdir dirname           # Tạo thư mục
mkdir -p path/to/dir   # Tạo thư mục và các thư mục cha
mkdir dir1 dir2 dir3   # Tạo nhiều thư mục cùng lúc
```

### rmdir - Xóa thư mục rỗng
```bash
rmdir dirname          # Xóa thư mục rỗng
rmdir -p path/to/dir  # Xóa thư mục và các thư mục cha rỗng
```

### rm - Xóa file và thư mục
```bash
rm filename            # Xóa file
rm -i filename        # Xóa với xác nhận
rm -f filename        # Xóa bắt buộc (không hỏi)
rm -r dirname         # Xóa thư mục và nội dung
rm -rf dirname        # Xóa thư mục bắt buộc
rm *.txt              # Xóa tất cả file .txt
```

### cp - Sao chép file và thư mục
```bash
cp source dest         # Sao chép file
cp -r source dest     # Sao chép thư mục
cp -i source dest     # Sao chép với xác nhận ghi đè
cp -u source dest     # Chỉ sao chép nếu source mới hơn
cp file1 file2 dir/   # Sao chép nhiều file vào thư mục
```

### mv - Di chuyển/đổi tên
```bash
mv oldname newname    # Đổi tên file/thư mục
mv file dir/          # Di chuyển file vào thư mục
mv -i source dest     # Di chuyển với xác nhận ghi đè
```

### touch - Tạo file rỗng hoặc cập nhật timestamp
```bash
touch filename        # Tạo file rỗng hoặc cập nhật timestamp
touch file1 file2     # Tạo nhiều file
```

---

## Xem và chỉnh sửa file

### cat - Hiển thị nội dung file
```bash
cat filename          # Hiển thị toàn bộ nội dung
cat file1 file2       # Hiển thị nhiều file liên tiếp
cat -n filename       # Hiển thị với số dòng
```

### less/more - Xem file theo trang
```bash
less filename         # Xem file (có thể cuộn lên xuống)
more filename         # Xem file theo trang
```

### head - Xem đầu file
```bash
head filename         # Hiển thị 10 dòng đầu
head -n 20 filename   # Hiển thị 20 dòng đầu
head -c 100 filename  # Hiển thị 100 ký tự đầu
```

### tail - Xem cuối file
```bash
tail filename         # Hiển thị 10 dòng cuối
tail -n 20 filename   # Hiển thị 20 dòng cuối
tail -f filename      # Theo dõi file real-time
```

### nano/vim - Chỉnh sửa file
```bash
nano filename         # Mở file với nano editor
vim filename          # Mở file với vim editor
```

---

## Tìm kiếm

### find - Tìm file và thư mục
```bash
find /path -name "filename"       # Tìm theo tên
find /path -type f -name "*.txt"  # Tìm file .txt
find /path -type d -name "dirname" # Tìm thư mục
find /path -size +100M            # Tìm file > 100MB
find /path -mtime -7              # Tìm file sửa đổi trong 7 ngày
find /path -user username         # Tìm file của user
```

### grep - Tìm kiếm trong nội dung file
```bash
grep "pattern" filename           # Tìm pattern trong file
grep -r "pattern" directory/      # Tìm recursive trong thư mục
grep -i "pattern" filename        # Tìm không phân biệt hoa thường
grep -n "pattern" filename        # Hiển thị số dòng
grep -v "pattern" filename        # Hiển thị dòng không chứa pattern
grep -c "pattern" filename        # Đếm số dòng chứa pattern
```

### which/whereis - Tìm vị trí lệnh
```bash
which command         # Tìm đường dẫn của lệnh
whereis command       # Tìm binary, source, manual
```

---

## Quyền và sở hữu

### chmod - Thay đổi quyền file
```bash
chmod 755 filename    # Thiết lập quyền rwxr-xr-x
chmod +x filename     # Thêm quyền execute
chmod -w filename     # Bỏ quyền write
chmod u+x filename    # Thêm execute cho owner
chmod g-w filename    # Bỏ write cho group
chmod o=r filename    # Thiết lập read-only cho others
```

### chown - Thay đổi chủ sở hữu
```bash
chown user filename           # Đổi owner
chown user:group filename     # Đổi owner và group
chown -R user:group dir/      # Đổi recursive cho thư mục
```

### chgrp - Thay đổi group
```bash
chgrp group filename          # Đổi group
chgrp -R group dir/           # Đổi recursive cho thư mục
```

---

## Quản lý process

### ps - Hiển thị process
```bash
ps                    # Hiển thị process của user hiện tại
ps aux                # Hiển thị tất cả process chi tiết
ps -ef                # Hiển thị tất cả process với PPID
ps -u username        # Hiển thị process của user cụ thể
```

### top/htop - Monitor process real-time
```bash
top                   # Monitor system và process
htop                  # Phiên bản cải tiến của top
```

### kill - Kết thúc process
```bash
kill PID              # Kết thúc process với PID
kill -9 PID           # Force kill process
killall process_name  # Kill tất cả process có tên
pkill pattern         # Kill process theo pattern
```

### jobs - Quản lý background jobs
```bash
jobs                  # Hiển thị background jobs
bg                    # Đưa job vào background
fg                    # Đưa job vào foreground
nohup command &       # Chạy lệnh không bị kill khi logout
```

---

## Mạng

### ping - Test kết nối
```bash
ping hostname         # Test ping đến host
ping -c 4 hostname    # Ping 4 lần rồi dừng
```

### wget/curl - Download file
```bash
wget URL              # Download file từ URL
wget -O filename URL  # Download và đặt tên file
curl URL              # Hiển thị nội dung từ URL
curl -O URL           # Download file giữ nguyên tên
```

### ssh - Kết nối remote
```bash
ssh user@hostname     # SSH đến host
ssh -p port user@host # SSH với port cụ thể
scp file user@host:path # Copy file qua SSH
```

### netstat - Hiển thị kết nối mạng
```bash
netstat -an           # Hiển thị tất cả kết nối
netstat -tulpn        # Hiển thị port đang listen
```

---

## Nén và giải nén

### tar - Archiving
```bash
tar -cvf archive.tar files/       # Tạo tar archive
tar -xvf archive.tar              # Giải nén tar
tar -czvf archive.tar.gz files/   # Tạo tar.gz
tar -xzvf archive.tar.gz          # Giải nén tar.gz
tar -tf archive.tar               # Liệt kê nội dung archive
```

### zip/unzip
```bash
zip archive.zip files             # Tạo zip file
zip -r archive.zip directory/     # Zip thư mục recursive
unzip archive.zip                 # Giải nén zip
unzip -l archive.zip              # Liệt kê nội dung zip
```

---

## Hệ thống

### df - Disk usage
```bash
df -h                 # Hiển thị disk usage dễ đọc
df -i                 # Hiển thị inode usage
```

### du - Directory usage
```bash
du -h directory/      # Kích thước thư mục
du -sh directory/     # Tổng kích thước thư mục
du -ah directory/     # Kích thước tất cả file và thư mục
```

### free - Memory usage
```bash
free -h               # Hiển thị RAM usage dễ đọc
free -m               # Hiển thị RAM trong MB
```

### uptime - System uptime
```bash
uptime                # Hiển thị thời gian chạy hệ thống
```

### whoami/who - User info
```bash
whoami                # Hiển thị username hiện tại
who                   # Hiển thị user đang login
w                     # Hiển thị chi tiết user và hoạt động
```

### history - Lịch sử lệnh
```bash
history               # Hiển thị lịch sử lệnh
history | grep command # Tìm lệnh trong lịch sử
!!                    # Chạy lại lệnh cuối
!n                    # Chạy lại lệnh thứ n
```

---

## Lệnh nâng cao

### awk - Text processing
```bash
awk '{print $1}' file             # In cột đầu tiên
awk -F: '{print $1}' /etc/passwd  # Sử dụng : làm delimiter
awk '/pattern/ {print}' file      # In dòng chứa pattern
```

### sed - Stream editor
```bash
sed 's/old/new/g' file            # Thay thế old bằng new
sed '1d' file                     # Xóa dòng đầu tiên
sed -n '1,5p' file               # In dòng 1-5
```

### sort - Sắp xếp
```bash
sort file             # Sắp xếp nội dung file
sort -n file          # Sắp xếp số
sort -r file          # Sắp xếp ngược
sort -u file          # Sắp xếp và loại bỏ trùng lặp
```

### uniq - Loại bỏ dòng trùng lặp
```bash
uniq file             # Loại bỏ dòng trùng lặp liền kề
sort file | uniq      # Loại bỏ tất cả dòng trùng lặp
uniq -c file          # Đếm số lần xuất hiện
```

### wc - Word count
```bash
wc file               # Đếm dòng, từ, ký tự
wc -l file            # Chỉ đếm dòng
wc -w file            # Chỉ đếm từ
wc -c file            # Chỉ đếm ký tự
```

### xargs - Build command từ input
```bash
find . -name "*.txt" | xargs rm   # Xóa tất cả file .txt
echo "file1 file2" | xargs touch # Tạo file1 và file2
```

### pipe (|) - Kết hợp lệnh
```bash
ls -l | grep "txt"                # Lọc file .txt từ ls
cat file | sort | uniq            # Sắp xếp và loại bỏ trùng lặp
ps aux | grep process_name        # Tìm process cụ thể
```

---

## Shortcuts hữu ích

- `Ctrl + C`: Dừng lệnh đang chạy
- `Ctrl + Z`: Tạm dừng lệnh (có thể dùng `fg` để tiếp tục)
- `Ctrl + D`: Thoát terminal hoặc EOF
- `Ctrl + L`: Xóa màn hình (tương đương `clear`)
- `Tab`: Auto-complete tên file/lệnh
- `↑/↓`: Duyệt lịch sử lệnh
- `Ctrl + R`: Tìm kiếm trong lịch sử lệnh

---

## Wildcards

- `*`: Khớp với bất kỳ ký tự nào
- `?`: Khớp với một ký tự duy nhất  
- `[]`: Khớp với một trong các ký tự trong ngoặc
- `{}`: Mở rộng brace expansion

```bash
ls *.txt              # Tất cả file .txt
ls file?.txt          # file1.txt, file2.txt, etc.
ls file[1-3].txt      # file1.txt, file2.txt, file3.txt
cp file.{txt,bak}     # Tương đương cp file.txt file.bak
```

---

## Tips quan trọng

1. **Luôn cẩn thận với lệnh `rm -rf`** - có thể xóa toàn bộ hệ thống
2. **Sử dụng `man command`** để xem manual của lệnh
3. **Sử dụng `command --help`** để xem trợ giúp nhanh
4. **Backup quan trọng trước khi thực hiện thay đổi lớn**
5. **Sử dụng Tab completion** để tránh lỗi đánh máy
6. **Kiểm tra quyền trước khi thực hiện các thao tác quan trọng**
