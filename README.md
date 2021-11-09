Pushover-Android-Java
--------

[![Build Status](https://travis-ci.org/sps/pushover4j.png?branch=master)](https://travis-ci.org/sps/pushover4j)
[![Coverage Status](https://coveralls.io/repos/sps/pushover4j/badge.png?branch=master)](https://coveralls.io/r/sps/pushover4j?branch=master)

A simple java client for [pushover](https://pushover.net/) notification service. Example:
```
PushoverClient client = new PushoverRestClient();        

client.pushMessage(PushoverMessage.builderWithApiToken("MY_APP_API_TOKEN")
        .setUserId("USER_ID_TOKEN")
        .setMessage("testing!")
        .build());
```
Just that fast. Now the message can be customized with much more control as seen below. We also capture the result from the API call and can reference that for success or error message logging:
```
// push a message with optional fields
//(note we are reusing the client from the first example here)
Status result = client.pushMessage(PushoverMessage.builderWithApiToken("MY_APP_API_TOKEN")
      .setUserId("USER_ID_TOKEN")
      .setMessage("Welcome to pushover4j!")
      .setDevice("<your device name>")
      .setPriority(MessagePriority.HIGH) // LOWEST,QUIET,NORMAL,HIGH,EMERGENCY
      .setTitle("Testing")
      .setUrl("https://github.com/sps/pushover4j")
      .setTitleForURL("pushover4j github repo")
      .setSound("magic")
      .build());
System.out.println(String.format("status: %d, request id: %s", result.getStatus(), result.getRequestId()));
```
And you can keep up to date with the latest in available sounds with a quick call as well.
```
// get and print out the list of available sounds:
for (PushOverSound sound : client.getSounds() ) {
    System.out.println(String.format("name: %s, id: %s", sound.getName(), sound.getId()));
}              
```

Just search the maven repo for ` pushover-client ` or add the following to your POM
```
<dependency>
  implementation 'com.github.sps.pushover.net:pushover-client:1.5.1'
</dependency>
```
