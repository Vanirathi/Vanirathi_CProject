# Vanirathi_CProject
#include <stdio.h>
#include <string.h>

char calculateGrade(float marks) {
    if (marks >= 90)
        return 'A';
    else if (marks >= 80)
        return 'B';
    else if (marks >= 70)
        return 'C';
    else if (marks >= 60)
        return 'D';
    else
        return 'F';
}

int main () {
    char name[50];
    int rollNo;
    char section;
    float marks[5];
    float total = 0, average, attendance;
    int i;
    const char *subjects[5] = {"MATHEMATICS", "PHYSICS", "CHEMISTRY", "BIOLOGY", "ENGLISH"};

    printf("Enter student's name: ");
    scanf("%s", name);

    printf("\nEnter roll number: ");
    scanf("%d", &rollNo);

    printf("\nEnter section (A, B, or C): ");
    scanf(" %c", &section);
    if (section != 'A' && section != 'B' && section != 'C') {
        printf("Error: Invalid section entered. Please restart the program.\n");
        return 0;
    }

    printf("\nEnter attendance percentage: ");
    scanf("%f", &attendance);
    if (attendance < 0 || attendance > 100) {
        printf("Error: Attendance must be between 0 and 100. Please restart the program.\n");
        return 0;
    }

    for (i = 0; i < 5; i++) {
        printf("\nEnter marks for %s (out of 100): ", subjects[i]);
        scanf("%f", &marks[i]);

        if (marks[i] < 0 || marks[i] > 100) {
            printf("Error: Marks must be between 0 and 100. Please restart the program.\n");
            return 0;
        }
        total += marks[i];
    }

    average = total / 5;

    printf("\n\n==================== Report Card ====================\n");
    printf("Name: %s\n", name);
    printf("Roll Number: %d\n", rollNo);
    printf("Class: XII\n");
    printf("Section: %c\n", section);
    printf("Attendance: %.2f%%\n", attendance);

    printf("-----------------------------------------------------\n");
    printf("Subjects         Marks   Grade\n");
    printf("-----------------------------------------------------\n");

    for (i = 0; i < 5; i++) {
        printf("%-16s   %.2f   %c\n", subjects[i], marks[i], calculateGrade(marks[i]));
    }

    printf("-----------------------------------------------------\n");
    printf("Total Marks:      %.2f\n", total);
    printf("Average Marks:    %.2f\n", average);

    char averageGrade = calculateGrade(average);
    printf("Grade: %c\n", averageGrade);


    if (attendance < 75) {
        printf("Result: Debarred due to low attendance\n");
    } else if (averageGrade != 'F') {
        printf("Result: Pass\n");
    } else {
        printf("Result: Fail\n");
    }

    printf("=====================================================\n");

    return 0;
}
