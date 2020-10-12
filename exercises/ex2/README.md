# Exercise 2 - Document Information Extraction

In this exercise, we will create...

## Exercise 2.1 - Setup Document Information Extraction Service and UI

After completing these steps you will have created...

1. Click here.
<br>![](/exercises/ex2/images/02_01_0010.png)

2.	Insert this line of code.
```abap
response->set_text( |Hello ABAP World! | ). 
```



## Exercise 2.2 - Upload a document for Extraction using UI Application

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc = 0.
    response->set_status( i_code = 200
                     i_reason = 'Everything is fine').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex2/images/02_02_0010.png)

## Exercise 2.3 - Visualize and Correct Extraction Results on UI Application

## Exercise 2.4 - Upload Data through Rest API

## Exercise 2.5 - Upload Document through Rest API to encrich the extraction results with Supplier Data


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
