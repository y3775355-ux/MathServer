# Ex.04 Design a Website for Server Side Processing
## Date:

## AIM:
To create a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts.

## FORMULA:
Bill = P + (P * GST / 100)
<br> P --> Price (in Rupees)
<br> GST --> GST (in Percentage)
<br> Bill --> Total Bill Amount (in Rupees)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the total bill amount (including GST).

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
math.html
```
<!DOCTYPE html>
<html>
<head>
    <title>GST BILL CALCULATOR</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }

        .container {
            max-width: 350px;
            margin: auto;
            padding: 40px;
            border: 10px solid green;
            background-color: lightyellow;
        }

        input, button {
            margin: 10px;
            padding: 5px;
        }
    </style>
</head>

<body bgcolor="#E6F7FF">

<form method="POST">
    {% csrf_token %}

    <div class="container">
        <h2>GST BILL CALCULATOR 💰</h2>

        Price (₹):
        <input type="text" name="price" value="{{price}}"><br>

        GST (%):
        <input type="text" name="gst" value="{{gst}}"><br>

        <button type="submit">GET RESULT</button><br>

        Total Bill (₹):
        <input type="text" name="bill" value="{{bill}}"><br>

    </div>
</form>

</body>
</html>
```
views.py 
```
from django.shortcuts import render

def gst(request):
    context = {}
    context['bill'] = ""
    context['price'] = "0"
    context['gst'] = "0"

    if request.method == "POST":
        print("POST method is used")

        price = request.POST.get('price', '0')
        gst = request.POST.get('gst', '0')

        print("request=", request)
        print("Price=", price)
        print("GST=", gst)

        bill = float(price) + (float(price) * float(gst) / 100)

        context['bill'] = bill
        context['price'] = price
        context['gst'] = gst

        print("Total Bill=", bill)

    return render(request, 'mathapp/math.html', context)
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.gst, name="GST"),
]
```
## OUTPUT - SERVER SIDE:
<img width="1517" height="851" alt="Screenshot 2026-06-03 105236" src="https://github.com/user-attachments/assets/9436e2e6-2bae-4247-9f98-bf9a5eadb9f8" />


## OUTPUT - WEBPAGE:
<img width="1515" height="848" alt="Screenshot 2026-06-03 105203" src="https://github.com/user-attachments/assets/f7e02b0e-29f5-4dda-b63a-40434e2d56de" />


## RESULT:
The a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts is created successfully.
