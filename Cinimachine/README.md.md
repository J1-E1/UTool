
核心分为3个部分：unity Camera ，Cinemachine Brain， Cinemachine Cameras

![[Pasted image 20251024085247.png]]

- 一个unity摄像机，用于捕捉整个场景中的图像
- Cinemachine核心组件，用于Unity摄像机中启用Cinemachine功能
- 一个或者多个Cinemachine摄像机，根据状态轮转控制Unity摄像机

####  Unity Camera
- Cinimachine 设置，必须包括唯一的一个Unity相机
- 该相机将成为唯一

#### Cinemachine Brain
- 必须包含一个Brain组件
- 它用来监控所有激活的场景中的Cinemachine Cameras 
- 处理不同相机之间的过渡效果
- 使用Timeline，其优先级将比，CinemachineBrain的级别更高

### Cinemachine Cameras
- 当Cinemachine Camera接管Unity 相机是，会动态覆盖其属性和行为
- 独立，可通过额外的Cinemachine组件来管理程序化并扩展功能
