# Omada Chat Widget

 ## Omada Chat Widget provides a floating chat interface with support for real-time messaging, customizable UI, and seamless backend integration.



### ✅ Framework-agnostic - works with any JavaScript framework

⚡ Quick Start
#### 1. Add the script to your HTML

```html 
  <script src="https://cdn.jsdelivr.net/gh/bhargavram-fission/OmadaChat/OmadaCDN.js"></script>
 ```

#### 2. Initialize the widget with your configuration

```html
<script>
  document.addEventListener('DOMContentLoaded', async function() {
    if (window.OmadaChat) {
      const chat = await window.OmadaChat.init({
        agentId: 'your-agent-id',
        workspaceId: 'your-workspace-id',
        accessToken: 'your-access-token'
      });
    }
  });
</script>
```

### Framework Integration
#### Direct Integration (Recommended)
##### Just place the script in your index.html file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Your App</title>
</head>
<body>
  <div id="root"></div>

  <script src="https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js"></script>
  <script>
    document.addEventListener('DOMContentLoaded', async function() {
      if (window.OmadaChat) {
        const chat = await window.OmadaChat.init({
          agentId: 'your-agent-id',
          workspaceId: 'your-workspace-id',
          accessToken: 'your-access-token'
        });
      }
    });
  </script>
</body>
</html>
```

### Framework-Specific Integrations
#### For React Js Integration
```jsx

import { useEffect } from 'react';

function ChatComponent() {
  useEffect(() => {
    const script = document.createElement('script');
    script.src = 'https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js';
    script.async = true;
    script.onload = async () => {
      if (window.OmadaChat) {
        await window.OmadaChat.init({
          agentId: 'your-agent-id',
          workspaceId: 'your-workspace-id',
          accessToken: 'your-access-token'
        });
      }
    };
    document.body.appendChild(script);
    return () => {
      document.body.removeChild(script);
    };
  }, []);
  return null;
}
export default ChatComponent;
```
#### For Vue Js Integration
```jsx

<template>
  <div></div>
</template>

<script>
export default {
  name: 'OmadaChatWidget',
  mounted() {
    const script = document.createElement('script');
    script.src = 'https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js';
    script.async = true;
    script.onload = async () => {
      if (window.OmadaChat) {
        this.chatWidget = await window.OmadaChat.init({
          agentId: 'your-agent-id',
          workspaceId: 'your-workspace-id',
          accessToken: 'your-access-token'
        });
      }
    };
    document.body.appendChild(script);
  }
}
</script>
```

#### For Angular Integration

```ts

import { Component, OnInit, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-chat-widget',
  template: '',
})
export class ChatWidgetComponent implements OnInit, OnDestroy {
  private scriptElement: HTMLScriptElement | null = null;

  ngOnInit(): void {
    this.scriptElement = document.createElement('script');
    this.scriptElement.src = 'https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js';
    this.scriptElement.onload = async () => {
      if (window.OmadaChat) {
        await window.OmadaChat.init({
          agentId: 'your-agent-id',
          workspaceId: 'your-workspace-id',
          accessToken: 'your-access-token'
        });
      }
    };
    document.body.appendChild(this.scriptElement);
  }

  ngOnDestroy(): void {
    if (this.scriptElement) {
      document.body.removeChild(this.scriptElement);
    }
  }
}
```

#### For Next Js Integration

```Jsx

import { useEffect } from 'react';

export default function ChatWidget() {
  useEffect(() => {
    if (typeof window !== 'undefined') {
      const script = document.createElement('script');
      script.src = 'https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js';
      script.async = true;
      script.onload = async () => {
        if (window.OmadaChat) {
          await window.OmadaChat.init({
            agentId: 'your-agent-id',
            workspaceId: 'your-workspace-id',
            accessToken: 'your-access-token'
          });
        }
      };
      document.body.appendChild(script);
      return () => {
        document.body.removeChild(script);
      };
    }
  }, []);
  return null;
}
```

 
## Configuration Options
```js

await window.OmadaChat.init({
  agentId: 'your-agent-id',
  workspaceId: 'your-workspace-id',
  accessToken: 'your-access-token',
  toggleText: "💬",
  headerTitle: "Omada Assistant",
  headerSubTitle: "How can I help?",
  headerColor: "#0057F3",
  toggleColor: "#0057F3",
  position: "bottom-right",
  chatContainerPosition: "bottom-right",
  introMessage: "Hello! How can I assist you today?",
  avatars: true,
  customizeAvatarImageForAI: "https://your-ai-avatar.png",
  customizeAvatarImageForUser: "https://your-user-avatar.png",
  websocket: false,
  stream: true,
  textInputPlaceholder: {
    text: "Type a message...",
    style: { color: "#bcbcbc" }
  },
  errorMessages: {
    displayServiceErrorMessages: false,
    overrides: {
      default: "Something went wrong. Please try again.",
      service: "Unable to connect to server.",
      speechToText: "Voice input failed."
    }
  },
  messageStyles: {
    error: {
      bubble: { backgroundColor: "#ff0000", color: "#ffffff", fontSize: "15px" }
    },
    default: {
      shared: { bubble: { color: "white" } },
      ai: { bubble: { backgroundColor: "#F3F5F7", color: "#000000", padding: "10px" } },
      user: { bubble: { backgroundColor: "#0057F3" } }
    }
  }
});
```
