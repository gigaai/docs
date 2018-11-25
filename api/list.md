# List
---
The List Template is a template that allows you to present a set of items vertically. It can be rendered in two different ways.

The first way renders the first item with a cover image with text overlaid. This is good to making the first item appear prominently above the other items.

![List Template](/images/list-template.png)

The second way renders each item identically and is useful for presenting a list of items where no item is shown prominently.

![List Template Compact](/images/list-template-compact.png)


Each item may render a button which can be used as a call-to-action. You can also provide a URL to be opened when an item is tapped.

Each list template message can also have up to 1 global button which will be rendered below the item list.

**Usage**
The list template can be sent with a call to the Send API with a new template_type list.

The first item style is controlled by a new field called `top_element_style`. The value can be `large` or `compact`. To send a list view as a plain list (with no cover item), set the `top_element_style` to compact; otherwise, the first element will be rendered as the cover item and the `image_url` is required for the first element.

Each element also supports a `default_action`. Using this, you can enable people to open a URL when the row of the list item is tapped.

Please take note of the following limitations:

1. You may send at least 2 elements and at most 4 elements.
1. Adding a button to each element is optional. You may only have up to 1 button per element.
1. You may have up to 1 global button.

**Example**

A List with Cover:
```
'elements' =>  [
    [
        'title' =>  'Classic T-Shirt Collection',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/collection.png',
        'subtitle' =>  'See all our colors',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/shop_collection'
        ],
        'buttons' =>  [
            [
                'title' =>  'View',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/collection'
            ]
        ]
    ],
    [
        'title' =>  'Classic White T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/white-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=100',
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=100'              
            ]
        ]
    ],
    [
        'title' =>  'Classic Blue T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/blue-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=101'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=101'                     
            ]
        ]                
    ],
    [
        'title' =>  'Classic Black T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/black-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=102'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=102'                   
            ]
        ]                
    ]
],
'buttons' =>  [
    [
        'title' =>  'View More',
        'type' =>  'postback',
        'payload' =>  'payload'
    ]
]
```

Without Cover:
```
'top_element_style' => 'compact',
'elements' =>  [
    [
        'title' =>  'Classic T-Shirt Collection',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/collection.png',
        'subtitle' =>  'See all our colors',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/shop_collection'
        ],
        'buttons' =>  [
            [
                'title' =>  'View',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/collection'
            ]
        ]
    ],
    [
        'title' =>  'Classic White T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/white-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=100',
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=100'              
            ]
        ]
    ],
    [
        'title' =>  'Classic Blue T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/blue-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=101'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=101'                     
            ]
        ]                
    ],
    [
        'title' =>  'Classic Black T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/black-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=102'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=102'                   
            ]
        ]                
    ]
],
'buttons' =>  [
    [
        'title' =>  'View More',
        'type' =>  'postback',
        'payload' =>  'payload'
    ]
]
```