# wipy-urllib

To be completed, see urequests hereunder

# urequests

First version of urequests for micropython, minor bug-fixes to work with Enabling's Cloud Channels
Based on https://github.com/lucien2k/wipy-urllib

Supports:
 - SSL
 - Cookies
 - Basic Auth
 - Custom HTTP Headers
 - GET, POST, PUT, DELETE, OPTIONS, HEAD
 - JSON payloads (experimental)
 
Use it:
```
import urequests

''' Your cloud-channel is defined here:'''
url = "https://api.enco.io/platform/cloudchannels/1.0.0/cc/861ec263-41e7-4d35-9d6c-3c17889b106c"

''' The payload you defined in your CloudChannel interface, in this case a simple integer called 'sensor':
 {"type":"object","properties":{"Sensor":{"type":"integer"}},"title":"sensor"}'''
payload = {"Sensor": 1}

''' your auth bearer here, Content-Type must be set to 'Application/json' '''
myheaders = {
    "Authorization": "Bearer 38dfbef7900f75cadbae76e33f91363f",
    "Content-Type": "application/json"
    }
    
''' Actual call, returns an URLOpener object '''
response = urequests.urlopen(url, "POST", {}, payload, headers=myheaders)

''' URLOpener attributes '''
response.text
response.headers
response.url
response.status_code
```
Similar interface to http://docs.python-requests.org/en/latest/
