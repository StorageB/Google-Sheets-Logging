# Log data from an ESP8266 to Google Sheets

Below are step by step instructions to begin logging data using an ESP8266 module without the need for a third party service. This will publish random number values, so no additional hardware or sensors are required for the script to run. 

<br>

## Instructions for Google Sheets

1. Create new Google Sheets document, and give it a name.

2. Type the following text into each of the following cells:

   - Cell A1: `Date`
   - Cell B1: `Time`
   - Cell C1: `value0`
   - Cell D1: `value1`
   - Cell E1: `value2`
   <br>

   ![Selection_004](https://user-images.githubusercontent.com/44729718/115277764-46881380-a10a-11eb-9be4-b6fbe7ea7091.png)

   
3. Get the Spreadsheet ID from the URL.

      For example, if the URL is:
   
         https://docs.google.com/spreadsheets/d/1sqp9hIM5VvDGEf8i9H-W1Z72lm0O5-ZxC16sMMS-cgo/edit#gid=0

      Then the Spreadsheet ID is:
   
         1sqp9hIM5VvDGEf8i9H-W1Z72lm0O5-ZxC16sMMS-cgo
      
      ![Selection_006-3](https://user-images.githubusercontent.com/44729718/115287377-d1bad680-a115-11eb-8730-4c6ae00184a7.png)


4. From the Google Sheets menu, go to `Extensions > Apps Script`

5. Delete all of the default text in the script editor, and paste the GoogleScripts-example.gs code.

6. Update the Spreadsheet ID (line 9) with the ID obtained in step 3, and click `Save`.

   *Note:  The Spreadsheet ID must be contained in single quotation marks as shown in the example code, and **the script must be saved before continuing** to the next step.*
   
8. Click the blue `Deploy` button at the top right of the page, and select `New Deployment`. 
 
   Click the `gear` icon next to Select Type, and select  `Web App` and modify the following:

   - Enter a Description (optional)
   - Execute as: `Me`
   - Who has access: `Anyone` *(note: do not select `Anyone with a Google Account` - you must scroll down to the bottom to find `Anyone`)*
   
   Click `Deploy` 
   
9. Click `Authorize access` then select your Google account.
   
   On the "Google hasn't verified this app" screen, select `Advanced` > `Go to Untitled project (unsafe)` > `Allow`

   Copy and save the `Deployment ID` for use in the ESP8266 code, and click `Done`.

10. From the script editor, click `Save` and then `Run`. 

   *Note:  Nothing will happen when you click run but you must do that once before continuing.*
 


   

## Instructions for ESP8266

1. In the Arduino IDE, paste the "ESP8266-example.cpp" code into a blank sketch. Overwrite any existing code that was there.

2. Update the following info:

    - Add your Wifi network name
    - Add your Wifi password
    - Replace the Google Script Deployment ID with the ID obtained in step 8 above
    
    *Note:  The Deployment ID must be contained in quotation marks as shown in the example code. The Deployment ID can also be found by clicking `Deploy > Manage Deployments`.*

3. Install the HTTPSRedirect library from here:

    https://github.com/electronicsguy/HTTPSRedirect

    - Click on the green "code" button and "Download ZIP"
    - Unzip the file and move the HTTPSRedirect folder to your library directory
      
      *Note: For Arduino IDE 2.0 and above, the library directory is a subfolder named "libraries" at the path shown under File > Preferences > Sketchbook location. Create the "libraries" folder if it does not already exist (do not capitalize the L in the "libraries" folder name)*
    
4. Delete the config.cpp file from the HTTPSRedirect folder.

   *Note: It must be deleted, not just renamed as it may cause errors when compiling the sketch.*

5. Upload code to your ESP8266 module and watch data get published to your sheet!

     
## Important Note

When making changes to the Google Scripts code, you will need to click `Save` then `Deploy > New deployment` for any new changes to take effect. You will be given a new Deployment ID that you will have to update in the ESP8266 code each time (each new deployment is given a new Deployment ID).



## Troubleshooting

1. If you get a "Something went wrong. Please try again." error message from Google during step 9 when trying to authorize access, try using the Google Chorme browser for this step. I have found that Google has blocked access from some other browsers.
2. If you get an error when compiling, go to the HTTPSRedirect library folder and verify that you have deleted the "config.cpp" file. Note that the network ID, password, host, and Google Script Deployment ID are defined in the main ESP8266 example code and therefore this file is not required and may cause errors for some compilers. 
3. If you are unable to get this working for your existing project, it is recommended that you start with a brand new empty project and spreadsheet and then follow the above instructions. Once you have the example above working, then make the changes to implement your own custom code.
4. For applications where data is not sent on a regular interval but rather on an event trigger (such as only sending data when a button is pressed), occasionally the first attempt to send data will fail. Therefore, the code must be modified to send the data again if the first attempt fails. See the example under the "Advanced" folder for additional information.
5. This tutorial does not work for an ESP32 device.


#### I hope you found this tutorial helpful!

<a href="https://www.buymeacoffee.com/StorageB" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 36px !important;width: 131px !important;" ></a>
