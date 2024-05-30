#include <stdio.h>
#include <string.h>

int number_subjects(int num_sub);

int main(void) {
    int class_grades[10];
    int credit_hrs[10];
    int num_sub;
    double grade_point[10];
    double gpa;
    char subject[10][10];
    char grade[10][10];
    char option;

    do {
        printf("\t*** GPA CALCULATOR ***\n\n");
        printf("Please choose an option:\n");
        printf("[a] Calculate GPA\n[q] Quit\n");
        scanf("%c", &option);

        switch (option) {
            case 'q':
                return 0;
            case 'a':
                num_sub = number_subjects(num_sub);
                break;
            default:
                printf("Not a valid choice\n");
                break;
        }

        for (int i = 0; i < num_sub; i++) {
            printf("\nClass %d\n", i + 1);
            printf("Class name: ");
            scanf("%s", subject[i]);
            printf("Enter grade: ");
            scanf("%d", &class_grades[i]);
            printf("Enter credit hours: ");
            scanf("%d", &credit_hrs[i]);

            // Conversion for grades
            if (class_grades[i] >= 95 && class_grades[i] <= 100) {
                grade_point[i] = 4.00;
                strcpy(grade[i], "A+");
            } else if (class_grades[i] >= 90 && class_grades[i] <= 94) {
                grade_point[i] = 4.00;
                strcpy(grade[i], "A");
            } else if (class_grades[i] >= 85 && class_grades[i] <= 89) {
                grade_point[i] = 3.33;
                strcpy(grade[i], "B+");
            }
            // ... other grade conversions ...

            // Calculate GPA
            double sum_gpaxcredit_hrs = grade_point[i] * credit_hrs[i];
            gpa += sum_gpaxcredit_hrs;
        }

        // Final GPA calculation
        double totalCreditHour = 0;
        for (int i = 0; i < num_sub; i++) {
            totalCreditHour += credit_hrs[i];
        }
        gpa /= totalCreditHour;

        // Display course information
        printf("\nCourse\tSubject\tGrade\tGrade Point\tLetter Grade\n");
        for (int i = 0; i < num_sub; i++) {
            printf("%d\t%s\t%d\t%.2f\t\t%s\n", i + 1, subject[i], class_grades[i], grade_point[i], grade[i]);
        }

    } while (1); // Loop to allow user to try again

    return 0;
}

int number_subjects(int num_sub) {
    printf("Enter the number of subjects: ");
    scanf("%d", &num_sub);
    return num_sub;
}
