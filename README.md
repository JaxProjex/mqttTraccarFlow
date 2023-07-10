# mqttTraccarFlow
Node-Red Flow to forward MQTT sensor location to Traccar Server. MQTT sensor must be added as a Traccar Client in Devices through the Traccar Server Web GUI.

![traccar flow](/mqttTraccarFlow.png?raw=true "Node Red Flow")

MQTT PUB PAYLOAD EXAMPLE (JSON):

{

    "id": "1234",
    
    "name": "test-1234",
    
    "lat": "20.2020",
    
    "lon": "40.4040"
    
}

-------------------------------------------

MQTT PUB PAYLOAD:

-the "id" key gets used as the UniqueID for Traccar Clients to add devices to Traccar Server. Use this id to input when adding Traccar Devices by UniqueID.

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
