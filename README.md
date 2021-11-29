# Mô tả đồ án
## Cài đặt. ## 
Trong ~environment nhập lệnh:
```
cd rosbot_description
rosdep install --from-paths src --ignore-src -r -y
```
Sau khi lệnh chạy ta tiếp tục gõ:
```
colcon build
colcon bundle
```
Sau khi build và bundle hoàn thành ta sẽ đưa bundle lên S3 và dùng S3 để khởi tạo simulation.

## Sử dụng Teleop trong simulation. ##
Teleop là một thư viện trong ROS được sử dụng để điều khiển Robo thông qua terminal.
Khi đã có được một simulation job, ta mở terminal của simulation và gõ các lệnh sau:
```
sudo apt-get install ros-noetic-teleop-twist-keyboard
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
Ta được bảng điều khiển như hình bên dưới để Robo di chuyển
![image](https://user-images.githubusercontent.com/72614237/143812864-f30b9062-9cd6-400c-83cd-bba822ee4866.png)
