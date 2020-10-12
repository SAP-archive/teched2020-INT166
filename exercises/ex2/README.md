# Exercise 2 - Document Information Extraction

In this exercise, we will use Document Information Extraction Service to do following

- Upload Documents for extraction using UI
- Correct and Confirm Extracted information using UI
- Retrive Extracted Information Using Rest API
- Upload Supplier Master Data for Invoices
- Upload document for extraction using Rest API and enable enrichments for matching suppier id with Sender information

## Exercise 2.1 - Setup Document Information Extraction Service and UI

After completing below step you will have access for Document Information Extraction Service and its UI Application

1. Follow this [tutorial](https://developers-qa.sap.com/tutorials/cp-aibus-dox-service-instance-booster.html)
2. Follow this [tutorial](https://developers-qa.sap.com/tutorials/cp-aibus-dox-ui-sub.html)

## Exercise 2.2 - Upload documents for Extraction using UI Application

After completing these steps your will have information extracted from documents.

1.	In the top right, click + (Upload a new document).
<br>![](/exercises/ex2/images/02_02_1.png)


2.	In the Select Document screen, drop Invoice files directly or click + to upload one or more document files.
<br>![](/exercises/ex2/images/02_02_2.png)

3. Select the Document Type **Invoice**. 
<br>![](/exercises/ex2/images/02_02_3.png)

4. Click **Step 2** button.
<br>![](/exercises/ex2/images/02_02_4.png)

5. In Step 2, select the header fields you want to extract from the invoice documents you uploaded in the previous step. Click **Step 3** button.
<br>![](/exercises/ex2/images/02_02_5.png)

6. In Step 3, select the line items fields you want to extract from the documents you uploaded in the previous step. Click **Review** button.
<br>![](/exercises/ex2/images/02_02_6.png)

7. Review your selection. Click **Confirm** button.
<br>![](/exercises/ex2/images/02_02_7.png)

8. You see the Document Name, Upload Date and Status of the documents you have just uploaded.
<br>![](/exercises/ex2/images/02_02_8.png)

Status changes from PENDING to READY. This means the selected header fields and line items have been extracted, and the extraction results are ready to be validated and changed if necessary. If status changes from PENDING to FAILED, this means it was not possible to get the extraction results, and you need to upload the document once again.
<br>![](/exercises/ex2/images/02_02_9.png)

9. Repeat above steps 1-7 for Payment Advice Documents. Only difference is, in Step 3 Select Document Type **Payment Advices** and select relevent header fields and line items.


## Exercise 2.3 - Visualize, Correct Extraction Results and Confirm Document using UI Application

After completing these stepds you will have understand how the UI Application can be used to correct extraction results and Flag them after a manual verification is done by the user.

1. Click on **twitter.pdf (Invoice)** in the Documents list to open the Preview if the document.


2. Click on the **Extraction Results** Button to view the extracted information.
<br>![](/exercises/ex2/images/02_03_2.png)

3. Check the extracted extracted Header Fields and Line Items.
<br>![](/exercises/ex2/images/02_03_3.png)

4. Click on input field label **Sender Bank Account** to highlight location from where the value is extracted from in Preview.
<br>![](/exercises/ex2/images/02_03_4.png)

5. Expand First Line Item and click on **Description** to to highlight location from where the value is extracted from in Preview.
<br>![](/exercises/ex2/images/02_03_5.png)

6. Click on **Edit** Button, to fix some wrongly extracted information.
<br>![](/exercises/ex2/images/02_03_6.png)

7. Click on Currency Code Input Field, Search for **British** in Currencies Dialog Box and Click on **British Pound**.
<br>![](/exercises/ex2/images/02_03_7.png)

8. Draw a selection box around **Due Date: 31/2/2018** in Document Preview, select **Payement Terms** for field in **Assign Field** Popover and click **Apply**.
<br>![](/exercises/ex2/images/02_03_8.gif)

9. Now that all the information is correct, Click on **Confirm** button and then again click **Confirm** button in the **Confirm Extracted Values?** dialog box to save the information and mark the results as **Confirmed**.
<br>![](/exercises/ex2/images/02_03_9.png)

You'll notice that the document status has change to **CONFIRMED**.
<br>![](/exercises/ex2/images/02_03_10.png)


## Exercise 2.4 - Upload Data through Rest API

## Exercise 2.5 - Upload Document through Rest API to encrich the extraction results with Supplier Data


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
