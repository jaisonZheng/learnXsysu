# learnXsysu

经常错过DDL？  
常常错过一大堆通知中鱼龙混杂的重要通知？  
不想打开微信/企微/钉钉寻找课程群？   
手机“dingdingdingding”疯狂响，打开发现只是同学们在闲聊？   
你需要：**learnXsysu**

> **learnXsysu**
> All In One - 重塑你的学习秩序
> 将**作业**、**通知**、**DDL**、**课表**、**文件**集于一体，所有学业信息**一站即达**。

## 核心功能：
- 将分散在微信、企微、钉钉、QQ的群聊通知、作业集合总结到一起。
- 自动计算DDL，并提供DDL提醒
- 根据不同课程整理文件， 并将所有文件集合到一起（类似于MacOS的“下载”）

## 页面展示
### ios端：
<img width="300"  alt="IMG-20251124104743999" src="https://github.com/user-attachments/assets/92a81c70-9d43-4a1d-9db8-cbc050e646ee" />
<img width="300"  alt="IMG-20251124104744057" src="https://github.com/user-attachments/assets/3440efce-bc50-4f85-9463-785a5300c842" />
<img width="300"  alt="IMG-20251124104744126" src="https://github.com/user-attachments/assets/ef6ff698-4e4c-438a-aca5-98a853befac4" />

### Android端:
<img width="300"  alt="IMG-20251124123020234" src="https://github.com/user-attachments/assets/0b2952e0-b7a3-4575-8b20-33976b3cff52" />
<img width="300"  alt="IMG-20251124123058208" src="https://github.com/user-attachments/assets/41793460-f8af-4cd5-a70e-4589ba3ffd03" />

（由于当前的测试数据是我转发给自己的微信小号然后让爬虫服务器爬的，所以来源和课程名称都暂时不正确，实际使用时“中山大学”处会显示群聊/课程名称，learnXsysu会变成发布通知/作业的人的名字）
## 实现原理
<img width="1008" height="733" alt="IMG-20251125092522587" src="https://github.com/user-attachments/assets/c6a8142f-e8ff-4199-ac8e-b125de1bfa76" />
简单来说，就是利用windows上的盲人模式（可以这么理解），定时爬取微信/企业微信/钉钉/QQ的信息，先进行去重，然后经过大模型and脚本的数据清洗（结构化处理+判断是否有价值），发送到部署在腾讯云的云服务器，然后再分发到客户端。

其中，用到/借鉴了以下的开源项目：
- 客户端：[清华的learnX](https://github.com/robertying/learnX)（这也是这个项目的灵感来源）
- LLM工作流：[Dify](https://github.com/langgenius/dify/)
- RPA：
	[Python-UIAutomation-for-Windows](https://github.com/yinkaisheng/Python-UIAutomation-for-Windows)
	[WeChat3.9-32bit-Compatibility-Launcher](https://github.com/Skyler1n/WeChat3.9-32bit-Compatibility-Launcher)
	[wechat_utils](https://github.com/myworkMd/wechat_utils)


## 项目当前状况
### 当前未完成部分：
- 针对企业微信和钉钉的RPA(Robotic Process Automation)还没做。
	当前只做了针对微信的RPA。
- 课程表导入功能
- 文件集中功能
- 网站端（可选）
	当前只有ios端和android端，而且我对于ios端上线App Store699元的年费感到些许困扰。
	
### 项目局限性：
- 微信小号可能会被封。
	为了避免找每个群的群主申请引入一个群聊机器人，采用了基于windows系统的uiautomation的RPA，但是其实是有一定的被封风险的，而且和上次那个羽毛球抢场脚本不同，这个项目我还没怎么做反反爬虫机制。
	
- 需要其他年级的同学的账号才能拿到其他年级的信息。
	当前这个版本只能拿到2024级的信息，这显然是不够的。
	但是就算我借了其他年级的同学的账号，我仍然担心我那台陈旧的windows电脑（爬虫服务器）能不能支撑地了一个虚拟桌面。（已经部署了一个dify在docker上了）
	
- 项目的复制难度较大
	比如说，假如我想把这个东西给国金的同学用，我就得要他们的一个企业微信/钉钉/微信小号账号长期登在一台windows爬虫服务器上。

### 项目后续发展：
针对软件的RPA其实开发起来特别麻烦（我搞微信就搞了接近3天），所以针对企业微信和钉钉的RPA可能要搞很久。

苏书最近要忙别的事，所以项目可能会暂时搁置一段时间。

然后也想看看有没有对这个项目感兴趣的同学，可以一起做（该项目为开源项目），现在只是跑通了流程，还是剩下了很多很有挑战性的部分没做的。

唉，鉴于项目的麻烦程度和复制成本，我有点怀疑这个项目的价值，要是大家觉得这个玩意很有价值或者很没价值，或者有什么建议啥的，都可以和我说。
