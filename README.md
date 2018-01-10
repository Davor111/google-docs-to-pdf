# Google Apps Script To PDF Files

This is a simple Google App Script to convert all Google Docs or Google Sheets documents in a folder to PDF. 

No downloads are required as this is all done within the Google Drive application. You only need to provide folder IDs for the document root folder and the destination folder for the PDFs. The script will convert all Google documents in the root folder.

## How to: 

1. Create a new Google Apps Script document in your Google Drive app (NEW -> OTHER -> Google Apps Script). You might need to add the Google App Script app to your Google Drive account. 
2. Copy and paste the app.gdoc provided in this repository or copy and paste into a new Google App Script document.
3. Get the folder IDs. For this open up Google Drive, open the folder of the documents you want to convert and look at the URL in the browser. You will see something like this:<br> 
https://drive.google.com/drive/u/0/folders/THIS-IS-THE-FOLDER-ID-YOU-NEED-TO-COPY <br>
Copy and Paste the folder ID and do the same for the folder you want the PDF to be created in. You can use only one folder ID, if you want to create them in the same folder.
4. Exchange the folder IDs in your newly created Google Apps script document. Run the function gdocToPDF() and accept that this script is allowed to access your Drive files. PDFs should be created then.   
5. Optional: Set a trigger to convert the documents every X minutes/hours/days. Click on Edit -> All my triggers. Choose "gdocToPDF()" and the time frame.  
