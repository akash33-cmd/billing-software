# Retail Billing System

A simple web-based billing application for small retail stores, built with Flask and SQLite. Cashiers log in, scan or enter product barcodes, build a cart, take payment by cash or UPI, and get a bill. A summary of collections is shown on logout.

## Features

- Login-protected billing counter
- Add products to the cart by barcode
- Remove single items or clear the whole cart
- Cash payment with automatic balance calculation
- UPI payment support
- Unique bill number generated for every sale
- Sales saved in an SQLite database
- Session summary on logout: cash collected, UPI collected, total, and bills completed
- Sample products loaded automatically on first run

## Tech Stack

- Python 3
- Flask
- SQLite
- HTML templates (Jinja2)

## Project Structure

```
akash retails/
├── app.py
├── products.db
├── requirements.txt
└── templates/
    ├── login.html
    ├── index.html
    └── logout_summary.html
```

## Installation

1. Clone the repository

```bash
git clone https://github.com/akash33-cmd/billing-software.git
cd billing-software
```

2. Create and activate a virtual environment (optional)

```bash
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies

```bash
pip install flask
```

4. Run the app

```bash
python app.py
```

5. Open http://127.0.0.1:5000 in your browser.

## Configuration

Set these before running in a real environment:

| Setting | Purpose |
|---|---|
| SECRET_KEY | Secret used to protect Flask sessions (environment variable) |
| ADMIN_USERNAME | Login username (defined in app.py) |
| ADMIN_PASSWORD | Login password (defined in app.py) |

Change the default credentials and secret key before using the app anywhere other than your own machine.

## Sample Products

| Barcode | Product | Price |
|---|---|---|
| 1001 | Rice | 60.00 |
| 1002 | Milk | 30.00 |
| 1003 | Sugar | 50.00 |
| 1004 | Wheat | 45.00 |
| 1005 | Oil | 120.00 |
| 1006 | Biscuits | 20.00 |
| 1007 | Tea | 90.00 |
| 1008 | Coffee | 150.00 |

## How It Works

1. Log in with the admin credentials.
2. Enter a barcode and add it to the cart.
3. Choose Cash or UPI and complete the payment.
4. The bill is displayed with the bill number, items, total, and balance.
5. Log out to see the day's collection summary.

## Database Tables

**products**: id, barcode, name, price

**sales**: id, bill_number, total, payment_method, cash_received, balance, sale_time

## Routes

| Route | Method | Description |
|---|---|---|
| /login | GET, POST | Login page |
| / | GET, POST | Billing page, add items to cart |
| /payment | POST | Process payment and generate bill |
| /remove/&lt;index&gt; | GET | Remove an item from the cart |
| /clear | GET | Empty the cart |
| /logout | POST | End session and show summary |

## Future Improvements

- Add, edit, and delete products from the UI
- Sales history and reports
- Printable bills
- Multiple users with roles
- Quantity per item in the cart

## Author

Akash
