

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    struct telephone_number {
    int telephone;
    char name_of_person[39];
    char city[40];
    };

    int main() {

    int k;
    printf("Enter number of records you want to store: ");
    scanf("%d", &k);

    struct telephone_number telephone[k];
    int i, j, choice;
    struct telephone_number temp;

    while (1) {
        printf("\n====== MENU ======\n");
        printf("1. Add entries\n");
        printf("2. Display records\n");
        printf("3. Sort records by telephone\n");
        printf("4. Search by telephone\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {

            case 1:
                for (i = 0; i < k; i++) {
                    printf("\nEnter details for record %d\n", i + 1);
                    printf("Name: ");
                    scanf("%s", telephone[i].name_of_person);
                    printf("Telephone: ");
                    scanf("%d", &telephone[i].telephone);
                    printf("City: ");
                    scanf("%s", telephone[i].city);
                }
                break;

            case 2:
                printf("\n--- All Records ---\n");
                printf("%-20s %-12s %-20s\n", "Name", "Telephone", "City");
                printf("-----------------------------------------------------\n");

                for (i = 0; i < k; i++) {
                    printf("%-20s %-12d %-20s\n",
                           telephone[i].name_of_person,
                           telephone[i].telephone,
                           telephone[i].city);
                }
                break;

            case 3:
                // Bubble sort by telephone number
                for (i = 0; i < k - 1; i++) {
                    for (j = 0; j < k - i - 1; j++) {
                        if (telephone[j].telephone > telephone[j + 1].telephone) {
                            temp = telephone[j];
                            telephone[j] = telephone[j + 1];
                            telephone[j + 1] = temp;
                        }
                    }
                }

                printf("Records sorted successfully!\n");
                break;

            case 4: {
                int search_number;
                int found = 0;

                printf("Enter telephone number to search: ");
                scanf("%d", &search_number);

                for (i = 0; i < k; i++) {
                    if (telephone[i].telephone == search_number) {
                        printf("\nRecord found:\n");
                        printf("%-20s %-12d %-20s\n",
                               telephone[i].name_of_person,
                               telephone[i].telephone,
                               telephone[i].city);
                        found = 1;
                        break;
                    }
                }

                if (!found) {
                    printf("No record found with telephone number %d\n",
                           search_number);
                }
                break;
            }

            case 5:
                printf("Exiting program.\n");
                exit(0);

            default:
                printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
    }




