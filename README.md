# install-docker
```
ติดตั้ง Docker
อัปเดต package index:

bash
Copy code
sudo apt update
ติดตั้ง dependencies ที่จำเป็น:

bash
Copy code
sudo apt install apt-transport-https ca-certificates curl software-properties-common
เพิ่ม GPG key ของ Docker:

bash
Copy code
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
เพิ่ม Docker repository:

bash
Copy code
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
อัปเดต package index อีกครั้ง:

bash
Copy code
sudo apt update
ติดตั้ง Docker:

bash
Copy code
sudo apt install docker-ce
ตรวจสอบการติดตั้ง Docker:

bash
Copy code
sudo docker --version
2. ติดตั้ง Docker Compose
ดาวน์โหลด Docker Compose เวอร์ชันล่าสุด: สำหรับเวอร์ชันล่าสุด สามารถดูได้จากที่นี่: https://github.com/docker/compose/releases/latest สมมติว่าเวอร์ชันล่าสุดคือ v2.18.0

bash
Copy code
sudo curl -L "https://github.com/docker/compose/releases/download/v2.18.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
ให้สิทธิ์การใช้งานไฟล์ docker-compose:

bash
Copy code
sudo chmod +x /usr/local/bin/docker-compose
ตรวจสอบการติดตั้ง Docker Compose:

bash
Copy code
docker-compose --version
3. สั่งให้ Docker ทำงานอัตโนมัติเมื่อเครื่องบูต
bash
Copy code
sudo systemctl enable docker

1. เพิ่มผู้ใช้ของคุณเข้าในกลุ่ม docker
bash
Copy code
sudo usermod -aG docker $USER
คำสั่งนี้จะเพิ่มผู้ใช้ที่คุณกำลังใช้อยู่ ($USER คือตัวแปรที่อ้างถึงชื่อผู้ใช้ในปัจจุบัน) เข้าไปในกลุ่ม docker

2. ออกจากระบบและเข้าสู่ระบบใหม่ (หรือทำการรีสตาร์ทเครื่อง)
เพื่อให้การเปลี่ยนแปลงกลุ่มมีผล (หรือใช้คำสั่ง newgrp docker ในการเปลี่ยนกลุ่มโดยไม่ต้องออกจากระบบ)

3. ทดสอบการทำงานของคำสั่ง docker ps อีกครั้ง
หลังจากที่คุณเข้าสู่ระบบใหม่หรือเปลี่ยนกลุ่มแล้ว ลองรันคำสั่ง docker ps อีกครั้ง:

bash
Copy code
docker ps
```
