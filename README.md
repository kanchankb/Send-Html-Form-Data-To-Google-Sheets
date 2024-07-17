# Send-Html-Form-Data-To-Google-Sheets

This project demonstrates how to send data from an HTML form to a Google Sheet using Google Apps Script as a web app. This can be useful for capturing form submissions directly into a Google Sheet without needing a server-side backend.

Getting Started
Follow these instructions to set up the project on your local machine.

Prerequisites
•	A Google account
•	Basic knowledge of HTML, JavaScript, and Google Apps Script

Setting Up Google Apps Script:

1.	Create a Google Sheet:
o	Create a new Google Sheet where form submissions will be saved.
o	Note the sheet's URL as you'll need it later.

3.	Create a Google Apps Script:
o	Open the Google Sheet you created.
o	Click on Extensions > Apps Script.
o	Delete any code in the script editor and replace it with the following script:

function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  sheet.appendRow([data.name, data.email, data.message]);
  return ContentService.createTextOutput(JSON.stringify({ 'result': 'success', 'data': JSON.stringify(data) })).setMimeType(ContentService.MimeType.JSON);
}

	Deploy as a Web App:
•	Click on Deploy > New deployment.
•	For Description, enter "HTML Form to Google Sheets".
•	Under Execute as, select Me (your email).
•	Under Who has access, select Anyone.
•	Click Deploy.
•	Copy the web app URL provided after deployment.

Setting Up the HTML Form
Create an script File:
  <script>
        const scriptURL = 'please write googlesheet url here'
        const form = document.forms['submit-to-google-sheet']
      
        form.addEventListener('submit', e => {
          e.preventDefault()
          fetch(scriptURL, { method: 'POST', body: new FormData(form)})
            .then(response => console.log('Success!', response))
            .catch(error => console.error('Error!', error.message))
        })
      </script>

      1.	Replace YOUR_WEB_APP_URL:
o	Replace 'YOUR_WEB_APP_URL' in the fetch call with the URL of your deployed Google Apps Script web app.

Running the Project:
1.	Open the HTML File:
o	Open the index.html file in your web browser

3.	Submit the Form:
o	Fill out the form and click Submit.
o	Check your Google Sheet to see if the data has been appended.



code output :-

![image](https://github.com/user-attachments/assets/bd6bd86c-c61e-4e91-9468-069854780bd5)




