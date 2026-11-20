# DVLA UK Licence Plate Validator & Generator

A Python program I built to validate standard post-2001 UK licence plates, find out a car's registration year and age, look up the city and region it was registered in, and generate random example plates. Inputs are case-insensitive and spaces get stripped automatically, so a plate works whether you enter `AB21 BTR` or `ab21btr`.

## Menu Options

* **`1` — Check for valid licence plate:** Runs the plate through all four validation checks and confirms whether it follows DVLA rules.


* **`2` — Find age of the car:** Validates the plate, reads the middle two numbers to check whether it was registered in March–August (`02–26`) or September–February (`51–76`), and works out the year and age up to 2026.


* **`3` — Find the city registered in:** Validates the plate and matches its 2-letter area code against a lookup dictionary (`GROUPED_MAP`) of UK DVLA offices and regions.


* **`4` — Generate example licence plate:** Randomly picks valid starting area letters, a valid summer (`02–26`) or winter (`51–76`) age number, and three valid ending letters to build a 7-character UK plate.


* **`0` — Exit program:** Ends the program loop.



## How Validation Works

Whenever you enter a plate in options 1–3, it gets stripped of spaces, converted to uppercase, and checked in this order:

1. **Exact length (`ValidLength`):** Makes sure the plate is 7 characters long after removing spaces.


2. **Starting area letters (`ValidStartLetters`):** Rejects banned letters (`Q`, `I`, and `Z`, plus `J`, `U`, `T`, and `X` in the first position) and checks that the area tag is alphabetic.


3. **Ending 3 letters (`ValidEnd`):** Checks the last 3 characters to make sure they are all letters and don't use `Q` or `I`.


4. **Middle age numbers (`ValidMIddleNUmbers`):** Verifies the digits sit in the valid post-2001 ranges (`02–26` for March–August or `51–76` for September–February).



## Files in This Repo

* **`DLVA_Program.py`** — The main interactive menu program for checking plates, finding car age, looking up registration cities/regions, and generating example plates.


* **`DVLAtest.py`** — Automated test script with 9 test suites that log results out to `DVLAtestOUTPUT1`–`DVLAtestOUTPUT9`.



## Testing

`DVLAtest.py` lets you run 9 separate test sets covering first letters, second letters, the final 3 letters, age number boundaries (`02`, `26`, `51`, `76`), spacing and length edge cases, every UK city/region tag in `GROUPED_MAP`, year/age calculations, menu inputs, and bulk random plate generation. Each suite includes valid uppercase and lowercase plates alongside out-of-range numbers, banned DVLA letters, and invalid symbols.
