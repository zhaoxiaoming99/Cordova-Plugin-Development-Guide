# CordovaPluginTemplate
This is a guide to show how to quick create a new cordova plugin.

Also create a host cordova app to use the new plugin, you can use this host app to test the cordova plugin.



## Guide
https://gist.github.com/zhaoxiaoming99/4e65901818d77845c10a0a4a7d29d279


## Template
https://github.com/driftyco/cordova-plugin-template


## Quick Steps

0. Clone or download the repo:

```bash
$ git clone git@github.com:driftyco/cordova-plugin-template.git
```

You can also download the cordova-plugin-template to your local device manually.
https://github.com/zhaoxiaoming99/Cordova-Plugin-Template/blob/master/cordova-plugin-template-master.zip


1. Create your app

```bash
$ cordova create hostApp hostApp hostApp
```


2. Add platforms

```bash
$ cd hostApp
$ cordova platform add ios
```


3. Install and Link your Plugin

```bash
$ cordova plugin add --link ~/path/to/plugin
```

With the `--link` flag, Cordova creates a symbolic link to our plugin so we can update the plugin locally and rebuild without having to copy anything.

Note: to remove the plugin, use the symbolic name of the plugin instead:

```bash
$ cordova plugin rm my-cordova-plugin
```

4. Testing process

When our plugin is linked, we can make modifications to the native code in our plugin and rebuild our app immediately. If we make modifications to the JavaScript portion of our plugin, we need to reinstall the plugin (as far as I know, I am trying to find a way around this).

```bash
$ cordova plugin rm my-cordova-plugin
$ cordova plugin add --link ~/path/to/plugin
```

5. Building our plugin

Now you can plug-in you iPhone, then install and test the plugin.

## Best practice

### call js function inside the native code
general usage
```Objective-C
NSString *js = [NSString stringWithFormat:@"cordova.fireDocumentEvent('mipush.%@',%@)", type, json];
[SharedMiPushPlugin.commandDelegate evalJs:js];
```
maybe you can trigger a event 
```Objective-C
[self.commandDelegate evalJs:@"cordova.fireDocumentEvent('active');"];
```
