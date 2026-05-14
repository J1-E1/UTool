https://docs.unity3d.com/Packages/com.unity.cinemachine@3.1/manual/CinemachinePanTilt.html

![[Pasted image 20251126143218.png]]

- 可以用来平移或者倾斜摄像机， 本身不读取用户输入
- 可以通过[Cinemachine Input Axis Controller](https://docs.unity3d.com/Packages/com.unity.cinemachine@3.1/manual/CinemachineInputAxisController.html)组件驱动

属性

![[Pasted image 20251126143326.png]]


| 属性                  |                           | **Function:**                                                         |
| ------------------- | ------------------------- | --------------------------------------------------------------------- |
| **Reference Frame** |                           | 定义进行平移和倾斜旋转的坐标系                                                       |
|                     | _Parent Object_           | 如果 CinemachineCamera 有父对象，则使用该父对象的局部坐标系作为参考系。如果没有父对象，则使用世界坐标系。        |
|                     | World                     | 将以世界坐标系作为参考系。                                                         |
|                     | _Tracking Target_         | 如果 CinemachineCamera 具有跟踪目标，则该目标的局部坐标轴将用作参考系。如果没有父对象，则将使用世界坐标轴。       |
|                     | _LookAt Target_           | 如果 CinemachineCamera 具有 LookAt 目标，则该对象的局部坐标系将用作参考系。如果没有父对象，则将使用世界坐标系。 |
|                     |                           |                                                                       |
| **Pan Axis**        |                           |                                                                       |
|                     | _Value_                   |                                                                       |
|                     | _Center_                  |                                                                       |
|                     | _Range_                   |                                                                       |
|                     | _Wrap_                    |                                                                       |
|                     |                           |                                                                       |
| **Tilt Axis**       |                           |                                                                       |
|                     | _Value_                   |                                                                       |
|                     | _Center_                  |                                                                       |
|                     | _Range_                   |                                                                       |
|                     | Wrap                      |                                                                       |
|                     |                           |                                                                       |
| **Recentering**     |                           |                                                                       |
|                     |                           |                                                                       |
|                     |                           |                                                                       |
|                     |                           |                                                                       |
| **Recenter Target** |                           | 当发生轴线重新定位时，它将向该目标重新定位。                                                |
|                     | AxisCenter                | 以轴内定义的中心值为中心进行重新定位。                                                   |
|                     | _Tracking Target Forward_ | 将中心重新定位到与跟踪目标的前向轴一致的值。                                                |
|                     | _LookAt Target Forward_   | 将中心重新定位到与 LookAt Target 的前向轴一致的值。                                     |
|                     |                           |                                                                       |
|                     |                           |                                                                       |
