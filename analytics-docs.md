App Center Analytics helps you understand user behavior and customer engagement to improve your app. The SDK automatically captures session count and device properties like model, OS version, etc. You can define your own custom events to measure things that matter to you. All the information captured is available in the App Center portal for you to analyze the data.

Please follow the [Get started_TODO]() section if you haven't set up the SDK in your application yet.

## Session and device information

Once you add App Center Analytics to your app and the SDK is started, it will automatically track sessions and device properties like OS Version, model, etc. You don’t need to write any additional code.

## Custom events

You can track your own custom events with up to five properties to know what's happening in your app, understand user actions, and see the aggregates in the App Center portal.

Once you have started the SDK, use the `trackEvent` method to track your events with properties. You can send **up to 200 distinct event names**. Also, there is a maximum limit of 256 characters per event name and 64 characters per event property name and event property value.

```js
var success = function() {
    console.log("event tracked");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.trackEvent('Video clicked', { Category: 'Music', FileName: 'favorite.avi' }, success, error);
```

This function uses third parameter as success callback which returns an empty string and fourth parameter as error callback which returns the error.

Properties for events are entirely optional. If you just want to track an event, use this sample instead:

```js
var success = function() {
    console.log("event tracked");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.trackEvent('Video clicked', success, error);
```

## Enable or disable App Center Analytics at runtime

You can enable and disable App Center Analytics at runtime. If you disable it, the SDK will not collect any more analytics information for the app.

```js
var success = function() {
    console.log("analytics disabled");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.setEnabled(false, success, error);
```

This function uses second parameter as success callback which returns an empty string and third parameter as error callback which returns the error.
To enable App Center Analytics again, use the same API but pass true as a parameter.

```js
var success = function() {
    console.log("analytics enabled");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.setEnabled(true, success, error);
```

## Check if App Center Analytics is enabled

You can also check if App Center Analytics is enabled or not.

```js
var success = function(result) {
    console.log("analytics " + (result) ? "enabled" : "disabled");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.isEnabled(success, error);
```

This function uses first parameter as success callback which returns a `boolean` and second parameter as error callback which returns the error.

## Wait for JS to enable App Center Analytics

In some cases, an application may want to ask users whether they want to share analytics information. In that case, you should change preference `APPCENTER_ANALYTICS_ENABLE_IN_JS` to `true` in your `config.xml`

```xml
<preference name="APPCENTER_ANALYTICS_ENABLE_IN_JS" value="true" />
```

This means that for any information to be sent to App Center (even basic session information), the developer must first enable App Center Analytics inside the app by adding the following line to their code.


```js
var success = function() {
    console.log("analytics disabled");
}

var error = function(error) {
    console.error(error);
}
AppCenter.Analytics.setEnabled(true, success, error);
```


