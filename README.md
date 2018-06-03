# VGS IOT sensor network demo in pure C (Espressif IDF c99)

#### Poll a senor and leverage VGS Proxy/Vault platfom to to protect sensor data
----

Uses APIs from [esp-tls](https://github.com/espressif/esp-idf/tree/master/components/esp-tls) component to make a very simple tcp sockets based HTTPS 1.1 POST over tls1.2, including verifying the server TLS certificate. You can also harden the TLS Protocols and Ciphers a bit using `$make menuconfig` make option
 
- This demo will use an Espressif [ESP* format device](https://www.espressif.com) with [Espressif IDF](https://github.com/espressif/esp-idf) C development environment.   
    esp8266, esp32, etc

- The demo shows how easy it is to safely, securely operate on sensor network data within the constraints of a low power - limited compute device which may need near wire speed processing at the backend

**Solution Architecture:**     
![esp32x2.jpg](/docs/flow.png)   


**Rest API Call - Unprotected**

```bash
Headers
host api.gordonyoung.us:443
Accept-Encoding identity;q=1,chunked;q=0.1,*;q=0
Content-type application/json
User-Agent ESP8266HTTPClient
...
Body
{
  "SensorID": "E25C67AF-CA37-4996-8C7A-3375499995FB",
  "GPS": "334484N1120740WT1526864344",
  "TEMP": "48.2C"
}
```

**Configure dashboard routes:**     
![esp32x2.jpg](/docs/routes.png)    

**Redacted API message:**    
Data is protected for middle tier and Uptream:   

```bash    
Headers
Accept-Encoding identity;q=1,chunked;q=0.1,*;q=0
Content-type application/json
User-Agent ESP8266HTTPClient
...
host api.gordonyoung.us:443
content-length 145
Body
{
  "SensorID": "tok_sandbox_5BkDXb68SeBNZBeYagAeMa",
  "GPS": "tok_sandbox_5TkDXb68SeBNZBeYagBWME",
  "TEMP": "tok_sandbox_51y7ZoSyeKSAiZY8uGFUfW"
}
```    

**Device Display:**    
![esp32x2.jpg](/docs/espboard.jpeg)    

~Gordon
 