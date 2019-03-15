微信最新版本下载:https://dldir1.qq.com/weixin/Windows/WeChatSetup.exe  
wehub最新版本下载:https://s.weituibao.com/wehub/package/WeHubSetup0.3.13.exe

支持2.6.4.56|2.6.5.38|2.6.6.28 |2.6.7.40 这几个版本的微信

使用wehub是否会导致封号?

WeHub只是一个提供些许便利的工具软件,无法保证你的微信不被封号.

是否封号取决于你使用工具做了什么(微信后台后分析和记录你的行为特征),当你无节制地滥用工具时,封号将是不可避免的.请心怀敬畏,用合适的工具做合适的事.

------

wehub 回调接口开发文档:  
https://github.com/fangqing/wehub-callback/blob/master/wehub-api-doc-v2.md

faq:在与第三方企业在对接过程中遇到的相关问题的记录(整理中)     
https://github.com/fangqing/wehub-callback/blob/master/faq.md

微信消息的静态表情转义对照表见emoji_index.html 或
https://s.weituibao.com/wehub/Emoji/emoji_index.html

------
对接的demo(php版) : https://github.com/tuibao/wehub-demo-php  
对接的demo(python版): https://github.com/fangqing/wehub_callback_server  

(demo仅展示数据的处理方式)

------
版本更新记录:  

- 2019.3.15:

  发布0.4.0 :客户端强制做安全验证, 新增检测更新功能(下次升级可支持通过客户端进行升级).

  添加对僵尸粉检测任务的支持.

  https://s.weituibao.com/wehub/package/package/WeHubSetup0.4.0.exe

- 2019.2.28:   
发布0.3.13, 对0.3.12版本中适配出现的问题的进行修复  
https://s.weituibao.com/wehub/package/WeHubSetup0.3.13.exe

- 2019.2.26:   
  发布0.3.12版本,适配支持微信最新的2.6.7.40版本  
  https://s.weituibao.com/wehub/package/WeHubSetup0.3.12.exe

- 2019.1.18:   
  发布0.3.8版本:  新增report_friend_removed (上报好友被删除的事件)

- 2018.12.27:

    发布0.3.6版本:  增加缓存清理功能  

-  2018.12.11:

   发布 0.3.3 版本:上报的文本消息中新增atuserlist字段;支持上传文件消息中的文件


- 2018.11.30:

  发布 0.3.0 版本
  
  适配微信最近发布的新版本2.6.6.28( !!注意在2.6.5.38 和2.6.6.28 之间微信临时推出了2.6.6.25版本,我们没有适配和支持这个版本)

  支持消息中的语音上传

  支持下发gif表情任务

  report_contact 中增加公众号信息

- 2018.11.16

  发布 0.2.15版本:

  适配微信最近发布的新版本2.6.5.38,同时修正了之前微信中的图片与视频在每天某时间段内(每天18:00之后)不自动下载的问题.

- 2018.10.23:

  发布0.2.6,新增action "report_contact_update",用于改进上报的联系人列表不全的问题.

- 208.10.17

   发布0.2.3: login 中增加 "local_ip" 字段

-  2018.10.12:
    发布wehub 0.2.2

出于安全性考虑,自0.2.2版本开始,wehub引进了"安全性验证"机制. 请第三方管理员请登录wehub后台 http://wehub.weituibao.com  对回调参数进行配置, 系统会自动为每一个appID生成了单独的"secret key",第三方管理员可以开启/关闭 "安全性验证"(默认不开启安全性验证). 若在后台开启安全性验证,回调接口必须在收到 wehub 的login request后将正确签名返回给wehub客户端进行校验. 详情见文档 wehub-api-doc-v2.md

<u>**回调接口必须实现对login的正确处理,否则使用相应appid的wehub 客户端将无法使用**</u>



- 2018.9.28:
  发布wehub 0.2.0

```
1.简化了ack中的协议
2."发消息任务"的任务类型数据结构有调整:  
调整前的数据结构为:
{
    "task_type": 1,  
    "task_dict":
    {
    	"room_wxid": "xxxxxx",  
    	"wxid":"xxxxxxx",	   				  
    	"msg_list":[$push_msgunit,$push_msgunit,....]
	}
}

调整后的数据结构为
{
   "task_type": 1,  
   "task_dict":
    {
        "wxid_to":"xxxxxx",  	
        "at_list":['xxxx','xxxx'],  
    	"msg_list":[$push_msgunit,$push_msgunit,....]
	}
}

调整后发群消息时可以at多个微信号了(原来只能at一个微信号)
```
