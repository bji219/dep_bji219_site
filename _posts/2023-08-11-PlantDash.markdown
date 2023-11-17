---
title:  "Plant Dashboard"
date:   2023-08-11 15:33:33 -0500
permalink: "/PlantDashboard/"
excerpt: "Green Thumbs Up"
image: assets/Images/PDB/bonsai.png
---

# Plants
Otts in Phoenixville

# Moisture and Temperature Sensor
I used the [Adafruit Moisture Sensor](https://www.adafruit.com/product/4026?gad_source=1&gclid=Cj0KCQiAmNeqBhD4ARIsADsYfTdZhK3RA6qm0lkXq8VbazNq9MfwznrWmgwvLLp2y8q5B3fl0uMYlLEaAiF_EALw_wcB) in conjunction with my Raspberry Pi to monitor my plant's temperature level and moisture level.

I was able to clone the bus on the Raspberry pi to a separate GPIO pin so that I can run two sensors at once.

# Python Code
I wrote some simple python code that reads the moisture and temperature of each sensor and sends the data to my Supabase database.
```python
```

# Supabase
I save a reading from the sensors every 5 minutes to my [Supabase](https://supabase.com/) database. This simple SQL table houses the time the reading was taken as well as the moisture and temperature reading from each sensor. 

# Flask Application

# HTML Code

# Dashboard 

