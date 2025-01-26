# product-price-comparision-tool-
import tkinter as tk
from tkinter import messagebox
import random

# Mock function to simulate fetching prices from Amazon and Flipkart
def get_price_amazon(product_name):
    # Simulate a random price for Amazon (mocking a real fetch)
    return round(random.uniform(50000, 80000), 2)

def get_price_flipkart(product_name):
    # Simulate a random price for Flipkart (mocking a real fetch)
    return round(random.uniform(60000, 90000), 2)

# Function to compare prices from Amazon and Flipkart
def compare_prices():
    product_name = entry_product_name.get()

    if not product_name:
        messagebox.showerror("Input Error", "Please enter a product name.")
        return

    # Get the prices from both platforms (simulated)
    amazon_price = get_price_amazon(product_name)
    flipkart_price = get_price_flipkart(product_name)

    # Compare the prices
    if amazon_price < flipkart_price:
        cheaper_store = "Amazon"
        cheaper_price = amazon_price
    else:
        cheaper_store = "Flipkart"
        cheaper_price = flipkart_price

    # Display the result
    label_result.config(text=f"The cheapest price for '{product_name}' is from {cheaper_store}: ₹{cheaper_price:.2f}\n" f"Amazon Price: ₹{amazon_price:.2f}\n"f"Flipkart Price: ₹{flipkart_price:.2f}")

# Create the main window
root = tk.Tk()
root.title("Price Comparison Tool (Amazon vs Flipkart)")

# Create and place widgets (labels, entries, buttons)
label_title = tk.Label(root, text="Product Price Comparison (Amazon vs Flipkart)", font=("Helvetica", 16))
label_title.grid(row=0, column=0, columnspan=2, pady=10)

label_product_name = tk.Label(root, text="Product Name:")
label_product_name.grid(row=1, column=0, padx=10, pady=5, sticky="e")

entry_product_name = tk.Entry(root, width=30)
entry_product_name.grid(row=1, column=1, pady=5)

# Button to trigger comparison
button_compare = tk.Button(root, text="Compare Prices", command=compare_prices)
button_compare.grid(row=2, column=0, columnspan=2, pady=20)

# Label to show result
label_result = tk.Label(root, text="", font=("Helvetica", 12, "bold"))
label_result.grid(row=3, column=0, columnspan=2, pady=10)

# Start the Tkinter event loop
root.mainloop()
