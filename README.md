fcm-rest-api
========

A Node.JS simple interface to Google's Firebase Cloud Messaging (FCM). Supports android, iOS and Web push, including topic messages, and topic subscribe/unsubscribe functionalities.  
Additionally it also keeps the callback behavior for the new firebase messaging service. 

## Installation

Via [npm][1]:

    $ npm install fcm-rest-api

## Usage

There are 3 APIs for FCM Push Functionality:
### FCM REST APIs 
   1. Send Push Message To Android/IOS/Web/Topic
   2. Subscribe Topic For FCM Push
   2. UnSubscribe Topic To Stop FCM Push
   

#### SEND PUSH MESSAGE TO ANDROID/IOS/WEB
```js
    const fcm = require('fcm-rest-api')
    
    var serverKey = require('path/to/privatekey.json') //put the generated private key path here  
	
	var platfrom = 'android/ios/web';//VALID PLATFORMS
	
	var notificationObj: {
		title: 'Title of your push notification', 
		body: 'Body of your push notification', 
		click_action: 'Click Action Url', 
		badge: 'Badge Count'
	};
	
	var additionalObj: {
		key1: 'value1', 
		key2: 'value2' 
	};
    
    fcm.sendPushToTokens(serverKey, tokens, notificationObj, additionalObj, 'android')
	.then(json => {
		resolve(json);
	})
	.catch((err) => {
		reject(err);
	});
```


#### SEND PUSH MESSAGE TO TOPIC
```js
    const fcm = require('fcm-rest-api')
    
    var serverKey = require('path/to/privatekey.json') //put the generated private key path here    
	
	var topic = "topic_name_here";
	
	var notificationObj: {
		title: 'Title of your push notification', 
		body: 'Body of your push notification', 
		click_action: 'Click Action Url', 
		badge: 'Badge Count'
	};
	
	var additionalObj: {
		key1: 'value1', 
		key2: 'value2' 
	};
    
    fcm.sendPushToTopic(serverKey, topic, notificationObj, payloadObj)
	.then(json => {
		resolve(json);
	})
	.catch((err) => {
		reject(err);
	});
```



#### SUBSCRIBE TO TOPIC
```js
    const fcm = require('fcm-rest-api')
    
    var serverKey = require('path/to/privatekey.json') //put the generated private key path here    
	
	var topic = "topic_name_here";
    
    fcm.subscribeToTopic(serverKey, tokens, topic)
	.then(json => {
		resolve(json);
	})
	.catch((err) => {
		reject(err);
	});
```



#### UNSUBSCRIBE FROM TOPIC
```js
    const fcm = require('fcm-rest-api')
    
    var serverKey = require('path/to/privatekey.json') //put the generated private key path here    
	
	var topic = "topic_name_here";
    
    fcm.unSubscribeToTopic(serverKey, tokens, topic)
	.then(json => {
		resolve(json);
	})
	.catch((err) => {
		reject(err);
	});
```

#### UPDATES
	1-> Version 1.0.0 -> Initial Setup
	2-> Version 1.0.1 -> Web Push Click Action issue fixed
	3-> Version 1.0.2 -> Git repo added
