# Advanced Examples

###### This folder contains alternative examples for logging data to Google Sheets. This assusems you have followed the instructions for the main tutorial and are familiar with the process of updating the ESP8266 code.

### Log data on button press

This example will log data to Google Sheets when a button is pressed.

1. Wire a button to read HIGH when the button is pressed:

   https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button
  
2. Follow the instructions for the main tutorial, but use the code from the "ESP8266-example_button-press.cpp" example instead.
3. Data will be published to Google Sheets when the button is pressed.

*Code explanation:*

If data is not being sent to Google Sheets on a regular interval but rather on an event trigger (such as only publishing data when a button is pressed), occasionally the first attempt to send data will fail. Therefore, it is required to immediately try again if the first attempt fails. 

When the button is pressed (pin D1 reads high), the data_published variable is set to false, and the  error_count variable is set to zero. An attempt is then made to publish data to Google Sheets inside of the while loop. If successful, data_published is set to true and it exits the while loop. If sending data fails, data_published remains false and error_count is increased by 1, then a second attempt to publish is made. It will attempt to publish up to 3 times (while data_published is false and error_count is less than 3). However, I have found that it always works on the second attempt (unless there is something else wrong such as WiFi/router issues, Google servers temporarily down, etc).
  

### Send data from Goole Sheets to the ESP8266

(example code coming soon)
