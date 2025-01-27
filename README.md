# flic2hass
## A Flic SDK utility to publish all of your Flic buttons to Home Assistant via MQTT

Requirements:
* A Flic Hub
* A functional MQTT server
## Basic Steps:

**1. Connect to Flic Hub IDE:**

* Follow along with the beginning of [these instructions](https://hubsdk.flic.io/static/tutorial/) to enable SDK access.
* Go to: <https://hubsdk.flic.io/> and login, your hub should be discovered automatically.

**2. Create `MQTT` module:**

* One in the Web IDE, click "Create Module".
* Give the new module a name. "`MQTT`" is a good option but anything will work.

**3. Insert `main.js` and `mqtt.js`:**

* Copy content from `main.js` in this repo to main.js in the flic IDE.
* Right click the folder in the left pane and select "New File".
* Name the file `mqtt.js` (IT MUST BE NAMED THIS).
* Copy content from `mqtt.js` in this repo to mqtt.js in the flic IDE.

**4. Update variables in `main.js`:**

* Modify `server`, `hatopic`, `authentication` with your details.

   *If your MQTT server does not require authentication:*

* Delete:

     ```javascript
     var username = 'flichub';
     var password = 'xxxxx';
     ```

* Replace:

     ```javascript
     var mqtt = require("./mqtt").create(server,{'username':username,'password':password});
     ```

     With:

     ```javascript
     var mqtt = require("./mqtt").create(server);
     ```

1. Start the module in the IDE by clicking the green play button, and watch the Console output (it's extremely verbose right now)
   
   *If the module didn't start correctly, try powercycling your Flic Hub and reconnect. Verify the Module saved properly and is running.*

2. Once the module has started and you have verified it is working as expected, turn on the "restart after crash" checkbox to ensure the module is always running after any unexpected crash or hub power cycle.
