Setup firewall Linux
    Check file /etc/default/ufw đảm bảo IPv6 được bật
    

    Setup default policy rule
        sudo ufw default deny incoming
        sudo ufw default allow outgoing  
    (Các lệnh này đặt các giá trị mặc định để từ chối kết nối đến và cho phép các kết nối gửi đi.) 
    (Chỉ riêng các mặc định tường lửa này đã có thể đủ cho một máy tính cá nhân, nhưng các máy chủ thường cần phản hồi các yêu cầu đến từ người dùng bên ngoài)


    Cho phép kết nối SSH
        sudo ufw app list
    Kích hoạt cấu hình ứng dụng OpenSSH
        sudo ufw allow OpenSSH  
    Cho phép SSH theo tên dịch vụ
        sudo ufw allow ssh
    Cho phép SSH theo số cổng
        sudo ufw allow 22


    Bật UFW
        sudo ufw show added
        sudo ufw enable


    Cho phép các kết nối khác
    HTTP trên cổng 80, là cổng mà máy chủ web không được mã hóa sử dụng 
        sudo ufw allow http hoặc sudo ufw allow 80
    HTTPS trên cổng 443, là cổng mà máy chủ web được mã hóa sử dụng
        sudo ufw allow https hoặc sudo ufw allow 443
    Apache với cả HTTP và HTTPS
        sudo ufw allow ‘Apache Full’
    Nginx với cả HTTP và HTTPS
        sudo ufw allow ‘Nginx Full’    
    Kiểm tra các cấu hình ứng dụng có sẵn 
        sudo ufw app list


    Set cho dãy port
        sudo ufw allow 6000:6007/tcp
        sudo ufw allow 6000:6007/udp
    

    Đối với địa chỉ IP cụ thể
        sudo ufw allow from 203.0.113.4
        sudo ufw allow from 203.0.113.4 to any port 22


    Đối với subnet
        sudo ufw allow from 203.0.113.0/24
        sudo ufw allow from 203.0.113.0/24 to any port 22


    Đối với cổng mạng 
        sudo ufw allow in on eth0 to any port 80
        sudo ufw allow in on eth1 to any port 3306


    Xóa rule theo số 
    Xác định số thứ tự của rule    
        sudo ufw status numbered
        sudo ufw delete 2

    Xóa rule theo tên
        sudo ufw delete allow "Apache Full"
        sudo ufw delete allow http
        sudo ufw delete allow 80


    Kiểm tra trạng thái và rule UFW 
        sudo ufw status verbose
    inactive ( bị tắt theo mặc định)
    nếu ufw đang active sẽ liệt kê các quy tắc được thiết lập


    Tắt hoặc đặt lại UFW
        sudo ufw disable
        sudo ufw reset    