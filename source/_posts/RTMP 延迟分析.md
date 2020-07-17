---
延迟分析
---
#RTMP
RTMP是Real Time Messaging Protocol（实时消息传输协议）的首字母缩写。该协议基于TCP，是一个协议族，包括RTMP基本协议及RTMPT/RTMPS/RTMPE等多种变种。

RTMP是一种设计用来进行实时数据通信的网络协议，主要用来在Flash/AIR平台和支持RTMP协议的流媒体/交互服务器之间进行音视频和数据通信。支持该协议的软件包括Adobe Media Server/Ultrant Media Server/red5等。

* RTMP工作在TCP之上，默认使用端口1935；
* RTMPE在RTMP的基础上增加了加密功能；
* RTMPT封装在HTTP请求之上，可穿透防火墙；
* RTMPS类似RTMPT，增加了TLS/SSL的安全功能。

[来自](https://www.jianshu.com/p/5ce11c20a9df)

# RTMP 延迟分析
RTMP和HLS基本上可以覆盖所有客户端观看

* HLS主要是延时比较大
* RTMP主要优势在于延时低

# 应用场景（Verify）

低延时应用场景包括：

* 互动式直播：譬如2013年大行其道的美女主播，游戏直播等等。
	* 各种主播，流媒体分发给用户观看。用户可以文字聊天和主播互动。
     
* 视频会议：我们要是有同事出差在外地，就用视频会议开内部会议。
	*  其实会议1秒延时无所谓，因为人家讲完话后，其他人需要思考。
	*  思考的延时也会在1秒左右。当然如果用视频会议吵架就不行。
	
*  其他：监控，直播也有些地方需要对延迟有要求。
	*  互联网上RTMP协议的延迟基本上能够满足要求。
# 来源
1. [为什么流媒体直播的延迟很高](https://draveness.me/whys-the-design-live-streaming-latency/)
2. [RTMP 延迟分析](https://blog.csdn.net/lcalqf/article/details/52993630)
3. [视频和视频帧：ffmpeg的RTMP推流](https://zhuanlan.zhihu.com/p/73984438)
4. [视频传输协议详解（RTMP、RTSP、HLS）](https://www.jianshu.com/p/c04d810b7562)
5. [RTMP协议解析（一） —— 基本了解](https://www.jianshu.com/p/5ce11c20a9df)
6. [流媒体系统的RTMP协议](https://zhuanlan.zhihu.com/p/27368329)
7. [通过信号量和共享内存实现h264码流在不同进程间传输](https://blog.csdn.net/dong_beijing/article/details/60776248)
