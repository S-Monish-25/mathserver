# Ex.05 Design a Website for Server Side Processing
# Date: 30.11.2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html


{%load static%}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator for Lamp Filament</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: black;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ccc;
            background-color: red;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: black;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        
        #result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Power Calculator</h1>
        <p>Calculate the power of a lamp filament using the formula:</p>
        <p><b>P = I<sup>2</sup> × R</b></p>
        <form method="POST">
            {% csrf_token %}
           <label >I</label> <input type="text" name='intensity' placeholder="Enter intensity" id="intensity" value="{{i}}"> <br>
        
           <label >R</label> <input type="text " name="resistance" placeholder="Enter resistance" id="resistance" value="{{r}}"> <br>
         
           <button type="submit">Calculate Power</button> <br>

            <label >P</label><input type="text" placeholder="Answer" id="power" name="power" value="{{power}}" readonly>

        </form>
        <div id="result"></div>
    </div>

    
</body>
</html>

views.py
from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from maths import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]
```
# SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/891c6064-8bf6-4729-a3c3-bb6b5bccf26a)

# HOMEPAGE:
![Screenshot 2024-12-08 221010](https://github.com/user-attachments/assets/f8c9c463-1fc8-404e-a80d-e18ed2a628be)

# RESULT:
The program for performing server side processing is completed successfully.
