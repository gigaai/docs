# Generic
---

Unlike Button Groups which contains only text and buttons. Generic template is a horizontal scrollable carousel of 1-10 items. Each item can contains Image, Title, Subtitle, and 1-3 buttons which bring more visualize information for people.
![Generic Template](/images/generic-template.png)

```
// Answer `Show me your new product` question with a button
$bot->answers('Show me your new product', [
    // A generic bubble
    [
        "title"     => "Lamborghini",
        "image_url" => "http://pictures.topspeed.com/IMG/crop/201603/2016-lamborghini-centenar-5_800x0w.jpg",
        "subtitle"  => "Amazing speed",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "https://lamborghini.com",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_LAMBORGHINI_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ],

    // Another generic bubble
    [
        "title"     => "Rolls Royce",
        "image_url" => "http://static.robbreport.com/sites/default/files/images/articles/2015Sep/1642581//rolls-royce-dawn-02.jpg",
        "subtitle"  => "Most Luxury Car",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "https://www.rolls-roycemotorcars.com/en-GB/home.html",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_ROLLSROYCE_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ],

    // Yet another generic bubble
    [
        "title"     => "Ferrari",
        "image_url" => "https://cdn1.vox-cdn.com/thumbor/-pG8Dcb_qtRf6te3ug12FHhqUDs=/1020x0/cdn0.vox-cdn.com/uploads/chorus_asset/file/4156848/Ferrari_F12tdf_3low.0.jpg",
        "subtitle"  => "I like the horse",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "http://www.ferrari.com/en_en/",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_FERRARI_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ]
]);
```

**Fields:**

The whole generic should be in a nested array. Each item is an array.

- ***title*** (required): Item title
- ***image_url***: Item thumbnail
- ***subtitle***: Item subtitle
- ***buttons***: A group of button, follows the [Buttons](/docs/api/buttons) documentation.