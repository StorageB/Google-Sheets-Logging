# Advanced Examples

###### This folder contains alternative examples for logging data to Google Sheets. This assusems you have followed the instructions for the main tutorial and are able to succussfully send data to Google Sheets.

### Log data on button press

This example will log data to Google Sheets when a button is pressed.

1. Wire a push button so that pin D1 will read HIGH when the button is pressed.

   Example wiring diagram:    https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button
  
2. Follow the instructions for the main tutorial, but use the code from the "ESP8266-example_button-press.cpp" file for the ESP8266 instead.
3. Data will be published to Google Sheets when the button is pressed.

*Notes:*

If data is not being sent to Google Sheets on a regular interval but rather on an event trigger (such as only sending data when a button is pressed), occasionally the first attempt to send data will fail. Therefore, the example code is set up to automatically try again. I have found that data gets sent on the second attempt (although the code will attempt up to 3 times) unless something else is wrong such as Google servers temporarily down, etc. 

In the example code when the button is pressed (pin D1 reads high), an attempt to send data is made. If it fails, it will wait a couple seconds and try again. The data_published and error_count variables keep track whether or not data has been send successfully to Google Sheets, and are reset each time the button is pressed.
  

### Send data from Goole Sheets to the ESP8266

(example code coming soon)
