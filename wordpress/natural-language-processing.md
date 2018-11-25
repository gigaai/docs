# Natural Language Processing (NLP)

***

It isn't a real AI without NLP. We're currently support Facebook NLP at the moment and will support Microsoft Cognitive Service in the future so the bot can think, listen, and watch.

## Installation

To use NLP, you must first install NLP for your bot:

1. Go to Facebook app dashboard, under PRODUCTS section, select Messenger page.
1. Under Built-In NLP section, select the page you want to run NLP.
1. Switch the switcher to **On**
1. In **Language Model** select the language which is best applied to your bot.
1. In **Advanced Settings** select options which are best applied to your bot:
    - Verbose: A flag to get auxiliary information about entities, like the location within the sentence.
    - N-Best: The number of n-best trait entities you want to get back. The Default is 1, and the maximum is 8.

![Setup Facebook NLP](/images/docs-facebook-nlp.png)

## Using NLP

### Responding NLP Entities
When a message sent to your bot, it will returns parsed nlp data with entities. For example, when people say **"Hello"**, it will sends the entity `greetings` with confident > 0.98 (+98%). That means, the "hello" message is a greeting message, that also means, you can create a node to handle all greetings messages.

To response an entity, enter hash (#) sign before entity name in bot builder Pattern, or first param in `$bot->answers()` method.

For example:
```
$bot->answers('#greetings', 'Hi [first_name]');
```

This will send **"Hi John"** for example, when user send hi, hello, howdy, or other greeting messages. 

### Extracting NLP Values
When received a message, Giga AI will parse nlp data with all entities ordered by their confidences, from high to low.

In orderto get NLP values, you can either use `[nlp]` shortcode or `$bot->nlp()` method.