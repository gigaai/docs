# Answers Method
---
The answers method can takes up to 3 arguments.

### $bot->answers(array $requestResponsesPairs)
If you put one argument, it defines [Multiple Nodes](/docs/api/multiple-messages#multiple-nodes)

**Fields**
- `$requestResponsesPairs`: The associated array of `'request' => 'response'` style

**Example**

```
$bot->answers([
    'hi' => [
        'Hi [first_name]!',
        'Do you want to buy some meth?'
    ],
    'buy meth' => [
        'Here are our available, free ship meth',
        [
            [
                'title'     => 'Blue Meth',
                'subtitle'  => 'Tight tight tight',
                'image_url' => 'https://blue-meth.com',
                'buttons' => [
                    [
                        'title' => 'View',
                        'type' => 'web_url',
                        'url' => 'https://amc.com'
                    ]
                ]
            ]
        ]
    ]
]);
```

### $bot->answers(string $request, Mixed $responses, Array $nodeProperties)
If the method have two arguments, then the first is the request and the second are the responses.

**Fields**
- ***$request*** String: Can be people text, button payload, intended action, attachment.
- ***$responses*** String/Array/Callable: Can be `String` for text message, `array` for other template or list of messages, and `Callable` for callback function.
- ***$nodeProperties*** *(Optional)*: Other properties for this node, this will insert to column in `bot_nodes` table. For example: `['notification_type' => 'SILENT_PUSH']`
