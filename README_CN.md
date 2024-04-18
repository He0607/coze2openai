# C2O
[English](README.md) · **中文** 

**在您喜爱的 OpenAI 客户端上使用 Coze.**

该项目将 Coze API 转换为 OpenAI API 格式，使您可以在您喜爱的 OpenAI 客户端中访问 [Coze](https://www.coze.com) 的LLMs、知识库、插件和工作流程.

# 特点
- 将 Coze API 转换为 OpenAI API
- 支持流式和阻塞
- 在 Coze 上支持 Chatbots API

# 准备工作
1. 在 [Coze](https://www.coze.com)注册并获取您的 API 令牌
![cozeapitoken](pictures/token.png)

2. 创建您的机器人并发布到 API
![cozeapi](pictures/api.png)

3. 获取机器人的 ID，即机器人参数后面的数字，并将其配置为环境变量
```bash
https://www.coze.com/space/73428668341****/bot/73428668*****
```

# 部署
## Zeabur
[![Deploy on Zeabur](https://zeabur.com/button.svg)](https://zeabur.com/templates/BZ515Z?referralCode=fatwang2)

## Vercel
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/fatwang2/coze2openai&env=BOT_ID&envDescription=COZE_BOT_ID)

**注意:** Vercel 的无服务器函数有 10 秒的超时限制

# 本地部署
1. 首先把`.env.template`文件复制改名为`.env`

2. 在 .env 文件上设置环境变量
```bash
BOT_ID=xxxx
```

3. 安装依赖项
```bash
pnpm install
```

4. 运行项目
```bash
pnpm start
```

**注意:** 浏览器打开你部署的网址是否显示dify2openai部署成功
```bash
http://ip:3000
```

5. 停止程序
如果想要关闭程序可以执行 ```kill -9 <进程ID>``` 来完成，执行以下命令可以查看当前进程的 id：
```bash
sudo lsof -i :3000
```

# 用法
```JavaScript
const response = await fetch('http://localhost:3000/v1/chat/completions', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer YOUR_COZE_API_KEY',
  },
  body: JSON.stringify({
    model: 'Coze',
    messages: [
      { role: 'system', content: 'You are a helpful assistant.' },
      { role: 'user', content: 'Hello, how are you?' },
    ],
  }),
});

const data = await response.json();
console.log(data);
```

# 环境变量
该项目提供了一些额外的配置项，通过环境变量设置：

| 环境变量 | 必须的 | 描述                                                                                                                                                               | 例子                                                                                                              |
| -------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `BOT_ID`     | Yes      | 机器人的 ID。从 Coze 中机器人的开发页面 URL 获取它。 bot参数后面的数字是bot ID.| `73428668*****`|

# 路线图
**即将推出**
*   图像支持
*   音频转文字
*   文本转语音
*   Docker 部署
*   工作流机器人
*   变量支持

**现在可用**
*   持续对话
*   Zeabur＆Vercel&Railway＆Railway 部署
*   流式和非流式传输
*   Coze 插件

# 联系
如有任何问题或反馈，请随时联系

[X](https://sum4all.site/twitter)\
[telegram](https://sum4all.site/telegram)

<a href="https://www.buymeacoffee.com/fatwang2" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

# 许可证
该项目在 MIT 许可证下获得许可.
