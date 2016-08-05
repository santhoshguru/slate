---
title: HappyFox Chat - API Reference

language_tabs:
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

> All API methods should be called on the onLoad event

```javascript
HFCHAT_CONFIG.onload = function() {

 var HappyFoxChat = this;

};
```

<p class="top-spacing">HappyFox Chat's JavaScript API provides you more control over the chat widget. You can customize the widget behavior programmatically.</p>

<p > All API methods should be called only after the script is loaded.</p>

<aside class="notice">
  You can, add your HappyFox Chat api related code with in the `onload` function
</aside>


# Set Visitor Info

> Syntax - setVisitorInfo

```javascript
HappyFoxChat.setVisitorInfo(<visitorInfoObject>, <callback>);
```

<blockquote>
 <p>&lt;visitorInfo[Object]&gt; should have two mandatory properties name and email.</p>
</blockquote>


> Example

```javascript
HappyFoxChat.setVisitorInfo({
 'name': 'Bob',
 'email': 'bubblybob@gmail.com'
}, function(err, resp) {
 if(err) {
  console.error('Failed to set visitor details. Error:', err);
 } else {
  console.log('Added visitor details:', resp);
 }
});
```
<p class="top-spacing">You can send in your signed-in user's name and email by simply calling the setVisitorInfo method to pass those details. This is will skip the pre-chat form for the users.</p>

<p>Mandatory properties that needs to be set:</p>

- name
- email

# Get Visitor Info

> Syntax - getVisitorInfo

```javascript
HappyFoxChat.getVisitorInfo(<callback>);
```

> Example

```javascript
HappyFoxChat.getVisitorInfo(function(err, resp) {
 if(err) {
  console.error('Failed to set visitor details. Error:', err);
 } else {
  console.log('Got visitor info:', resp);
 }
});
```

<p class="top-spacing">Properties returned by this method:</p>

- name
- email

# Unset Visitor

> Syntax - unsetVisitor

```javascript
HappyFoxChat.unsetVisitor(<callback>);
```

> Example

```javascript
HappyFoxChat.unsetVisitor(function(err) {
 if (err) {
  console.error('Failed to reset the visitor. Error:', err);
 } else {
  console.log('Visitor reset successful');  
 }
});
```

<p class="top-spacing">If you want to clear or unset the visitor details when your visitor logs off, you can call the method unsetVisitor API to clear the pre-filled data.</p>

<aside class="notice">
  This will force the widget to forget the visitor. When your visitor wants to chat with you, he/she has to fill the pre-chat form with  name and email details.
</aside>

# Set Custom Fields

> Syntax - setCustomFields

```javascript
HappyFoxChat.setCustomFields(<customFieldObject>, <callback>);
```

<blockquote>
 <p>&lt;customField[Object]&gt; should have properties <a href="https://support.happyfoxchat.com/kb/article/420-how-to-send-more-info-about-visitors-to-happyfox-chat" target="_blank">defined inside HappyFox Chat</a>.
</blockquote>

> Example

```javascript
HappyFoxChat.setCustomFields({
 'Account Number': '1234567890',
 'Branch': 'CA',
 'Type': 'Free'
}, function(err, resp) {
 if(err) {
  console.error('Failed to add given properties to custom fields. Error:', err);
 } else {
  console.log('Added custom field properties:', resp);
 }
});
```

> Syntax - unsetCustomFields

```javascript
HappyFoxChat.unsetCustomFields(["<customFieldName>", "<customFieldName>", ... ], <callback>);
```

```javascript
HappyFoxChat.unsetCustomFields({
 'Account Number',
 'Branch'
}, function(err, resp) {
 /**
  * err  -> Incase of failure this will have error object
  */
 if(err) {
  console.error('Failed to unset given custom field values. Error:', err);
 } else {
  console.log('Successfully unset custom fields');
 }
});
```

<p class="top-spacing">The <a href="https://support.happyfoxchat.com/kb/article/483-customizing-chat-widget-using-javascript-api?_ga=1.146945136.657137493.1436768824" target="_blank">custom field</a> is a way to pass more data about visitors from your website to HappyFox Chat without any action needed from them. You can send details using the API mentioned below.</p>

# Get Custom Field

> To Get Custom Field, use this code

```javascript
HappyFoxChat.getCustomField("<customFieldName>", <callback>);
```

> Example

```javascript
HappyFoxChat.getCustomField("Type", function (err, value) {
 /**
  * err  -> Incase of failure this will have error object
  */
 if(err) {
  console.error('Failed to unset given custom field values. Error:', err);
 } else {
  console.log('Successfully got custom field value. Value:', value);
 }
});
```

# Add Custom Styles

> To Add Custom Styles, use this code

```javascript
HappyFoxChat.addCustomStyles(<customStyle>);
```

> Example

```javascript
HappyFoxChat.addCustomStyles('.hfc-title-text { color: #0000FF !important; } .hfc-title-bar { background-color: #00FF00 !important; }', function(err) {
 /**
  * err  -> Incase of failure this will have error object
  */
  if (err) {
    console.error('Failed to add custom styles. Error:', err);
  } else {
    console.log('Added custom styles');
  }
});
```

<p class="top-spacing">To make CSS customization or to change the style of the widget, use the below API.</p>

# Add Custom CSS File

> To Add Custom Styles, use this code

```javascript
HappyFoxChat.addCustomCSSFile(<customCSSFileUrl>);
```

> Example

```javascript
HappyFoxChat.addCustomCSSFile('http://mydomain.com/css/happyfoxchat-custom.css', function(err) {
 /**
  * err  -> Incase of failure this will have error object
  */
 if(err) {
  console.error('Failed to add custom CSS file. Error:', err);
 } else {
  console.log('Added custom CSS file');
 }
});
```

# Expand/Collapse Chatbox

> To Expand Chatbox, use this code

```javascript
HappyFoxChat.expandChatbox(<callback>);
```

> To Collapse Chatbox, use this code

```javascript
HappyFoxChat.collapseChatbox(<callback>);
```

> Example

```javascript
HappyFoxChat.expandChatbox(function(err) {
 /**
  * err  -> Incase of failure this will have error object
  */
 if(err) {
  console.error('Failed to expand chatbox. Error:', err);
 } else {
  console.log('Expanded chatbox');
 }
});
```

# Show/Hide Widget

> To Show Widget, use this code

```javascript
HappyFoxChat.showWidget(<callback>);
```

> To Hide Widget, use this code

```javascript
HappyFoxChat.hideWidget(<callback>);
```

# Show/Hide Badge:

> To Show Badge, use this code

```javascript
HappyFoxChat.showBadge(<callback>);
```

> To Hide Badge, use this code

```javascript
HappyFoxChat.hideBadge(<callback>);
```

# Get Agents Availability

> To Get Agents Availability, use this code

```javascript
HappyFoxChat.getAgentsAvailability(function (err, agentsAvailability) {
  ...
});
```

# Get Visitor State

> Get Visitor State, use this code

```javascript
HappyFoxChat.getVisitorState(function (err, visitorState) {
  ...
  visitorState can be "passive"/"waiting_for_agent"/"chattting"
});
```

# Get Proactive Message

> to Get Proactive Message, use this code

```javascript
HappyFoxChat.getProactiveMessage(function (err, proactiveMessage) {
  ...
});
```

# Get Widget Properties

> to Get Widget Properties, use this code

```javascript
HappyFoxChat.getWidgetProperties(function (err, widgetProperties) {
  ...
});
```

# Events

> Example

```javascript
HappyFoxChat.on('click:badge', function () {
  console.log('Chat with us badge clicked');
});
```

<p class="top-spacing"> You can listen to events via SDK </p>

**Supported Events:**

- `click:badge`
- `start:chat`
- `end:chat`
- `join:agent`
- `leave:agent`
- `change:agents_availability`
- `activate:triggered_chat`
- `received:proactive_message`
- `submitted:rating`
- `change:visitor_state`










