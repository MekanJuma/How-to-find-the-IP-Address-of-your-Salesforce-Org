# How to find the IP Address of your Salesforce Org

## Overview
Salesforce Orgs often need to identify their public IP address for various integrations and security configurations. This process involves making an outbound HTTP request to an external service that returns the IP address of the requester.

## Step 1: Add Remote Site Setting
1. Log in to your Salesforce Org.
2. Navigate to Setup.
3. In the Quick Find box, search for Remote Site Settings.
4. Select Remote Site Settings, and click on New Remote Site.
5. Enter the following details:
  - Remote Site Name: FindIPAddress
  - Remote Site URL: https://api.ipify.org
  - Ensure Active is checked.
6. Click Save.

## Step 2: Execute Apex Code in Developer Console
1. Open the Developer Console from the gear icon in the upper right corner.
2. Press Ctrl + E to open the Execute Anonymous Window.
3. Copy and paste the following Apex code:
```apex
HttpRequest request = new HttpRequest();
request.setEndpoint('https://api.ipify.org');
request.setMethod('GET');
Http http = new Http();
HttpResponse response = http.send(request);
String responseBody = response.getBody();
System.debug('IP Address: ' + responseBody);
```
4. Click Execute to run the code.
5. Check the Debug Log for the output containing the IP address.

### Output
The IP address of your Salesforce Org will be displayed in the Debug Logs of the Developer Console.
