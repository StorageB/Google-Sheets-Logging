# Log data from an ESP8266 to Google Sheets

###### Below are step by step instructions to begin logging data using an ESP8266 module without the need for a third party service. This will publish random number values, so no additional hardware or sensors are required for the script to run. These instructions assume you are familiar with the Arduino IDE and how to upload code to your ESP8266 and install libraries.

#### Instructions for Google Sheets

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


4. From the Google Sheets menu, go to `Tools > Script Editor`
   
   *Note:  Make sure you are using the new Apps Script editor (not the legacy version). The editor will default to the new version, but if you're using the legacy version you'll need switch back by clicking the blue "Use new editor" button at the top of the page.*

5. Delete all of the default text in the script editor, and paste the GoogleScripts-example.gs code.

6. Update the Spreadsheet ID (line 11) with the ID obtained in step 3, and click `Save`.

   *Note:  The Spreadsheet ID must be contained in single quotation marks as shown in the example code, and the script must then be saved before continuing to the next step.*
   
7. Click the blue `Deploy` button at the top right of the page, and select `New Deployment`. 
 
   Click the `gear` icon next to Select Type, and select  `Web App` and modify the following:

   - Enter a Description (optional)
   - Execute as: `Me`
   - Who has access: `Anyone` (*note: do not select `Anyone with a Google Account` - you must scroll down to the bottom to find `Anyone`*)
   
   Click `Deploy` 
   
8. Click `Authorize access`

- select your Google account
- on the "Google hasn't verified this app" screen, select `Advanced` > `Go to project (unsafe)` > `Allow`
- copy and save the Deployment ID for use in the ESP8266 code, and click `Done`.

9. From the script editor, click `Run` (note that nothing will happen if everything has been set up successfully, but it is necessary to run this function manually just one time). 

   

#### Instructions for ESP8266

1. In the Arduino IDE, paste the ESP8266-example.cpp code into a blank sketch. Overwrite any existing code that was there.

2. Update the following info:

    - Add your Wifi network name
    - Add your Wifi password
    - Replace the Google Script Deployment ID with the ID obtained in step 8 above (note that the ID must be contained in quotation marks as shown in the example code).

3. Install the HTTPSRedirect library from here:

    https://github.com/electronicsguy/ESP8266

    (download and save the HTTPSRedirect folder in your library directory)

4. Upload code to your ESP8266 module and watch data get published to your sheet!

     

#### Additional Notes

1. When making changes to the Google Scripts code, you will need to click `Save` then `Deploy > New deployment` for any new changes to take effect. You will be given a new Deployment ID that you will have to update in the ESP8266 code each time (each new deployment is given a new Deployment ID).
