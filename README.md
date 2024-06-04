#include <stdio.h>

// Function to calculate CGPA
float calculateCGPA(int numCourses, float *grades, int *creditHours) {
    float totalCredits = 0;
    float totalGradePoints = 0;

    for (int i = 0; i < numCourses; i++) {
        totalGradePoints += grades[i] * creditHours[i];
        totalCredits += creditHours[i];
    }

    return totalGradePoints / totalCredits;
}

int main() {
    int numCourses;
    
    // Maximum number of courses supported by the program
    const int MAX_COURSES = 10;

    printf("Enter the number of courses: ");
    scanf("%d", &numCourses);

    // Validate the number of courses
    if (numCourses < 1 || numCourses > MAX_COURSES) {
        printf("Invalid number of courses. Please enter a number between 1 and %d\n", MAX_COURSES);
        return 1; // Exit the program with an error status
    }

    // Arrays to store grades and credit hours for each course
    float grades[MAX_COURSES];
    int creditHours[MAX_COURSES];

    // Input grades and credit hours for each course
    for (int i = 0; i < numCourses; i++) {
        printf("Enter grade for course %d (in GPA): ", i + 1);
        scanf("%f", &grades[i]);

        printf("Enter credit hours for course %d: ", i + 1);
        scanf("%d", &creditHours[i]);
    }

    // Calculate and display CGPA
    float cgpa = calculateCGPA(numCourses, grades, creditHours);
    printf("Your CGPA is: %.2f\n", cgpa);

    return 0;
}

                
           
