---
title:  "Bill Pay Web Scraper"
date:   2021-06-21 15:33:33 -0500
# categories: jekyll update
permalink: "/BillScraper/"
image: assets/Images/BillScraper/VenmoPic.jpg
excerpt: "Making the Boring Things Fun (Like Paying Bills)."
---

# Writing a Bill-Paying Web Scraper
This script scrapes the account history pages of the websites which manage my utility bills. The script outputs the values of each bill to a google sheets as well as the amount due by each tenant. Since I pay the bills directly from my bank account, the script then creates and sends a Venmo request for half of the cost to my roommate. 

Here are the Python packages that I employed to write this script (yes, even the emoji package 😆):
```python3
from selenium import webdriver
import datetime
import gspread
from oauth2client.service_account import ServiceAccountCredentials
from selenium.webdriver.common.by import By
from venmo_api import Client
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import emoji
```

Here is a code snippet showing how I split the cost of the bills by converting the scraped dollar amount strings and divide them by two with my roommate. 
```python3
# Splits the cost of the bills
def split(wifi, curr_elecbill):
    # Contribution calculation
    wifinosign = wifi.replace("$", "")
    wifiNum = float(wifinosign)
    elecnosign = curr_elecbill.replace("$", "")
    elecNum = float(elecnosign)
    cont = round(((wifiNum + elecNum) / 2), 2)  # round?
    return cont
```

Lastly, I use the Venmo API for Python to send a Venmo request to my roommate to complete the transaction.
```
# Copies contribution amount and auto sends venmo
def venmo_send(cont):
    # Venmo access token. You will need to complete the 2FA process
    access_token = Client.get_access_token(username=email,
                                           password=password3 device_id="YOUR-ID-HERE")

    venmo = Client(access_token=access_token)

    print("\nVenmo charge is approximately "+str(cont))

    dateprompt = input("Date for bills: ")

    prompt = input("Proceed with Venmo charge? (Y/N)  ")

    if prompt.lower().startswith("y"):

        # Request money for bills
        print(emoji.emojize("\nSending Venmo Request for this month's bills... :moneybag:\n", use_aliases= True))

        venmo.payment.request_money(cont, "Bills for "+dateprompt+""+emoji.emojize(":moneybag:", use_aliases= True), "USER-ACCESS-TOKEN-HERE")

        # Log out of venmo
        venmo.log_out(access_token)
```

The final result! 

![](/assets/Images/BillScraper/VenmoPic.jpg)

