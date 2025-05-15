# OmadaChat
Quick Start
Adding the Omada Chat Widget to your website is simple:

1.Add the script to your HTML:

<script src="https://cdn.jsdelivr.net/gh/bhargavram-fission/deepchat@254e427/deepchat.js"></script>

2.Initialize the widget with your configuration:

<script>
  document.addEventListener('DOMContentLoaded', async function() {
    if (window.OmadaChat) {
      const chat = await window.OmadaChat.init({
        // Your configuration here
        agentId: 'your-agent-id',
        workspaceId: 'your-workspace-id',
        accessToken: 'your-access-token'
      });
    }
  });
</script>

Framework Integration
The simplest way to integrate the Omada Chat Widget with any framework is by adding the script directly to your index.html file. This approach has been tested and works reliably across all major frameworks.
Direct Integration (Recommended)
For any framework (React, Vue, Angular, Next.js, Svelte, etc.), you can add the widget by including the script in your main HTML file:


<!-- In your index.html file -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Your App</title>
</head>
<body>
  <div id="root"></div>
  <!-- Your framework's root element -->
  
  <!-- Add the Omada Chat Widget script -->
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

This method works regardless of your framework because the widget creates its own isolated DOM elements and doesn't interfere with your application's rendering.

Configuration Options
The widget can be customized with the following options:

await window.OmadaChat.init({
  // Required for connecting to the backend
  agentId: 'your-agent-id',           // Your agent ID
  workspaceId: 'your-workspace-id',   // Your workspace ID
  accessToken: 'your-access-token',    // Authentication token
  
  // Alternative: Direct connection URL
  // connectUrl: 'https://your-backend-url',
  
  // User interface customization
  toggleText: "💬",                    // Text/emoji on the chat button
  headerTitle: "Omada Assistant",      // Title in the chat header
  headerSubTitle: "How can I help?",   // Subtitle in the chat header
  headerColor: "#0057F3",              // Header background color
  toggleColor: "#0057F3",              // Chat button color
  
  // Position settings
  position: "bottom-right",            // Position of the chat button (bottom-right, bottom-left, top-right, top-left)
  chatContainerPosition: "bottom-right", // Position of the chat window
  
  // Message settings
  introMessage: "Hello! How can I assist you today?", // First message displayed
  
  // Avatar settings
  avatars: true,                       // Show avatars for messages
  customizeAvatarImageForAI: "https://your-ai-avatar.png", // Custom AI avatar image URL
  customizeAvatarImageForUser: "https://your-user-avatar.png", // Custom user avatar image URL
  
  // Connection settings
  websocket: false,                    // Use WebSocket (default: false)
  stream: true,                        // Enable streaming responses (default: true)
  
  // Input field customization
  textInputPlaceholder: {
    text: "Type a message...",
    style: { color: "#bcbcbc" }
  },
  
  // Error message customization
  errorMessages: {
    displayServiceErrorMessages: false,
    overrides: {
      default: "Something went wrong. Please try again.",
      service: "Unable to connect to server.",
      speechToText: "Voice input failed."
    }
  },
  
  // Message styling
  messageStyles: {
    error: {
      bubble: {backgroundColor: "#ff0000", color: "#ffffff", fontSize: "15px"}
    },
    default: {
      shared: {bubble: {color: "white"}},
      ai: { bubble: { backgroundColor: "#F3F5F7", color: "#000000", padding: "10px" } },  
      user: { bubble: { backgroundColor: "#0057F3" } }  
    }
  }
});

Framework-Specific Component Integration
If you prefer to manage the widget as a component within your application, you can use the following approaches:

React

import { useEffect } from 'react';

function ChatComponent() {
  useEffect(() => {
    // Load the script
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

    // Clean up
    return () => {
      document.body.removeChild(script);
    };
  }, []);

  return null; // This component doesn't render anything itself
}

export default ChatComponent;
