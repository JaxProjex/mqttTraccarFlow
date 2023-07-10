# mqttTraccarFlow
Node-Red Flow to forward MQTT sensor location to Traccar Server. MQTT sensor must be added as a Traccar Client in Devices through the Traccar Server Web GUI.

![traccar flow](/mqttTraccarFlow.png?raw=true "Node Red Flow")

SETUP NODE-RED:

-https://nodered.org/docs/getting-started/

-options include installing node-red on your local PC, a Raspberry Pi or similar single board computer or mini PC, deploying node-red on a cloud server or virtual private server (VPS), Docker Container, or local virtual environment. After installing node-red you should be able to go to the node-red dashboard at http://node-red-ip-address:1880 you may have to open appropriate ports (1880) to allow devices to access the node-red dashboard.

----------------------------------------------

IMPORT .JSON FLOW TO NODE RED:

-in GitHub: click on "mqttTraccarFlow.json" > click on the download icon "Download raw file" > note where the "mqttTraccarFlow.json" file downloaded to, default is in your Downloads folder.

-in Node-Red: click on menu icon (3 horizontal lines top right) > click on "Import" > click on "select a file to import" > go to Downloads folder and click on "mqttTraccarFlow.json" > Upload > Import

ALTERNATIVELY..

-you can just copy the whole "mqttTraccarFlow.json" code from GitHub and paste it into the Node-Red Import Clipboard.

-----------------------------------------------

MQTT PUB PAYLOAD EXAMPLE (JSON):

    {

        "id": "1234",
    
        "name": "test-1234",
    
        "lat": "20.2020",
    
        "lon": "40.4040"
    
    }

-------------------------------------------

MQTT PUB PAYLOAD:

-the "id" key gets used as the Identifier/UniqueID for Traccar Clients to add devices to Traccar Server. Use this id to input when adding Traccar Devices by Identifier/UniqueID.

-the "name" key gets used as the name of the Traccar Client device on the Traccar Server.

-the "lat" and "lon" key is used to plot the latitude and longitude coordinates, however you get the lat and lon of your mqtt device (gps module, network gps, virtual gps, etc.) be sure to pass them seperately as a "lat" and "lon" key.

--------------------------------------------

MQTT IN NODE:

-configure the "mqtt in" node of the necessary subscribed topic and the authentication needed (if necessary).

---------------------------------------------

HTTP PUT NODE:

-the "http put" node needs to be configured for your Traccar Server IP Address. Keep the IP Port number as it specifies the protocol used being sent to Traccar Server.

-----------------------------------------------

ADDING DEVICE TO TRACCAR SERVER:

-login to your Traccar Server UI > Settings > Devices > "+" icon > add name of mqtt device, identifier/UniqueID is the "id" object used that the mqtt device sends in its payload (whatever you have set, it can be any random set of numbers and characters as long as it sends the same string every payload).

-when your mqtt device sends its position payload it should then populate on your traccar server, you can use the example mqtt devices in the flow to test.

-------------------------------------------------

TROUBLESHOOTING / KNOWN ISSUES:

-in the event the Node-Red service explodes and you lose connection to the Node-Red UI and cant reconnect, you may need to restart your Node-Red service

$ sudo service node-red restart

