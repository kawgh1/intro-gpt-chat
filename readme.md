### Chat style LLMs

- There (at least) two basic types of LLMs, traditional (or completion style) and chat style. Traditional is an input in output out kind of flow. There's no context between input requests unless they are chained together.

- In Traditional or Completion style LLMs, the LLM is given a string of text and provides back it's best guess to complete the string of text, according to various parameters (tone, length, etc.)

  - Ex.) "Taxes are bad because" --> "Taxes are bad because they take money out of the economy"

- In Chat style LLMs, there is a back and forth dynamic for the duration of the chat session. This creates the appearance of a more natual interaction, conversational.
  - The GPT does not actually remember anything the user just sent them. It doesn't remember the conversation message by message. The only way it keeps context is if the user (under the hood) sends back the entire conversation with each new request to the GPT.
  - ![chat_example](https://raw.githubusercontent.com/kawgh1/intro-gpt-chat/main/images/GPT%20Chat%20Conversation.png)

### LangChain

- A lot of LangChain assumes you are using **completion** style models.
- They are probably planning for a future where ChatGPT isn't the best LLM model around.
- A ton of documentation assumes you are using a **completion** model. Many **LangChain** Classes are designed to only work with **completion models**. Keep this in mind. It can require tweaking the baseline LangChain functionality to work with a Chat-style LLM.

### Memory

- LangChain has many kinds of memory

  - ConversationTokenBufferMemory
  - CombinedMemory
  - ConversationBufferWindowMemory
  - etc.

- ConversationBufferMemory

  - This is the Memory we are going to use to keep track of our session conversation with ChatGPT, so that we send a complete transcript of the latest conversation with each new message to ChatGPT. This allows us to reference previous messages in the chat. It allows for ChatGPT to "remember what we were talking about." Except, really it isn't. It's just referencing prior chat data we are sending it. It does not remember anything.

- `from langchain.memory import ConversationBufferMemory, FileChatMessageHistory`
  - Using `FileChatMessageHistory` we can save our conversations to a file like `messages.json` or to a DB or Redis or anywhere. This allows us to return any user's previous conversations to a Chat session so the user can pick up where they left off on an old conversation, or start a new one.
