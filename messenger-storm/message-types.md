# Message Types
---
Giga supports sending almost types of messages which Messenger provided. You can send **Text**, **Images**, **Audio**, **Videos**, **Files**, or **Structured Messages** which have several templates.

## Message Types

### Text and Image Messages
You can send text and image messages in your conversation.
![Text and Image](https://scontent-hkg3-1.xx.fbcdn.net/t39.2178-6/12532937_1707565839531937_1916590448_n.png)

### Audio


### Video


### File


### Structured Messages (Button, Generic and Receipt)
Structured Messages support multiple templates to enable different kinds of use cases. The Button and Generic Template can render buttons that open a URL or make a back-end call to your webhook. The Receipt Template can be used to send a receipt.
Response with image.
![Structured Message](https://scontent-hkg3-1.xx.fbcdn.net/t39.2178-6/12679454_228093174215421_635988637_n.png)

The Generic Template can supports multiple bubbles in one message and renders them as a horizontal list. (Below is an example with 2 bubbles.)
![Generic Bubble](https://scontent-hkg3-1.xx.fbcdn.net/t39.2178-6/12995563_1711733995711442_1886079481_n.png)

---

## Message Types Reference

### Text
Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`content` | Text content | String | Y

### Image

Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`url` | URL of Image | String | Y

### Button
Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`text` | Text that appear in the main body | String | Y
`buttons` | Set of buttons that appear as call-to-actions | Array | N
	-> `type` | `web_url` or `postback` | String | Y
	-> `title` | Button title | String | Y
	-> `url` | For web_url buttons, this URL is opened in a mobile browser when the button is tapped | String | Y, if type is `web_url`
	-> `payload` | For postback buttons, this data will be sent back to you via webhook | String | Y, if type is `postback`


### Generic
Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`elements` | Data for each bubble in message | Array | Y
	-> `title` | Bubble title | String | Y
	-> `subtitle` | Button subtitle | String | N
	-> `image_url` | Bubble image | String | N
	-> `item_url` | URL that is opened when bubble is tpped | String | N
	-> `buttons` | Set of buttons that appear as call-to-actions and have same syntax with Button section above | Array | N

### Receipt
Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`recipient_name` | Recipient's Name | String | Y
`order_number` | Order number | String | Y, Must be unique
`currency` | Currency for order | String | Y
`payment_method` | Payment method details. This can be a custom string. Ex: 'Visa 1234' | String | Y
`timestamp` | Timestamp of order | String | N
`order_url` | URL of order | String | N
`elements` | Items in order | Array | Y
	-> `title` | Title of item | String | Y
	-> `subtitle` | Subtitle of item | String | N
	-> `quantity` | Quantity of item | Number | N
	-> `price` | Item price | Number | N
	-> `currency` | Currency of price | String | N
	-> `image_url` | Image URL of item | String | N
`address` | Shipping address | Object | N
	-> `street_1` | Street Address, line 1 | String | Y, if `address` is set
	-> `street_2` | Street Address, line 2 | String | N
	-> `city` | City | String | Y, if `address` is set
	-> `postal_code` | Postal code | String | Y, if `address` is set
	-> `state` | State abbrevation | String | Y, if `address` is set
	-> `country` | Two-letter country abbreviation | String | Y, if `address` is set
`summary` | Payment summary | Object | N
	-> `subtotal` | Subtotal | Number | N
	-> `shipping_cost` | Cost of shipping | Number | N
	-> `total_tax` | Total tax | Number | N
	-> `total_cost` | Total cost | Number | Y
`adjustments` | Payment adjustments | Array | N
	-> `name` | Name of adjustment | String | N
	-> `amount` | Adjusted amount | Number | N
	
