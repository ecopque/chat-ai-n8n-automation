# Chatbot with AI + Google Sheets Storage using N8N

This project demonstrates how to create an intelligent chatbot using Groq AI, automatic message storage in Google Sheets, and conversational memory—all powered by **n8n**, a low-code automation platform.

## What this project does

- Captures user messages in a public chat
- Stores each message along with a session ID in Google Sheets
- Responds with a friendly AI assistant
- Maintains conversation context using memory
- Can perform calculations and fetch answers from Wikipedia

## Tools used

- [n8n.cloud](https://n8n.io) (automation platform)
- [Groq](https://groq.com) (AI model)
- Google Sheets (data storage)
- Wikipedia and Calculator (AI tools)

## Project screenshots

- Workflow overview:  
  [Insert image link here]

- Example spreadsheet:  
  [Insert image link here]

- Chat interface in action:  
  [Insert image link here]

## Step-by-step: Building the workflow

1. **Create a new workflow**
   - On the n8n dashboard, click **Start from scratch**
   - Click **Add first step...**

2. **Add the trigger**
   - Search for the trigger `On Chat Message`
   - Click **Open Chat**, type "Hi", and confirm the green check appears

3. **Transform incoming data**
   - Add the node `Data Transformation > Set`
   - Drag `sessionId` to the center panel and rename it to `idChat`
   - Click **Add Field**, type `Message`, and drag `chatInput` into the value field
   - Test the node with **Execute step**

4. **Save messages in Google Sheets**
   - Add the node `Google Sheets > Append Row in Sheet`
   - Set up credentials by signing in with your Google account
   - Create a spreadsheet named `file_message`, with headers `idChat` and `Message` in row A1 and B1
   - Rename the sheet tab to `Case 1`
   - Map `idChat` and `Message` to their respective fields
   - Execute the step and confirm that data appears in the spreadsheet

5. **Add AI capabilities**
   - Add the node `AI Agent`
   - Choose the `Groq Chat Model` and configure it using your API key
   - In **Prompt (User Message)**, select the `Message` field
   - Add a **System Message** with the following prompt:
     "You are a super helpful support agent. Be polite, humorous, and use emojis in your responses to make the conversation more human."
   - Execute the step to test

6. **Enable memory**
   - Add the node `Memory > Simple Memory`
   - Set **Session ID > Define below** and use the `idChat` field

7. **Add extra tools**
   - Add the nodes `Tool > Calculator` and `Tool > Wikipedia`

8. **Finalize the workflow**
   - Add a node called `No Operation (Do nothing)`
   - Click **Save** to store the workflow
   - In the chat trigger node, enable **Make Chat Publicly Available**
   - Set an initial message such as:
     "Hello, how can I help you today?"
   - On the main workflow page, click **Inactive** to activate the workflow

## Public chat link

You can interact with the chatbot via the following public link:  
https://edsoncopque.app.n8n.cloud/webhook/3db478a9-177a-4c07-89fc-e1fe0ca1c5b9/chat

## Available files

- `workflow-chat-ai.json`: exported n8n workflow
- `sample-spreadsheet.csv`: example Google Sheets file
- `README.md`: complete setup instructions

## Contributions

Feel free to open issues, suggest improvements, or customize the workflow for other use cases such as customer support, CRM integration, or automated FAQ systems.

## Images

This project is licensed under the MIT License.

