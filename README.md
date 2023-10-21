# Student-grade-calculator
import java.util.Scanner;

public class StudentGradeCalculator1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of students: ");
        int numStudents = scanner.nextInt();

        int[] grades = new int[numStudents];
        int sum = 0;
        int highestGrade = Integer.MIN_VALUE;
        int lowestGrade = Integer.MAX_VALUE;
        int[] gradeCounts = new int[5];  // To store counts for each grade category

        System.out.println("Enter the grades for each student (0-100):");
        for (int i = 0; i < numStudents; i++) {
            System.out.print("Enter grade for student " + (i + 1) + ": ");
            grades[i] = scanner.nextInt();

            // Update sum, highest grade, and lowest grade
            sum += grades[i];
            if (grades[i] > highestGrade) {
                highestGrade = grades[i];
            }
            if (grades[i] < lowestGrade) {
                lowestGrade = grades[i];
            }

            // Categorize grades
            int gradeCategory = calculateGradeCategory(grades[i]);
            gradeCounts[gradeCategory]++;
        }

        // Calculate average grade
        double averageGrade = (double) sum / numStudents;

        // Display results
        System.out.println("Grade Summary:");
        System.out.println("Total number of students: " + numStudents);
        System.out.println("Average grade: " + averageGrade);
        System.out.println("Highest grade: " + highestGrade);
        System.out.println("Lowest grade: " + lowestGrade);

        // Display grade distribution
        String[] gradeCategories = {"A", "B", "C", "D", "F"};
        System.out.println("Grade distribution:");
        for (int i = 0; i < gradeCategories.length; i++) {
            System.out.println(gradeCategories[i] + ": " + gradeCounts[i]);
        }

        scanner.close();
    }

    private static int calculateGradeCategory(int grade) {
        if (grade >= 90) {
            return 0; // A
        } else if (grade >= 80) {
            return 1; // B
        } else if (grade >= 70) {
            return 2; // C
        } else if (grade >= 60) {
            return 3; // D
        } else {
            return 4; // F
        }
    }
}
