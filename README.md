# YaoYaoLe

>  这是一个基于FPGA的“摇摇乐”3D实时姿态同步工具。 
>
>  2020年新工科联盟-Xilinx暑期学校（Summer School）项目

### Inctroduction

##### Project Description 项目简介

​		This project is a 3D posture simulation project based on `FPGA`. It reads the posture data of the onboard gyroscope and uploads it to the remote server to display the 3D posture model. This is a real-time attitude transmission system, which can upload the attitude information (how to rotate, etc.) of the device (`Sea-Board`) networked via `WiFi` to a remote server for display. The display method is a real-time 3D model: a Six-sided cube cube (currently still a short version).



​		本项目是一个基于`FPGA`的3D姿态模拟项目，通过读取板载陀螺仪的姿态数据，上传至远程服务器，展示3D姿态模型。这是一个实时的姿态传输系统，能够将通过`WiFi`联网的设备(`Sea-Board`)的姿态信息（如何转动等）上传至远程服务器进行展示，展示的方式是实时的3D模型：一个六面的方块cube（目前还是简略版）。



##### Project system 项目系统

This is the structure diagram of the project components

这是项目组件的结构框图

![system](system.jpg)



---



### Install

​		This project uses [Vivado(2019.1)](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/2019-1.html) and [Arduino(1.8.13)](https://www.arduino.cc/en/Main/Software). Go check them out if you don't have them locally installed.

​		该项目使用[Vivado(2019.1)](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/2019-1.html)和[Arduino(1.8.13)](https://www.arduino.cc/en/Main/Software)。 如果您没有在本地安装它们，请点击链接下载安装。



---



### Deployment steps

- The onboard gyroscope transmits the original gyroscope attitude data through the IIC and gyroscope drive module.

- The driver module stores the original data in `RAM` after processing. Using `RAM` and `QSPI` modules, Esp32 can access the data in RAM through the `QSPI` interface.

- Esp32 connects to `AWS IoT` and uploads the onboard gyroscope data to the `IoT` cloud.

- Create a `HTML` web page to realize a 6-sided `cube` that can rotate around the central axis, and each side is distinguished by a number with a different color.

- Use the `IoT` cloud `Web API` to transfer cloud data to other web services (web server in this project), which is used to present the `cube` 3D posture online simulation.

  

- 板载的陀螺仪通过IIC与陀螺仪驱动模块传递原始的陀螺仪姿态数据。
- 驱动模块将原始数据经过处理后存于`RAM`，利用`RAM`与`QSPI`模块，Esp32可以通过`QSPI`接口访问RAM中的数据。
- Esp32连接`AWS IoT`，将板载陀螺仪数据上传至`IoT`云端。
- 创建`HTML`网页，实现可绕中心轴旋转的6面`cube`，每一面附上不同的颜色的数字加以区分。
- 利用`IoT`云端 `Web API`，将云上数据传给其他Web服务（此项目中为网站服务器），用于呈现`cube`3D姿态在线模拟。



---



### Project demo

This is the demo at this stage

这是现阶段的demo

![demo](demo_latest.gif)



---



### Project expand

​		On the HTML webpage displayed in real-time posture, the `cube` can be replaced with various 3D objects (such as steering wheels, cars, cartoon characters, tumblers, etc.). 

​		By modifying the model on the webpage, or adding some interactions, you can simulate driving, play a tumbler, etc., realize many expansion functions, and exert great potential.

​		在实时姿态展示的HTML网页上，`cube`六面魔方可以替换为各类3D物样（如方向盘，小车，卡通人物，不倒翁等等）。

​		通过修改网页上的模型，或增添一些交互，可以模拟开车，玩不倒翁等等，实现许多拓展功能，发挥潜力很大。



---



### Change Log

##### v0.1.1

- Modified the three-axis angular velocity data transmission relationship, and solved the problem that the on-board gyroscope is synchronized with the flip direction of the webpage `cube`.
- Updated and improved the structure of the project system.

- 修改了三轴角速度数据的传输关系，解决了板载陀螺仪与网页`cube`翻转方向同步一致的问题。

- 更新完善了项目系统的结构。

  

##### v0.1.2

- The refresh rate has been updated and the sensitivity of the `cube` rotation has been optimized.

- 更新了刷新频率，优化了`cube`旋转的灵敏度。
