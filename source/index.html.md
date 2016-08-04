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

<p class="top-spacing">HappyFox Chat's JavaScript API provides you more control over the chat widget. You can customize the widget behavior programmatically.</p>

# Onload

> to listen onload, use this code

```javascript
HFCHAT_CONFIG.onload = function() {

 var HappyFoxChat = this;

};
```

<p class="top-spacing"> All API methods should be called only after the script is loaded.</p>

<aside class="notice">
  You can, add your HappyFox Chat api related code with in the `onload` function
</aside>


# Set Visitor Information

> to set visitor information, use this code

```javascript
HappyFoxChat.setVisitorInfo(<visitorInfoObject>, <callback>);
```

> Example

```javascript
HappyFoxChat.setVisitorInfo({
 'name': 'Bob',
 'email': 'bubblybob@gmail.com'
}, function(err, resp) {
 /**
  * err  -> Incase of failure this will have error object
  * resp -> Passed visitor info object (Here: { 'name': 'Bob', 'email': 'bubblybob@gmail.com' })
  */
 if(err) {
  console.error('Failed to set visitor details. Error:', err);
 } else {
  console.log('Added visitor details:', resp);
 }
});
```

<p class="top-spacing">Available visitor info fields:</p>

- name
- email

# Get Visitor Information

> To get visitor information, use this code

```javascript
HappyFoxChat.getVisitorInfo(<callback>);
```

> Example

```javascript
HappyFoxChat.getVisitorInfo(function(err, resp) {
 /**
  * err  -> Incase of failure this will have error object
  * resp -> Visitor Info object (Example: { 'name': 'Bob', 'email': 'bubblybob@gmail.com' })
  */
 if(err) {
  console.error('Failed to set visitor details. Error:', err);
 } else {
  console.log('Got visitor info:', resp);
 }
});
```

<p class="top-spacing"> Available visitor info fields:</p>

- name
- email

# Unset Visitor

> to unset visitor, use this code

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

<aside class="notice">
  This will force the widget to forget the visitor.
</aside>

# Set Custom Field Value

> To Set Custom Field Value, use this code

```javascript
HappyFoxChat.setCustomFields(<customFieldObject>, <callback>);
```

> Example

```javascript
HappyFoxChat.setCustomFields({
 'Account Number': '1234567890',
 'Branch': 'CA',
 'Type': 'Free'
}, function(err, resp) {
 /**
  * err  -> Incase of failure this will have error object
  * resp -> Passed custom field object (Here: { 'Account Number': '1234567890', 'Branch': 'CA', 'Type': 'Free'})
  */
 if(err) {
  console.error('Failed to add given properties to custom fields. Error:', err);
 } else {
  console.log('Added custom field properties:', resp);
 }
});
```

> To Unset Custom Field Value, use this code

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










