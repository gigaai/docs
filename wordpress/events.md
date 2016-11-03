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

Payload
: When leads tap on any previous button response. Included **Get Started** button, **Persistent Menu**, or **Quick Replies**..

<a name="nodes"></a>
## Nodes
As mentioned above, **Node** is an event with a set of responses. So basically, Bot is constituted by Nodes. For example:

```
// This is a Node

// Lead text
People text: 'Do you like watching movie?'

// Bot answers
Bot answers: 'Yes. The Walking Dead for sure.'
Bot answers: 'And you?'
```

<a name="response"></a>
## Response Leads
To response leads, we'll create Nodes, both [Bot Buider](bot-builder) and [Giga API](api) brings a convenience way to do that.