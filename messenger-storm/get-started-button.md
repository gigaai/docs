# Get Started Button
- [Creating Get Started Button](#creating-get-started-button)
- [Handling Get Started Button](#handling-get-started-button)

---
Your Messenger's welcome screen can display a Get Started button. When this button is tapped, our bot will:
 
- Pull lead data and store to CRM 
- Trigger `GIGA_GET_STARTED_PAYLOAD` payload so you can send any message to your lead. 
    - You can then present a personalized message to greet the user or present buttons to prompt him or her to take an action.
    - Adding a "Get Started" button resolves the issue of users not knowing what to write to break the ice with your bot and, many developers find, increases conversions.
    
![Get Started Button](/images/get-started-button.png)

<a name="creating-get-started-button"></a>
## Creating Get Started Button
After you added a Page, Storm automatically creates Get Started button for you so you don't have to.

<a name="handling-get-started-button"></a>
## Handling Get Started Button
After people tapped Get Started button, you'll want to send a custom message. In order to handle Get Started button. You'll need to handle `GIGA_GET_STARTED_PAYLOAD` payload.

Storm has already handled that by default, you can go to **Bot Builder**, find the `GIGA_GET_STARTED_PAYLOAD` node and edit it.