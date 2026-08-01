#include <stdio.h>

struct Borewell {
    int id;
    char location[50];
    float depth;
    float waterLevel;
};

int main() {
    struct Borewell b[10];
    int n, i;
    float total = 0, average;

    printf("=====================================\n");
    printf("     GROUND WATER MANAGEMENT SYSTEM\n");
    printf("=====================================\n");

    printf("Enter the number of borewells: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++) {
        printf("\nEnter details of Borewell %d\n", i + 1);

        printf("Borewell ID: ");
        scanf("%d", &b[i].id);

        printf("Location: ");
        scanf("%s", b[i].location);

        printf("Depth (feet): ");
        scanf("%f", &b[i].depth);

        printf("Current Water Level (feet): ");
        scanf("%f", &b[i].waterLevel);

        total += b[i].waterLevel;
    }

    average = total / n;

    printf("\n=====================================\n");
    printf("      GROUND WATER REPORT\n");
    printf("=====================================\n");

    printf("\nID\tLocation\tDepth\tWater Level\tStatus\n");

    for(i = 0; i < n; i++) {
        printf("%d\t%s\t\t%.1f\t%.1f\t\t",
               b[i].id, b[i].location,
               b[i].depth, b[i].waterLevel);

        if(b[i].waterLevel <= 100)
            printf("Good\n");
        else if(b[i].waterLevel <= 200)
            printf("Moderate\n");
        else
            printf("Low\n");
    }

    printf("\nAverage Ground Water Level = %.2f feet\n", average);

    if(average <= 100)
        printf("Overall Status: Good Water Availability\n");
    else if(average <= 200)
        printf("Overall Status: Moderate Water Availability\n");
    else
        printf("Overall Status: Low Water Availability\n");

    printf("\nThank you for using the Ground Water Management System.\n");

    return 0;
}
