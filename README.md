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
# math.server
```html
<!DOCTYPE html>
<html>
<head>
    <title>GST Bill Calculator</title>

    <style>

        body{
            background-color: honeydew;
            font-family: Arial, Helvetica, sans-serif;
            text-align: center;
            margin-top: 50px;
        }

        .container{
            width: 400px;
            margin: auto;
        }

        h1{
            margin-bottom: 30px;
        }

        input{
            width: 120px;
            height: 25px;
            margin-top: 10px;
            margin-bottom: 20px;
        }

        button{
            padding: 6px 15px;
            margin-top: 10px;
            cursor: pointer;
        }

        h2{
            margin-top: 20px;
        }

    </style>
</head>

<body>

    <div class="container">

        <h1>GST Bill Calculator</h1>

        <form method="POST">

            {% csrf_token %}

            <label>Enter Price:</label><br>

            <input type="number" name="price" required><br>

            <label>Enter GST %:</label><br>

            <input type="number" name="gst" required><br>

            <button type="submit">Calculate</button>

        </form>

        {% if total %}

            <h2>Price : {{ price }}</h2>

            <h2>GST : {{ gst }}%</h2>

            <h2>Total Bill Amount : {{ total }}</h2>

        {% endif %}

    </div>

</body>
</html>
```
# views.py
```
from django.shortcuts import render

def home(request):

    total = None
    price = None
    gst = None

    if request.method == 'POST':

        price = float(request.POST['price'])
        gst = float(request.POST['gst'])

        total = price + (price * gst / 100)

    return render(request, 'math.html',
                  {'total': total,
                   'price': price,
                   'gst': gst})
```
# urls.py
```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('gstapp.urls')),
]
```

## OUTPUT - SERVER SIDE:
<img width="443" height="212" alt="{323DDFE2-2764-4361-A526-500A671B2D53}" src="https://github.com/user-attachments/assets/18a86c6f-bbdf-4b4d-9408-7e725df3c644" />


## OUTPUT - WEBPAGE:
![Uploading {F3E76E74-7583-4478-BB9A-00E33A127602}.png…]()


## RESULT:
The a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts is created successfully.
