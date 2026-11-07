# python--calculator-Link-
PYTHON CALCULATOR
"""
Advanced Calculator with History
A beginner-intermediate Python project.

Features:
- Basic math operations
- Stores calculation history
- Clean error handling
"""

from datetime import datetime

# List to store calculation history
history = []


def calculate(num1, num2, operation):
    """Perform calculation and return result."""
    if operation == "+":
        return num1 + num2
    elif operation == "-":
        return num1 - num2
    elif operation == "*":
        return num1 * num2
    elif operation == "/":
        if num2 == 0:
            return "Error: Cannot divide by zero!"
        return num1 / num2
    return None


def show_history():
    """Display all past calculations."""
    if not history:
        print("\n📭 No history yet.")
        return

    print("\n📜 Calculation History:")
    print("-" * 40)
    for i, entry in enumerate(history, 1):
        print(f"{i}. {entry}")
    print("-" * 40)


def main():
    print("=" * 40)
    print("   ADVANCED CALCULATOR v2.0")
    print("=" * 40)

    operations = {"1": "+", "2": "-", "3": "*", "4": "/"}

    while True:
        print("\n📌 Menu:")
        print("1. Add (+)")
        print("2. Subtract (-)")
        print("3. Multiply (*)")
        print("4. Divide (/)")
        print("5. View History")
        print("6. Clear History")
        print("7. Exit")

        choice = input("\nEnter choice (1-7): ")

        if choice == "7":
            print("Goodbye! 👋")
            break

        if choice == "5":
            show_history()
            continue

        if choice == "6":
            history.clear()
            print("🗑️  History cleared!")
            continue

        if choice not in operations:
            print("❌ Invalid choice.")
            continue

        try:
            num1 = float(input("Enter first number: "))
            num2 = float(input("Enter second number: "))
        except ValueError:
            print("❌ Please enter valid numbers only.")
            continue

        operation = operations[choice]
        result = calculate(num1, num2, operation)

        entry = f"{num1} {operation} {num2} = {result}"
        history.append(entry)

        timestamp = datetime.now().strftime("%H:%M:%S")
        print(f"\n✅ [{timestamp}] Result: {entry}")


if __name__ == "__main__":
    main()
