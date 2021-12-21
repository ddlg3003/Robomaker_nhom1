# Nhóm 24 
## Nguyễn Minh Chiến - 19110173
## Nguyễn Hữu Đăng - 19110187
## Nguyễn Văn Sơn Tùng - 19110018

# Mô tả đồ án 
## Cài đặt. ## 
### Cài đặt bằng bundle
Trong ~environment nhập lệnh:
```
cd Robomaker_nhom1
rosdep install --from-paths src --ignore-src -r -y
```
Sau khi lệnh chạy ta tiếp tục gõ:
```
colcon build
colcon bundle
```
Đưa file output.tar lên S3:
```
aws s3 cp bundle/output.tar s3://<tên-S3-đã-tạo>
```
Sau khi build và bundle hoàn thành ta sẽ đưa bundle lên S3 và dùng S3 để khởi tạo simulation.
### Cài đặt bằng terminal và máy ảo trong cloud9
Install:
```
sudo apt update
cd Robomaker_nhom1
rosdep install --from-paths src --ignore-src -r -y
colcon build
```
Lấy thế giới đã tạo trong worldforge và import vào project:
```
aws s3 cp <s3-world-uri> ./
unzip <world-name.zip>
```
Mở virtual desktop và chạy lệnh mở world:
```
source install/local_setup.bash
export DISPLAY=:0
roslaunch rosbot_gazebo world.launch gui:=true
```
Chạy Robot:
```
source install/setup.bash
roslaunch rosbot_description rosbot_rviz_gmapping.launch
```
## Sử dụng Teleop trong simulation. ##
Teleop là một thư viện trong ROS được sử dụng để điều khiển Robo thông qua terminal.
Khi đã có được một simulation job, ta mở terminal của simulation và gõ các lệnh sau:
```
sudo apt-get install ros-melodic-teleop-twist-keyboard
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
Ta được bảng điều khiển như hình bên dưới để Robo di chuyển
![image](https://user-images.githubusercontent.com/72614237/143812864-f30b9062-9cd6-400c-83cd-bba822ee4866.png)
