title: ConversationCallback
---

视频通话回调,创建会话时会通过 `onConversation` 方法传递会话实例对象或错误信息。

## 方法

### onConversation(Conversation, VideoException) 

**定义**   

```java
void onConversation(@Nullable  Conversation conversation,@Nullable  VideoException exception);
```

**说明**

创建视频通话时通过此接口传递 `Conversation` 和 `VideoException`。

* 视频通话创建成功 传递 `conversation` 对象,`VideoException` 为空。

* 视频通话创建失败 `conversation` 为 `null`,传递错误信息对象 `VideoException`。

**参数**

| 参数名 | 描述 |
|---|---|
|conversation|[Conversation](/video/Android/api/conversation.html),视频通话对象|
|exception|[VideoException](/video/Android/api/video-exception.html),视频通话异常对象|

**示例**

```java

	//mConversation为已经建立的视频通话
	mConversation.setConversationListener(new Conversation.Listener() {
		@Override
		public void onParticipantConnected(Conversation conversation, Participant participant) {
			RemoteStream remoteStream = participant.getRemoteStream();
			remoteStream.attach(remoteCallbacks);
		}

		@Override
		public void onFailedToConnectParticipant(Conversation conversation, Participant participant,VideoException exception) {
		}

		@Override
		public void onParticipantDisconnected(Conversation conversation, Participant participant) {
		}

		@Override
		public void onConversationEnded(Conversation conversation, VideoException exception) {

		}
    });

```
