# Level 1 Getting Started

In this exercise, you will Setup CF trail account to get try Document Classification and Document Information Extraction Service 

## Level 2 Create Trail Account

After completing these steps you will have trail account where you can use DOX and DC

1.	Click here.
<br>![](/exercises/ex0/images/00_00_0010.png)

2.	Insert this code.
```
 DATA(lt_params) = request->get_form_fields(  ).
 READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.
```

## Summary

Now that you have create a trail account
Continue to - [Exercise 1 - Exercise 1 Description](../ex1/README.md)
