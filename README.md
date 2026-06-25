# Modded TikTok Investigation
This was an investigation I did into a modded TikTok app for my CPE 400 class. I found suspicious DNS lookup requests to the personal site of the developer, but did not find anything concrete.
[Insert Image Here]

## Methodoloy
I took 10 packet captures of the modded TikTok app using PCAPdroid. Each capture lasted a minute and included the app's startup sequence. I took those 10 captures and analyzed them with in Python to look for IP addresses present in every capture. Finally I used the IPinfo API to retrieve information on each IP address.

## Findings
The program identified 117 unique destination IPs among the 10 packet captures. Of these, 103 are shared between the captures. Of those 103, 83 belong to Akamai. Of the remaining 20, 17 belong to known organizations such as Amazon, Oracle, UNR, and ByteDance (Tik-Tok’s parent company). The three remaining address, `151.101.42.73`, `185.199.110.153`, and `185.199.108.153`, belong to Fastly. In this context, Fastly is a CDN and cloud provider for GitHub. Viewing the traffic to these addresses reveals them to be DNS lookup requests for the domain "rezvorck.github.io". Visiting the address reveals to be the personal page for a Russian developer “Rezvorck”. Its not clear what the connection is here, whether Rezvorck is the developer or distributor of the modded TikTok app, nor what the purpose of these DNS lookups are.
[Insert Image Here]

## Installation
To run the script I used yourself, ensure you have any version of Python 3 as well as the packages present in the requirements.txt file (`pip install -r requirements.txt`). Run the script with `python3 code.py`
