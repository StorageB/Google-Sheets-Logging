# Advanced Examples

###### This folder contains alternative examples for logging data to Google Sheets. This assusems you have followed the instructions for the main tutorial and are able to succussfully send data to Google Sheets.

### Log data on button press

This example will log data to Google Sheets when a button is pressed.

1. Wire a push button so that pin D1 will read HIGH when the button is pressed.

   Example wiring diagram:    https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button
  
2. Follow the instructions for the main tutorial, but use the code from the "ESP8266-example_button-press.cpp" file for the ESP8266 instead.
3. Data will be published to Google Sheets when the button is pressed.

*Notes:*

If data is not being sent to Google Sheets on a regular interval but rather on an event trigger (such as only sending data when a button is pressed), occasionally the first attempt to send data will fail due to an issue with the way Google Sheets handles the request. The data is sent if a second attempt is made shortly after the first. Therefore, the example code is set up to automatically try again if the first attempt fails. 


### Send data from Google Sheets to the ESP8266

(example code coming soon)
