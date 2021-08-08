﻿# SailorProject 
- 程序打包命令 `windeployqt`

## `SailorProject`的所有源码是完全免费开放的，也欢迎有兴趣的小伙伴加入`水手计划`项目进行相关维护，如果你对此版本有任何建议可以尝试与作者联系，或者尝试自行修改，同时也希望大家可以将自己修改的版本开源，原作者`SEASKY`享有对此软件的所有解释权。（在使用时需要注意遵守`GPL协议`，不支持任何形式的私自产品化、商业化）。

## 记录
- 2021/7/7 日
    
    准备重新编写SerialScope软件

    - 拟定加入功能
    1. 常用的串口调试助手功能
        - 基础数据收发
        - HEX数据收发
        - 更多的多条发送配置，定时循环发送，方便指令调试
        - 界面优化
        - QT的 `QPlainTextEdit` 加载大量数据会造成界面卡顿，因此如果直接使用，高效率的接收数据会导致程序卡死，网上暂无该 `BUG`的改善措施，沿用上一个版本写的 `QPlainTextEdit` 控件，并需要再做一定的优化
    2. 自定义协议的支持 `Seasky协议` 的支持
        - `Seasky串口协议` 将满足极高的效率，将满足大多数的调试功能，不定长收发
        - 此版本软件发布版本固定最大支持 `24个float数据` 的传输，一个 `CMD_ID` ,一个 16位标志寄存器 `reg` ，如需发送24个 `float`数据，仅需发送 106 字节数据，同时具备了不定长收发功能
        - 增加和预留控件函数接口，方便扩展界面，此版本将加入基于`OpenGl`的3D 欧拉角显示功能
        - 和上次版本一样，所有解析的数据实时显示，以及所有数据汇总显示，汇总数据将加入时间戳，用于保存调试信息，拒绝字符串打印这种低效率的调试手段
    3. 同样是基于`Seasky`协议解算数据加入波形显示功能
    4. 加入浏览器支持，用于加载网页端说明文档，不再需要跳出软件打开网页链接


- 2021/7/11 日

    - 初步完成基本界面布局
    - 解决 `MSVC` 编译问题->中文注释编码格式导致编译不过
    - 由于本次采用`MSVC`编译，解决了 `MINGW`编译无法使用 `WEB` 功能的问题
    - 完成常用串口调试助手功能

- 2021/7/18 日
    - 初步完成所有功能框架
    - 加入 `Html` 功能
    - 代码比较乱，需要简单修改位置，名称，相关功能还需要移动到一起
    - 程序需要去耦合
    - 波形显示窗口鼠标右键，界面抖动问题需要解决

- 2021/7/25 日
    - 使用QSS初步优化界面
    - 开始完善控件部分功能，初步完善陀螺仪欧拉角的3D显示控件功能
    - 开始打包测试版本程序，后续群友测试，优化代码框架
    - 波形显示窗口鼠标右键，界面抖动问题需要解决

- 2021/7/27 日
    - 发布压缩包
    - 功能未完善、功能未完善、功能未完善、功能未完善、测试阶段
    - 改善界面，发送编辑窗口高度固定
    - 波形显示窗口鼠标右键，界面抖动问题需要解决  

- 2021/7/28 日
   - 解决波形显示窗口鼠标右键，界面抖动问题
        - 在此上一个版本是MINGW编译，自带的OPENGL库，所以没有兼容问题，而MSVC缺少OPENGL库，应该是自己添加的OPENGL库带来的兼容问题？
        - 修改了`qcustomplot`中的`void QCPPaintBufferGlFbo::draw(QCPPainter *painter) const` 函数

- 2021/7/30 日
    - 解决Linux串口调试时打印窗口数据混乱的问题，数据更新太快，由于使用了信号与槽分发数据，导致数据错位，更改后直接从串口流中取数据并处理，而不使用槽函数分发，不过不建立分发，需要在数据分类时，每种类型都需要做该处理，因此共享了串口类的指针
    - 重新梳理串口类的依赖关系，程序进一步去耦合，串口类多线程封装

- 2021/7/31 日
    - 进一步去耦合，优化依赖关系
    - 协议部分优化，修改到方便切换支持的最大FLOAT数据长度，方便定制化软件

- 2021/8/1 日
    - 添加多条指令发送窗口对导入csv表格的指令支持，以便于规范化、高效率的使用字符串命令调试

- 2021/8/2 日
    - 处理SEASKY协议显示窗口定时器关闭，导致刷新暂停的问题
    - 添加协议容错处理，解决发送非协议数据时，使能协议程序意外退出的问题

- 2021/8/7 日
    - 处理界面刷新相关的定时器，一共4个界面刷新相关的定时器，当且仅当切换到此界面才可以开启刷新定时器，以便于减小占用
    - 进一步优化程序，暂时不准备继续添加功能，此版本将作为V1版本发布



## 给作者加鸡腿！

| 支付宝                         | 微信                           |
|--------------------------------|--------------------------------|
| <img src="image/seaskyr1.jpg"> | <img src="image/seaskyr2.jpg"> |
