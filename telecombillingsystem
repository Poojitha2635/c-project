#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Structure to store user details
struct User {
    int userId;
    char name[100];
    char phoneNumber[15];
    float totalBill; // Total amount for the user
};

// Structure to store call records
struct Call {
    int userId;       // User associated with the call
    float duration;   // Duration of the call in minutes
    float cost;       // Cost for this call
};

// Function to calculate the call cost (rate is $0.10 per minute)
float calculateCallCost(float duration) {
    return duration * 0.10; // Example: $0.10 per minute
}

// Function to add a new user
void addUser(struct User users[], int *userCount) {
    printf("Enter User ID: ");
    scanf("%d", &users[*userCount].userId);
    getchar();  // To consume the newline character

    printf("Enter Name: ");
    fgets(users[*userCount].name, sizeof(users[*userCount].name), stdin);
    users[*userCount].name[strcspn(users[*userCount].name, "\n")] = '\0';  // Remove newline character

    printf("Enter Phone Number: ");
    fgets(users[*userCount].phoneNumber, sizeof(users[*userCount].phoneNumber), stdin);
    users[*userCount].phoneNumber[strcspn(users[*userCount].phoneNumber, "\n")] = '\0';  // Remove newline character

    users[*userCount].totalBill = 0.0;
    (*userCount)++;
    printf("User added successfully.\n");
}

// Function to add a call record
void addCall(struct Call calls[], int *callCount, int userId) {
    printf("Enter call duration (in minutes): ");
    float duration;
    scanf("%f", &duration);

    float cost = calculateCallCost(duration);

    calls[*callCount].userId = userId;
    calls[*callCount].duration = duration;
    calls[*callCount].cost = cost;
    (*callCount)++;

    printf("Call added successfully.\n");
}

// Function to generate and display a bill for a user
void generateBill(struct User users[], int userCount, struct Call calls[], int callCount, int userId) {
    float totalBill = 0.0;

    // Calculate total bill by summing the cost of calls made by the user
    for (int i = 0; i < callCount; i++) {
        if (calls[i].userId == userId) {
            totalBill += calls[i].cost;
        }
    }

    // Display user information and the bill
    printf("\nBill for User ID: %d\n", userId);
    for (int i = 0; i < userCount; i++) {
        if (users[i].userId == userId) {
            printf("Name: %s\n", users[i].name);
            printf("Phone Number: %s\n", users[i].phoneNumber);
            printf("Total Bill: $%.2f\n", totalBill);
            break;
        }
    }
}

// Function to display all users
void displayUsers(struct User users[], int userCount) {
    printf("\nUser List:\n");
    for (int i = 0; i < userCount; i++) {
        printf("User ID: %d, Name: %s, Phone: %s\n", users[i].userId, users[i].name, users[i].phoneNumber);
    }
}

// Main function to run the program
int main() {
    struct User users[100];  // Array to store users
    struct Call calls[500];  // Array to store call records
    int userCount = 0, callCount = 0;
    int choice, userId;

    while (1) {
        printf("\nTelecommunication Billing System\n");
        printf("1. Add User\n");
        printf("2. Add Call Record\n");
        printf("3. Generate Bill\n");
        printf("4. Display All Users\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addUser(users, &userCount);
                break;
            case 2:
                printf("Enter User ID to record the call: ");
                scanf("%d", &userId);
                addCall(calls, &callCount, userId);
                break;
            case 3:
                printf("Enter User ID to generate bill: ");
                scanf("%d", &userId);
                generateBill(users, userCount, calls, callCount, userId);
                break;
            case 4:
                displayUsers(users, userCount);
                break;
            case 5:
                printf("Exiting the program.\n");
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
