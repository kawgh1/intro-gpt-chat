### Chat style LLMs

- There (at least) two basic types of LLMs, traditional and chat style. Traditional is an input in output out kind of flow. There's no context between input requests unless they are chained together.

- In Chat style LLMs, there is a back and forth dynamic for the duration of the chat session. This creates the appearance of a more natual interaction, conversational.
  - The GPT does not actually remember anything the user just sent them. It doesn't remember the conversation message by message. The only way it keeps context is if the user (under the hood) sends back the entire conversation with each new request to the GPT.
  - ![chat_example](https://raw.githubusercontent.com/kawgh1/intro-gpt-chat/main/images/GPT%20Chat%20Conversation.png)
