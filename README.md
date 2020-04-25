# Log data from an ESP8266 to Google Sheets

###### Below are step by step instructions to begin logging data using an ESP8266 module. This will publish random number values, so no additional hardware or sensors are required for the script to run. These instructions assume you are familiar with the Arduino IDE and how to upload code to your ESP8266 and install libraries.

#### Instructions for Google Sheets

1. Create new Google Sheets document, and give it a name.

2. Type the following header text into each of the following cells:

   - Cell A1: `Date`
   - Cell B1: `Time`
   - Cell C1: `value0`
   - Cell D1: `value1`
   - Cell E1: `value2`
   
3. Get the Spreadsheet ID from the URL.

   For example, if the URL is:
   https://docs.google.com/spreadsheets/d/3213k-okfjdk-gkeJHjd87-vdKei-lKQDIc-a2a_Hjg4/edit#gid=0

   Then the Spreadsheet ID is:
   3213k-okfjdk-gkeJHjd87-vdKei-lKQDIc-a2a_Hjg4

4. From the Google Sheets menu, go to `Tools > Script Editor`

5. Delete the default text in the script editor, and paste the GoogleScripts-example.gs code.

6. Update the Spreadsheet ID with the ID obtained in step 3.

7. Go to `Publish > Deploy as web app`.

   - Enter a Project Name 
   - Project Version: `New`  
   - Execute the app as: `Me`
   - Who has access to the app: `Anyone, even anonymous`
   - Click `Deploy`

8. Click `Review Permissions` if asked for authorization. 

   - Select your account
   - Select `Advanced`
   - Select `Go to your-project-name (unsafe)` 
   - Click `Allow`

9.  Get the Script ID from the web app URL (this is not the same as the website URL)

   For example, if the URL is 
   https://script.google.com/macros/s/zDcGefuxEz5jG3RYq8sT4Sqq3aZ9MRKLgsqr9ejHkApmjQAkqAvxQXaq/exec

   Then the Script ID is 
   zDcGefuxEz5jG3RYq8sT4Sqq3aZ9MRKLgsqr9ejHkApmjQAkqAvxQXaq

10. From the script editor, go to `Run > Run function > doPost`.

11. Click the `Save` icon.

    

#### Instructions for ESP8266

1. In the Arduino IDE, paste the ESP8266-example.cpp code into a blank sketch. Overwrite any existing code that was there.

2. Update the following info:

    - Add network name
    - Add password
    - Replace the Google Script ID with the ID obtained in step 9 above.

3. Install the HTTPSRedirect library from here

    https://github.com/electronicsguy/ESP8266

    (download and save the HTTPSRedirect folder in your library directory)

4. Upload code to your ESP8266 module and watch data get published to your sheet.

     

#### Notes

1. When editing the Google Scripts code, you will need to `Publish > Deploy as a web app` for the changes to take effect. Make sure to change the Project Version to `New` each time. 

