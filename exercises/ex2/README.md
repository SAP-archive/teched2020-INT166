# Exercise 2 - Document Information Extraction

In this exercise, we will use Document Information Extraction Service to do following

- Upload Documents for extraction using UI
- Correct and Confirm Extracted information using UI
- Retrive Extracted Information Using Rest API
- Upload Supplier Master Data for Invoices
- Upload document for extraction using Rest API and enable enrichments for matching supplier id with Sender information

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

After completing these steps you will have understand how the UI Application can be used to correct extraction results and Flag them after a manual verification is done by the user.

1. Click on **twitter.pdf (Invoice)** in the Documents list to open the Preview if the document.


2. Click on the **Extraction Results** Button to view the extracted information.
<br>![](/exercises/ex2/images/02_03_2.png)

3. Check the extracted Header Fields and Line Items.
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


## Exercise 2.4 - Get Auth Token to use Document Information Extraction Rest API

Follow this [tutorial](https://developers-qa.sap.com/tutorials/cp-aibus-dox-web-oauth-token.html)

Keep the tab open since we'll need access token in next steps

## Excercise 2.5 - Get Extraction Results of Document using Rest API

You will use Swagger UI, via any web browser, to call the Document Information Extraction APIs. Swagger UI allows developers to effortlessly interact and try out every single operation an API exposes for easy consumption. For more information, see [Swagger UI](https://swagger.io/tools/swagger-ui/).

In the service key you created for Document Information Extraction in the previous tutorial: [Set Up Account for Document Information Extraction](https://developers-qa.sap.com/tutorials/cp-aibus-dox-service-instance-booster.html), you should find (outside the uaa section of the service key) an entry called url and another entry called swagger (as highlighted in the image below).

1. To access the Document Information Extraction Swagger UI, add the swagger value (**/document-information-extraction/v1**) to the url value, paste it in any web browser and press Enter.
<br>![](/exercises/ex2/images/02_05_1.png)

2. To be able to use the Swagger UI endpoints you need to authorize yourself. In the top right corner, click **Authorize**.
<br>![](/exercises/ex2/images/02_05_2.png)

3. Get the access_token value created in the previous exercise: Get Auth Token to use Document Information Extraction Rest API, then add **bearer** in front of it, and enter in the **Value** field. eg. `bearer <access_token>`
<br>![](/exercises/ex2/images/02_05_3.png)

4. Click **Authorize**, and then click **Close**.
<br>![](/exercises/ex2/images/02_05_4.png)

5. Expand the **GET /document/jobs** endpoint and click **Try it Out**.
<br>![](/exercises/ex2/images/02_05_5.png)

6. Input value `default` in **clientId** parameter and click on **Execute**.
<br>![](/exercises/ex2/images/02_05_6.png)

7. Check the **Response Body**, it will contain list of jobs in json format.
<br>![](/exercises/ex2/images/02_05_7.png)

8. In the **Response Body**, find the document with `"status": "CONFIRMED"`, you'll find that this is the same **twitter.pdf** that we confirmed in Exercise 2.3.
<br>![](/exercises/ex2/images/02_05_8.png)

9. Copy the value corresponding to `id` for **twitter.pdf**.
<br>![](/exercises/ex2/images/02_05_9.png)

10. Collapse **GET /document/jobs** endpoint and Expand the **GET /document/jobs/{id}** endpoint.

11. Click **Try it Out**
<br>![](/exercises/ex2/images/02_05_11.png)

12. Paste the value of `id` copied in step 9 into the **id** parameter and click on **Execute**.
<br>![](/exercises/ex2/images/02_05_12.png)

13. Check the **Reponse Body**, you'll find the information about job like `filename`, `status` etc. `headerFields` contains extraction results of Header fields. `lineItems` will contains results for Line items.
<br>![](/exercises/ex2/images/02_05_13a.png)
<br>![](/exercises/ex2/images/02_05_13b.png)


## Exercise 2.6 - Upload Supplier Data for matching

1. Expand the **POST /data/jobs** endpoint and click **Try it out**.
<br>![](/exercises/ex2/images/02_06_1.png)

2. Define the data in the payload field, so that the system knows which extracted field (using, for example, supplier IDs from master data) should be enriched. The date is below.
```json
{
   "value":[
      {
         "id":"BE0001",
         "name":"Umbro LLC",
         "accountNumber":"",
         "address1":"15 Sports Goods Street, London UD12 3TY",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"UK8080808080",
         "taxId":""
      },
      {
         "id":"BE0002",
         "name":"Twitter UK",
         "accountNumber":"",
         "address1":"15 Tweetdrive, Worthing BN12 3NX",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"GB34 5654 33456 3456 4565 35",
         "taxId":""
      },
      {
         "id":"BE0003",
         "name":"RC Consulting LLC",
         "accountNumber":"",
         "address1":"15 Enterprise Lane, Boston, MA 02125",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"US11 1111 1111 2222 33",
         "taxId":""
      },
      {
         "id":"BE0004",
         "name":"Norsk Folkehjelp",
         "accountNumber":"",
         "address1":"Stortorvet 100, 0255 OSLO Ministry of Health Aristotelous 17 Athina 104 33 Greece",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"NO80 8080 8080 8080 80",
         "taxId":""
      },
      {
         "id":"BE0005",
         "name":"NSYFAC Naval Facilities Engineering Command",
         "accountNumber":"",
         "address1":"Military Base 15, D.C. 65472-8326 US Command",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"US67 6767 6767 6767 6767 67",
         "taxId":""
      },
      {
         "id":"BE0006",
         "name":"Beijing 2008 OOC",
         "accountNumber":"",
         "address1":"15 Sports Goods Street, Bejing UD12 3TY",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"CN80 8080 8080 8080 8080 80",
         "taxId":""
      },
      {
         "id":"BE0007",
         "name":"Chinese Blogger Conference",
         "accountNumber":"",
         "address1":"Soho Tower, 25 Hart Avenue, Hong Kong",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"CN36 9369 3693 6936 9369 36",
         "taxId":""
      },
      {
         "id":"BE0008",
         "name":"Engenharia Ambiental",
         "accountNumber":"",
         "address1":"Service Drive 15, 18767 Manchester",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"GB27 2789 2789 2789 2789 89",
         "taxId":""
      },
      {
         "id":"BE0009",
         "name":"Flickr",
         "accountNumber":"",
         "address1":"Entrepeneurweg 15, 54321 Neustadt",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"DE28 4321 4321 4321 4321 21",
         "taxId":""
      },
      {
         "id":"BE0010",
         "name":"guru shop",
         "accountNumber":"",
         "address1":"Expertenweg 15, 90120 Gláubighausen",
         "address2":"",
         "city":"",
         "countryCode":"",
         "postalCode":"",
         "state":"",
         "email":"",
         "phone":"",
         "bankAccount":"DE12 3412 3412 3412 34",
         "taxId":""
      }
   ]
}
```
<br>![](/exercises/ex2/images/02_06_2.png)

3. Choose the enrichment data **type** value `businessEntity`.

4. Enter **clientId** as `default` .

5. Choose the **subtype** value `supplier`.

6. Click **Execute**.
<br>![](/exercises/ex2/images/02_06_6.png)

7. You should receive a response like the following with status PENDING, copy the `id` from the Response body to see the result of the enrichment data status in the next step.
<br>![](/exercises/ex2/images/02_06_7.png)

8. Expand the **GET /data/jobs/{id}** endpoint and click **Try it out**.
<br>![](/exercises/ex2/images/02_06_8.png)

9. Paste the `id` copied in step 8, in `id` parameter and click **Execute**
<br>![](/exercises/ex2/images/02_06_9.png)

10. You should receive a response like the following with status `SUCCESS`. If it's still `PENDING` try again in some time.
<br>![](/exercises/ex2/images/02_06_10.png)


## Exercise 2.7 - Upload Document through Rest API to enrich the extraction results with Supplier Data

1. Expand the **POST /document/jobs** endpoint and click **Try it out**.
<br>![](/exercises/ex2/images/02_07_1.png)

2. Choose one of the invoice document file you want to enrich for **file** parameter.
<br>![](/exercises/ex2/images/02_07_2.png)

3. In **options**, enter the list of fields to be extracted from the uploaded file, the **clientId** as `default`, the **documentType** as `invoice`, the enrichment data **type** as `businessEntity` and **subtype** as `supplier`. The Payload will be as following:
```json
{
   "extraction":{
      "headerFields":[
         "documentNumber",
         "purchaseOrderNumber",
         "netAmount",
         "senderAddress",
         "senderName",
         "senderBankAccount",
         "grossAmount",
         "currencyCode",
         "documentDate",
         "taxAmount",
         "receiverName",
         "receiverAddress",
         "paymentTerms"
      ],
      "lineItemFields":[
         "description",
         "netAmount",
         "quantity",
         "unitPrice"
      ]
   },
   "clientId":"default",
   "documentType":"invoice",
   "enrichment":{
      "sender":{
         "top":5,
         "type":"businessEntity",
         "subtype":"supplier"
      }
   }
}
```
<br>![](/exercises/ex2/images/02_07_3.png)

4. Click **Execute**.

5. You'll get a response with **status** as `PENDING`. Copy the value of `id` in response payload.
<br>![](/exercises/ex2/images/02_07_5.png)

6. Expand the **GET /document/jobs/{id}** endpoint, and click **Try it out**.
<br>![](/exercises/ex2/images/02_07_6.png)

7. Paste the id copied in step 5 as the **id** in parameter. click on **Execute**.
<br>![](/exercises/ex2/images/02_07_7.png)

8. Check the response body, one of the extracted fields is the sender name with value `Twitter UK,`. This information is enriched with the supplier ID enrichment data created in **excersice 2.6 - step 2**. The prediction suggests the supplier ID BE0002 (from sender name Twitter UK).
<br>![](/exercises/ex2/images/02_07_8.png)


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
