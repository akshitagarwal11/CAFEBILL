#include <stdio.h>

// Function to calculate the total price of items
float calculate_total_price(int quantity[], float unit_price[], int num_items) {
    float total = 0;
    for (int i = 0; i < num_items; i++) {
        total += quantity[i] * unit_price[i];
    }
    return total;
}

// Function to calculate the discount based on the total price
float calculate_discount(float total_price) {
    if (total_price < 1800) {
        return total_price * 0.05; // 5% discount
    } else if (total_price >= 1800 && total_price < 5000) {
        return total_price * 0.10; // 10% discount
    } else {
        return total_price * 0.15; // 15% discount
    }
}

// Function to display the invoice
void display_invoice(const char item_names[][50], int quantity[], float unit_price[], int num_items, float total_price, float discount) {
    printf("\n================ INVOICE ================\n");
    printf("Item Name\tQuantity\tUnit Price\tTotal Price\n");
    printf("-----------------------------------------\n");

    // Display details for each item
    for (int i = 0; i < num_items; i++) {
        printf("%-10s\t%d\t\t₹ %.2f\t\t₹ %.2f\n", 
               item_names[i], quantity[i], unit_price[i], quantity[i] * unit_price[i]);
    }

    printf("-----------------------------------------\n");
    printf("Total Price:\t\t\t\t₹ %.2f\n", total_price);
    printf("Discount:\t\t\t\t₹ %.2f\n", discount);
    printf("Final Price:\t\t\t\t₹ %.2f\n", total_price - discount);
    printf("=========================================\n");
}

int main() {
    int num_items = 7; // Predefined number of items

    // Predefined item names
    const char item_names[7][50] = {
        "Maggi",
        "Nuts Pkt",
        "Cold Drink",
        "Cadbury",
        "Ketchup Sauce",
        "Fruit Jam",
        "Wheat Pkt"
    };

    // Arrays to store quantities and unit prices
    int quantity[7];
    float unit_price[7];

    // Get quantity and unit price for each predefined item
    printf("Welcome to the Grocery Shop Billing System!\n");
    for (int i = 0; i < num_items; i++) {
        printf("\nEnter details for %s:\n", item_names[i]);

        // Input the quantity
        printf("Quantity: ");
        scanf("%d", &quantity[i]);

        // Input the unit price
        printf("Unit Price (₹): ");
        scanf("%f", &unit_price[i]);
    }

    // Calculate the total price
    float total_price = calculate_total_price(quantity, unit_price, num_items);

    // Calculate the discount
    float discount = calculate_discount(total_price);

    // Display the invoice
    display_invoice(item_names, quantity, unit_price, num_items, total_price, discount);

    return 0;
}
