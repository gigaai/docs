# Multiple Messages

- [Multiple Nodes](#multiple-nodes)

---
In the [Sending Text](/docs/api/text) guide, we've know that in order to send multiple messages. Just put each message as element in an array, like so:

```
$bot->answers('hi', [
    'Hi [first_name]!',
    'Do you want to buy some meth?'
]);
```

However, it's not only works with text but also works with all message types. Let's try with a Generic.

```
$bot->answers('buy meth', [

    // Bot send a text message
    'Here are our available, free ship meth',

    // Then send a carousel
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
]);
```

<a name="multiple-nodes"></a>
## Multiple Nodes
Sometimes, you don't want to keep writing `$bot->answers()` each time you create a node, you can define in a nested array like so:

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