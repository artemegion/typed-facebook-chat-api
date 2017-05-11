# Typings for [facebook-chat-api](https://www.npmjs.com/package/facebook-chat-api) module
These typings are built basing on the [documentation](https://github.com/Schmavery/facebook-chat-api/blob/master/DOCS.md). Typings are tested on the bleeding edge version of facebook-chat-api and are updated accordingly (with some delay of course).

# How to install
The below command will install newest version of the typings, they should match the bleeding edge version of [facebook-chat-api](https://github.com/Schmavery/facebook-chat-api#bleeding-edge).
```batch
typings install facebook-chat-api=github:legion44/facebook-chat-api-typings/index.d.ts --global --save
```

The below command will install typings compatible with [faceboot-chat-api commit 2ad4b25abdc594b63c87692843308e5d26050570](https://github.com/Schmavery/facebook-chat-api/commit/2ad4b25abdc594b63c87692843308e5d26050570)
```batch
typings install faceboot-chat-api=github:legion44/facebook-chat-api-typings/index.d.ts#fdf8bfc69126ee2ff254c4f86dcc68577e6910f1 --global --save
```

# Example usage
```typescript
import login = require('facebook-chat-api');

// Create simple echo bot
login({ email: 'FB_EMAIL', password: 'FB_PASSWORD' }, (err: Facebook.ILoginError, api: Facebook.API) => {
    if(err) return console.error(err);

    // note that if you also want to receive events, you will want message to be `IReceived` instead of `IReceivedMessage`
    api.listen((err: Facebook.IError, message: Facebook.IReceivedMessage) => {
        let response: Facebook.IMessage = {
            body: message.body
        };

        api.sendMessage(response, message.threadID);
    });
});
```