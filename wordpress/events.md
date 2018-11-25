# Events & Nodes
- [Types of Event](#types-of-event)
- [Nodes](#nodes)
- [Response Leads](#response)

---
> **Event** represents each lead's action which send to Giga AI. You can response many times per lead message. For example, if lead text: "hello", then you can response "hi!", then response "how can I help you today?". For each a group of `event - responses` we called **Node**.

<a name="types-of-event"></a>
## Types of Event

- **Text** When leads send text to Giga AI.
- **Postback** When leads tap on any payload button or Quick Replies.
- **Attachment** When leads send attachment message (files, audios, videos, location)
- **Intended** When leads responsed to intended action.
- **Default** When no nodes defined for the event


<a name="nodes"></a>
## Nodes
As mentioned above, **Node** is an event with a set of responses. So basically, Bot is constituted by Nodes. For example:

```
// This is a Node

// People text is an action
People text: 'Do you like watching movie?'

// Bot answers are responses
Bot answers: 'Yes. The Walking Dead for sure.'
Bot answers: 'And you?'
```

<a name="response"></a>
## Response Leads
To response leads, we'll create Nodes, both [Bot Buider](bot-builder) and [Giga AI API](api) bring convenience ways to do that.