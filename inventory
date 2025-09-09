def process_sale(inventory, sku, qty_sold):
    """
    Processes a sale by reducing inventory for the given SKU.

    Args:
        inventory (list of tuples): [(SKU, quantity), ...]
        sku (int): SKU identifier to process sale
        qty_sold (int): Quantity sold

    Returns:
        updated_inventory (list of tuples)
    """
    updated_inventory = []
    sku_found = False

    for current_sku, current_qty in inventory:
        if current_sku == sku:
            sku_found = True
            if current_qty >= qty_sold:
                updated_inventory.append((current_sku, current_qty - qty_sold))
                print(f"Sale processed: {qty_sold} units of SKU {sku}.")
            else:
                updated_inventory.append((current_sku, current_qty))
                print(f"Insufficient stock for SKU {sku}. Available: {current_qty}")
        else:
            updated_inventory.append((current_sku, current_qty))

    if not sku_found:
        print(f"SKU {sku} not found in inventory.")

    return updated_inventory


def identify_zero_stock(inventory):
    """
    Identify all SKUs with zero stock.

    Args:
        inventory (list of tuples): [(SKU, quantity), ...]

    Returns:
        zero_stock_list (list of int): SKUs with zero quantity
    """
    zero_stock_list = [sku for sku, qty in inventory if qty == 0]
    if zero_stock_list:
        print(f"Zero stock SKUs: {zero_stock_list}")
    else:
        print("No zero stock items found.")
    return zero_stock_list


def input_inventory():
    """
    Takes user input to create inventory list.

    Returns:
        inventory (list of tuples): [(SKU, quantity), ...]
    """
    inventory = []
    print("\nEnter inventory data (type 'done' to finish):")
    while True:
        raw = input("Enter SKU and quantity (e.g., 101 50): ")
        if raw.lower() == 'done':
            break
        try:
            sku, qty = map(int, raw.strip().split())
            inventory.append((sku, qty))
        except ValueError:
            print("Invalid input. Please enter SKU and quantity separated by space.")
    return inventory


def main():
    print("=== Inventory Management System ===")
    inventory = input_inventory()

    while True:
        print("\n--- Menu ---")
        print("1. Process Sale")
        print("2. Identify Zero Stock Items")
        print("3. Show Inventory")
        print("4. Exit")
        choice = input("Enter your choice (1-4): ").strip()

        if choice == '1':
            try:
                sku = int(input("Enter SKU to sell: "))
                qty = int(input("Enter quantity to sell: "))
                inventory = process_sale(inventory, sku, qty)
            except ValueError:
                print("Invalid input. Please enter numeric values.")
        elif choice == '2':
            identify_zero_stock(inventory)
        elif choice == '3':
            print("Current Inventory:")
            for sku, qty in inventory:
                print(f"SKU: {sku}, Quantity: {qty}")
        elif choice == '4':
            print("Exiting. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 4.")


if __name__ == "__main__":
    main()
