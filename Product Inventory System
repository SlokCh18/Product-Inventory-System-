#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Structure to store product details
struct Product {
    int id;                 // Product ID
    char name[50];          // Product Name
    int quantity;           // Product Quantity
    float price;            // Product Price
    struct Product *next;   // Pointer to next node
};

// Head pointer for linked list
struct Product *head = NULL;

// Function to create a new product node
struct Product* createProduct(int id, char name[], int quantity, float price) {
    struct Product *newProduct = (struct Product*)malloc(sizeof(struct Product));
    newProduct->id = id;
    strcpy(newProduct->name, name);
    newProduct->quantity = quantity;
    newProduct->price = price;
    newProduct->next = NULL;
    return newProduct;
}

// Function to add a new product
void addProduct() {
    int id, quantity;
    float price;
    char name[50];

    printf("\nEnter Product ID: ");
    scanf("%d", &id);
    printf("Enter Product Name: ");
    scanf("%s", name);
    printf("Enter Quantity: ");
    scanf("%d", &quantity);
    printf("Enter Price: ");
    scanf("%f", &price);

    struct Product *newProduct = createProduct(id, name, quantity, price);

    if (head == NULL) {
        head = newProduct;  // If list is empty
    } else {
        struct Product *temp = head;
        while (temp->next != NULL)
            temp = temp->next;
        temp->next = newProduct;  // Add at the end
    }

    printf("\n✅ Product added successfully!\n");
}

// Function to display all products
void displayProducts() {
    if (head == NULL) {
        printf("\n❌ No products in the inventory.\n");
        return;
    }

    struct Product *temp = head;
    printf("\n%-10s %-20s %-10s %-10s\n", "ID", "Name", "Quantity", "Price");
    printf("--------------------------------------------------------\n");
    while (temp != NULL) {
        printf("%-10d %-20s %-10d %-10.2f\n", temp->id, temp->name, temp->quantity, temp->price);
        temp = temp->next;
    }
}

// Function to search a product by ID
void searchProduct() {
    int id;
    printf("\nEnter Product ID to search: ");
    scanf("%d", &id);

    struct Product *temp = head;
    while (temp != NULL) {
        if (temp->id == id) {
            printf("\n✅ Product Found:\n");
            printf("ID: %d\nName: %s\nQuantity: %d\nPrice: %.2f\n",
                   temp->id, temp->name, temp->quantity, temp->price);
            return;
        }
        temp = temp->next;
    }

    printf("\n❌ Product not found.\n");
}

// Function to update product details
void updateProduct() {
    int id;
    printf("\nEnter Product ID to update: ");
    scanf("%d", &id);

    struct Product *temp = head;
    while (temp != NULL) {
        if (temp->id == id) {
            printf("\nEnter new Quantity: ");
            scanf("%d", &temp->quantity);
            printf("Enter new Price: ");
            scanf("%f", &temp->price);
            printf("\n✅ Product details updated successfully!\n");
            return;
        }
        temp = temp->next;
    }

    printf("\n❌ Product not found.\n");
}

// Function to delete a product
void deleteProduct() {
    int id;
    printf("\nEnter Product ID to delete: ");
    scanf("%d", &id);

    struct Product *temp = head, *prev = NULL;

    if (temp != NULL && temp->id == id) {
        head = temp->next;
        free(temp);
        printf("\n✅ Product deleted successfully!\n");
        return;
    }

    while (temp != NULL && temp->id != id) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL) {
        printf("\n❌ Product not found.\n");
        return;
    }

    prev->next = temp->next;
    free(temp);
    printf("\n✅ Product deleted successfully!\n");
}

// Function to calculate total inventory value
void totalInventoryValue() {
    float total = 0;
    struct Product *temp = head;
    while (temp != NULL) {
        total += temp->quantity * temp->price;
        temp = temp->next;
    }
    printf("\n💰 Total Inventory Value: %.2f\n", total);
}

// Main function with menu
int main() {
    int choice;
    while (1) {
        printf("\n===== PRODUCT INVENTORY MANAGEMENT SYSTEM =====\n");
        printf("1. Add Product\n");
        printf("2. Display All Products\n");
        printf("3. Search Product\n");
        printf("4. Update Product\n");
        printf("5. Delete Product\n");
        printf("6. Total Inventory Value\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: addProduct(); break;
            case 2: displayProducts(); break;
            case 3: searchProduct(); break;
            case 4: updateProduct(); break;
            case 5: deleteProduct(); break;
            case 6: totalInventoryValue(); break;
            case 7:
                printf("\n👋 Exiting Product Inventory System...\n");
                exit(0);
            default:
                printf("\n⚠️ Invalid choice! Please try again.\n");
        }
    }
    return 0;
}
