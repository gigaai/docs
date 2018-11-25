# Events & Nodes
- [Types of Event](#types-of-event)
- [Nodes](#nodes)
- [Response Leads](#response)

---
> **Event** represents each lead's action which send to Giga. You can response many times per lead message. For example, if lead text: "hello", then you can response "hi!", then response "how can I help you today?". For each a group of `event - responses` we called **Node**.

<a name="types-of-event"></a>
## Types of Event
Text
: When leads send text to Giga.

Postback
: When leads tap on any payload button or Quick Replies.

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
To response leads, we'll create Nodes, [Giga API](api) brings a convenience way to do that.