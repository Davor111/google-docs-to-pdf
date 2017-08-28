function gdocToPDF() {
    var documentRootfolder = DriveApp.getFolderById("DOCUMENT-ROOT-ID") // replace this with the ID of the folder that contains the documents you want to convert
    var pdfFolder = DriveApp.getFolderById("FOLDER-PDFs-WILL-BE-CREATED-IN"); // replace this with the ID of the folder that the PDFs should be put in. 

    var documentRootFiles = documentRootfolder.getFiles()

    while(documentRootFiles.hasNext()) {
        createPDF(documentRootFiles.next().getId(), pdfFolder.getId(), function (fileID, folderID) {
            if (fileID) createPDFfile(fileID, folderID);
        })
    }
}


function createPDF(fileID, folderID, callback) {
    var templateFile = DriveApp.getFileById(fileID);
    var templateName = templateFile.getName();
    
    var existingPDFs = DriveApp.getFolderById(folderID).getFiles();

    //in case no files exist
    if (!existingPDFs.hasNext()) {
        return callback(fileID, folderID);
    }

    for (; existingPDFs.hasNext();) {

        var existingPDFfile = existingPDFs.next();
        var existingPDFfileName = existingPDFfile.getName();
        if (existingPDFfileName == templateName + ".pdf") {
            Logger.log("PDF exists already. No PDF created")
            return callback();
        }
        if (!existingPDFs.hasNext()) {
            Logger.log("PDF is created")
            return callback(fileID, folderID)
        }
    }
}

function createPDFfile(fileID, folderID) {
    var templateFile = DriveApp.getFileById(fileID);
    var folder = DriveApp.getFolderById(folderID);
    var theBlob = templateFile.getBlob().getAs('application/pdf');
    var newPDFFile = folder.createFile(theBlob);

    var fileName = templateFile.getName().replace(".", ""); //otherwise filename will be shortened after full stop    
    newPDFFile.setName(fileName + ".pdf");
}
