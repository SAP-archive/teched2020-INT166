# Exercise 2 - Document Information Extraction

In this exercise, we will create...

## Exercise 2.1 - Setup Document Information Extraction Service and UI

After completing below step you will have access for Document Information Extraction Service and its UI Application

1. Follow this [tutorial](https://developers-qa.sap.com/tutorials/cp-aibus-dox-service-instance-booster.html)
2. Follow this [tutorial](https://developers-qa.sap.com/tutorials/cp-aibus-dox-ui-sub.html)

## Exercise 2.2 - Upload a document for Extraction using UI Application

After completing these steps your will have information extracted from documents.

1.	In the top right, click + (Upload a new document).
<br>![](/exercises/ex2/images/02_02_1.png)


2.	In the Select Document screen, drop files directly or click + to upload one or more document files.
<br>![](/exercises/ex2/images/02_02_2.png)

3. Select the Document Type **Invoice**. 
<br>![](/exercises/ex2/images/02_02_3.png)

4. Click **Step 2**.
<br>![](/exercises/ex2/images/02_02_4.png)

5. In Step 2, select the header fields you want to extract from the invoice documents you uploaded in the previous step. Click Step 3.
<br>![](/exercises/ex2/images/02_02_5.png)

6. In Step 3, select the line items you want to extract from the documents you uploaded in the previous step. Click Review.
<br>![](/exercises/ex2/images/02_02_6.png)

7. Review your selection. Click Edit if you want to change anything. Click Confirm.
<br>![](/exercises/ex2/images/02_02_7.png)

8. You see the Document Name, Upload Date and Status of the documents you have just uploaded.
<br>![](/exercises/ex2/images/02_02_8.png)

Status changes from PENDING to READY. This means the selected header fields and line items have been extracted, and the extraction results are ready to be validated and changed if necessary. If status changes from PENDING to FAILED, this means it was not possible to get the extraction results, and you need to upload the document once again.
<br>![](/exercises/ex2/images/02_02_9.png)


## Exercise 2.3 - Visualize and Correct Extraction Results on UI Application

## Exercise 2.4 - Upload Data through Rest API

## Exercise 2.5 - Upload Document through Rest API to encrich the extraction results with Supplier Data


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
