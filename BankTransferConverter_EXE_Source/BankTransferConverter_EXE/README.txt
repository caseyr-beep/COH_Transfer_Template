HOLYOKE BANK TRANSFER CONVERTER - WINDOWS EXE

WHAT END USERS NEED
-------------------
Once HolyokeTransferConverter.exe has been built, end users do NOT need Python.
They only need the EXE.

EASIEST WAY TO BUILD THE EXE WITHOUT INSTALLING PYTHON LOCALLY
--------------------------------------------------------------
Use GitHub Actions:

1. Create a private GitHub repository.
2. Upload all files and folders in this package, including the hidden .github folder.
3. Commit the files to the main branch.
4. Open the repository's Actions tab.
5. Choose "Build Windows EXE".
6. Click "Run workflow" if it has not already run automatically.
7. When it finishes, open the completed workflow run.
8. Download the artifact named "HolyokeTransferConverter-Windows".
9. Unzip the artifact. Inside is HolyokeTransferConverter.exe.
10. Put the EXE on a shared drive or distribute it to staff.

No Python installation is required for the users who run the EXE.

ALTERNATE BUILD METHOD
----------------------
If one Windows computer has Python installed, double-click build_windows.bat.
The finished EXE will be created at:
    dist\HolyokeTransferConverter.exe

HOW THE APP WORKS
-----------------
1. Double-click HolyokeTransferConverter.exe.
2. Browse to the raw bank transfer CSV.
3. Browse to the bank-code mapping workbook.
4. Choose an output Excel file.
5. Optionally enter additional scrub pairs, one per line, e.g.:
       1111,2222
6. Click Convert.

BUILT-IN RULES
--------------
- Uses Will Process On as transaction date.
- Date output is mm-dd-yyyy with no timestamp.
- Description is TRANSFER FROM [CODE] TO [CODE].
- TRANSFER FROM is negative.
- TRANSFER TO is positive.
- Debit row comes first, credit row second.
- Each pair nets to zero.
- Column D = TRANSFER.
- Column G = signed transfer amount.
- Column K = signed transfer amount.
- Column L = bank code.
- Negative amounts are red; positive amounts are black.
- Output is split into monthly tabs.
- Scrubs transfers between 1171 and 1220.
- Scrubs transfers between 1171 and 1270.
- Scrubs transfers where both sides are among 7189, 4237, and 4245.
- The app reports any 4-digit account that does not have a bank-code mapping.

BANK CODE WORKBOOK FORMATS
--------------------------
The app accepts either:

A. Horizontal format:
   Row 1 = Bank
   Row 2 = Account number
   Row 3 = Bank code

B. Simple two-column format:
   Account (Last 4) | Bank Code
