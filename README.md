# Exploit Title: Online Shopping Portal Project v3.1 - Parameter Tampering - Exploit
# Date: 28-11-2021
# Exploit Author: Abhijeet Singh
# Vendor Homepage: https://phpgurukul.com/
# Software Link : https://phpgurukul.com/shopping-portal-free-download/
# Version: v3.1 (Latest)
# Tested on: macOS Monterey(Version 12.0.1)
# CVE: N/A

Parameter Tampering:
The Web Parameter Tampering attack is based on the manipulation of parameters exchanged between client and server in order to modify application data, such as user credentials and permissions, price and quantity of products, etc. Usually, this information is stored in cookies, hidden form fields, or URL Query Strings, and is used to increase application functionality and control.

Attack Vector:
An attacker can modify the price of a product inside the application.


Steps to reproduce:
1. Open product detail page using following URL and add a product to cart:
http://127.0.0.1/shopping/product-details.php?pid=15


2. Now click on `UPDATE SHOPPING CART` button and intercept the request.
3. Now alter the `quantity` parameter from `1` to `0.5` and forward the request.
Payload: quantity%5B15%5D=1 ---> quantity%5B15%5D=0.5


4. Here we can see that the price becomes half of the original value.

After completing the purchase and tracking the order we can confirm that the price manipulation was successful.

IMPACT:
An attacker can modify the price of a product and damage the website financially. 

Suggested Mitigation/Remediation Actions
Integrity check must be there at the server side for every product and their prices.
Do not accept a request containing a special character from the users-end.
Apply regex to check qty and product id.