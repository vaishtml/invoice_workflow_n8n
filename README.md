###  Invoice Workflow - n8n

## Overview

The workflow is triggered when a new file is created in a specific Google Drive folder. It downloads the file, extracts information from it, and then uses that information to update a Google Sheet and send an email notification.

## Workflow Steps

## 1\. **Google Drive Trigger**

The workflow starts automatically whenever a new file is added to the "DEMO" folder in Google Drive.

## 2\. **Download Binary**

This step downloads the new file from Google Drive so the workflow can access its content.

## 3\. **Extract from File**

This node is responsible for reading the content of the downloaded file, likely a PDF, to get the text from the invoice.

## 4\. **Information Extractor**

This step uses an **AI model**, Google Gemini, to extract specific data points from the text. It looks for details like:

  - **Invoice Number**
  - **Client Name**
  - **Client Email**
  - **Client Address**
  - **Client Phone**
  - **Total Amount**
  - **Invoice Date**
  - **Due Date**

## 5\. **Update DB**

The extracted information is then used to add a new row to a Google Sheets spreadsheet named "Invoice DB," effectively logging the invoice details.

## 6\. **Create Email**

Using an **AI model**, GPT-4o-mini, this step generates an email to be sent to an internal billing team. The email's content is created based on the extracted invoice details.

## 7\. **Send Email**

The generated email is sent to `xyz@gmail.com` to notify the billing team that a new invoice has been processed and added to the database.

## 8\. **No Operation, do nothing**

This final step does not perform any action and marks the end of the workflow.
