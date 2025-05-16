class ShoppingCart:
    def __init__(self, customer_name):
        self.customer_name = customer_name
        self.items = []  # List to store (item_name, price, quantity)

    def add_item(self, item_name, price, quantity=1):
        self.items.append((item_name, price, quantity))
        print(f"✅ Added {quantity} x {item_name} to cart.")

    def remove_item(self, item_name):
        self.items = [item for item in self.items if item[0] != item_name]
        print(f"❌ Removed {item_name} from cart.")

    def view_cart(self):
        if not self.items:
            print("🛒 Your cart is empty.")
            return

        print(f"\n🧾 Cart for {self.customer_name}")
        for item_name, price, quantity in self.items:
            print(f"- {item_name}: ₹{price} x {quantity}")
        print(f"Total: ₹{self.calculate_total()}")

    def calculate_total(self):
        return sum(price * quantity for _, price, quantity in self.items)

    def apply_discount(self, percent):
        total = self.calculate_total()
        discounted_total = total - (total * percent / 100)
        print(f"🎉 After {percent}% discount: ₹{discounted_total:.2f}")
        return discounted_total



cart=ShoppingCart("xyz")
cart.add_item("Laptop", 600, 1)

cart.add_item("Laptop", 600, 2)
cart.add_item("Laptop", 600, 3)
cart.add_item("Laptop", 600, 4)

cart.view_cart()
cart.remove_item("Laptop")
cart.view_cart()

cart.apply_discount(10)
