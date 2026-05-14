
- 使用两个组件来决定动作取景的方式

- **Camera Controllers:** 一个attach在camera上的组件，正常情况下为Main Camera组件是主要的Camera Controller
- **Camera Shot:**  多种设置联系Camera Conroller

= 
- 例如，如果Main Camera 于Third person Camera有关，， 使得Main camera可以模仿该视角的行为跟随并切换注释目标，用户围绕目标旋转
- Camera Controller 能切换到另一个Camera shot， Transition 可以发生一段时间，或者立即