# URLShortener- Readme
Making URL shortner(only cli based) with python language.

#Features:
Shortens long URLs to 3 random character alphanumeric codes.
stores url data in csv file.
click tracking for shortened urls.
checking if the url is valid or not.
open urls using webbrowser.

#Language:
Python

#Working:
The code provides the user with options to choose from regarding the result they desire.

load_urls() — Reads Saved Links
Purpose: Reads all saved short codes and original web addresses from a CSV file into memory.

How it works:

Checks if the storage file (D) exists.

If it exists, opens the CSV file and reads it line by line.

Converts each row into a Python dictionary containing the short_code, original url, and the clicks count (converted to an integer number).

Returns all this data so other functions can use it.

save_urls(urls) — Saves Links to File
Purpose: Writes the updated list of short links back into the CSV file.

How it works:

Opens the CSV file in write mode ("w").

Creates column headers: short_code, url, and clicks.

Writes the header first, then loops through all short codes in memory and writes each one into the file.

is_valid_url(url) — Checks If the Website Works
Purpose: Checks if a link actually exists on the internet before saving it.

How it works:

Pretends to be a regular web browser (User-Agent: Mozilla/5.0) and sends a quick request to the website with an 8-second timeout limit.

Returns True if the website responds successfully.

Returns False if there is a network error or a broken link (404 Not Found).

make_readable_code(url) — Creates human-friendly short codes
Purpose: Generates a custom readable short code using the website's main domain name (e.g., google-a8X).

How it works:

Strips out prefixes like https://, http://, and www..

Extracts the primary domain name (e.g., youtube from [youtube.com/watch](https://youtube.com/watch)).

If no name remains, defaults to "link".

Pick 3 random letters/digits and attaches them to the domain name (e.g., github-9k2).

generate_short_code(length=3) — Generates Random Codes
Purpose: Generates a purely random 3-character short code (e.g., a7B).

How it works:

Takes all letters (A-Z, a-z) and numbers (0-9).

Picks 3 characters completely at random and combines them.

shorten_url() — Handles New Link Creation
Purpose: Takes a long URL from the user, validates it, and prepares it for saving.

How it works:

Asks you to type in a long web link.

Automatically adds https:// if you forgot to include it.

Runs is_valid_url() to verify if the link works. If it fails, asks if you still want to save it anyway.

Loads existing saved URLs into memory. (Note: This function is currently incomplete near the end in your provided code).

find_url() — Finds, Tracks Clicks & Opens Link
Purpose: Looks up a short code, increments its click count, displays its original URL, and offers to open it in your browser.

How it works:

Asks for a short code.

Loads all saved URLs and checks if the code exists.

Increments click count by 1 and saves the updated count back to the CSV file.

Prints the original URL and total clicks.

Asks if you want to open it; if you type y, opens the page using your web browser (webbrowser.open).

Prints an error message if the code isn't found.

list_urls() — Shows All Saved Links
Purpose: Prints a formatted table listing all stored short links, click stats, and original URLs.

How it works:

Loads all URLs from the CSV file.

If empty, warns that no URLs exist.

Otherwise, displays a formatted table showing each Code, Clicks, and Original URL.

main() — Interactive Menu Loop
Purpose: Runs the main program loop and presents a text menu.

How it works:

Displays options 1 to 4 in a loop (1. Shorten, 2. Find/Open, 3. List, 4. Exit).

Calls the appropriate function based on user input (1, 2, 3, or 4).

Stops the program if 4 is chosen.
