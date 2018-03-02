# iConDimmer

## Summary: 
The iCon Dimmer uses a mesh protocol to connect multiple devices in multiple locations(zones) to one central hub(icon). Using bluetooth and WiFi technology, we were able to create a mesh network between the icon, and surrounding lights. We offered a real-time solution to controlling the light intensities locally and remotely from both android and ios devices.

* **Tech Involved**: NodeJS MQTT broker and Express for back-end, MongoDB Passport and Mongoose for authentication, Bluetooth GAT Protocol and Bonjour for direct communication, Swift3 and Xcode for IOS, Java and Android Studio for Android.

### Details:
### Phase 1: Connect iCon to internet
* **Goal**: Use local bluetooth to connect to the iCon to transfer WiFi credentials so that the iCon can create its own MQTT Broker and connect to the AWS MQTT Broker.
* **Reasoning** This needs to occur so that the iCon has a persistant socket connection, waiting for the mobile application to send a request.
* **What We Did**: We transferred the username and password to the AWS MQTT broker by HTTP. Once their instance was created, we used Bluetooth GAT to connect to the iCon, transfered over the Wifi Name, SSID, Username, and Password to the iCon, and waited for the iCon to establish its own MQTT broker and connect to the AWS MQTT broker.

### Phase 2: Connect to iCon to Lights
* **Goal**: Create the Mesh links between the iCon and the lights using the zone-link feature of the app.
* **Reasoning** This needs to occur so that the iCon can have full control of the lights.
* **What We Did**: We used MQTT to communicate to the iCon telling it distribute a connectivity signal to which listening lights would attach to. From this point forward, the iCon would have complete control of these lights and would response in real-time to any command the mobile application would send.

### Phase 3: Override System
* **Goal**: Have a backup system in case a light loses connection to iCon or needs a reset.
* **Reasoning** We needed a way to directly connect the mobile app to individual lights for worst case scenerio problems.* * **What We * **What We Did**: We Used Bluetooth GAAT to connect directly to the lights so that we can erase their content, putting them back into their factory setting.
