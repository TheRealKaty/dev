# What is this?

The github.dev web-based editor is a lightweight editing experience that runs entirely in your browser. You can navigate files and source code repositories from GitHub, and make and commit code changes.

There are two ways to go directly to a VS Code environment in your browser and start coding:

* Press the . key on any repository or pull request.
* Swap `.com` with `.dev` in the URL. For example, this repo https://github.com/github/dev becomes http://github.dev/github/dev

Preview the gif below to get a quick demo of github.dev in action.

![github dev](https://user-images.githubusercontent.com/856858/130119109-4769f2d7-9027-4b
c4-a38c-10f297499e8f.gif)

# Why?
It’s a quick way to edit and navigate code. It's especially useful if you want to edit multiple files at a time or take advantage of all the powerful code editing features of Visual Studio Code when making a quick change. For more information, see our [documentation](https://github.co/codespaces-editor-help).


from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
from reportlab.platypus import Table, TableStyle
from reportlab.lib import colors

def create_generic_statement_pdf(filename, data, account_info, summary):
    c = canvas.Canvas(filename, pagesize=letter)

    # Header
    c.drawString(50, 750, "Financial Institution Name")  # Generic name
    c.drawString(50, 730, "123 Generic Address")          # Generic address
    c.drawString(450, 750, f"Account Number: {account_info['number']}")
    c.drawString(450, 730, f"Statement Period: {account_info['period']}")

    # Table
    table = Table(data)
    # ... (Add table styling as shown in the previous example)
    table.wrapOn(c, 500, 500)
    table.drawOn(c, 50, 500)

    # Summary
    c.drawString(50, 300, f"Beginning Balance: ${summary['beginning']}")
    # ... (Add other summary details)

    c.save()

# Example data (replace with your generated data)
data = [
    ["Date", "Description", "Deposits", "Withdrawals"],
    ["2024-07-26", "ACH Deposit", "$500.00", "$0.00"],
    # ... more transactions
]
account_info = {"number": "1234567890", "period": "July 1, 2024 - July 31, 2024"}
summary = {"beginning": "1000.00"}

create_generic_statement_pdf("generic_statement.pdf", data, account_info, summary)
