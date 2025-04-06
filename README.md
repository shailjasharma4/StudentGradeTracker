import java.util.ArrayList;
import java.util.Scanner;

public class StudentGradeTracker {
    public static void main(String[] args) {
        ArrayList<Integer> grades = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n--- Student Grade Tracker ---");
            System.out.println("1. Enter a new grade");
            System.out.println("2. Show all grades");
            System.out.println("3. Calculate average grade");
            System.out.println("4. Show highest grade");
            System.out.println("5. Show lowest grade");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter student grade (0-100): ");
                    int grade = scanner.nextInt();
                    if (grade >= 0 && grade <= 100) {
                        grades.add(grade);
                        System.out.println("Grade added.");
                    } else {
                        System.out.println("Invalid grade. Please enter a value between 0 and 100.");
                    }
                    break;
                case 2:
                    System.out.println("All Grades: " + grades);
                    break;
                case 3:
                    if (!grades.isEmpty()) {
                        double avg = calculateAverage(grades);
                        System.out.println("Average Grade: " + avg);
                    } else {
                        System.out.println("No grades entered yet.");
                    }
                    break;
                case 4:
                    if (!grades.isEmpty()) {
                        int max = findHighest(grades);
                        System.out.println("Highest Grade: " + max);
                    } else {
                        System.out.println("No grades entered yet.");
                    }
                    break;
                case 5:
                    if (!grades.isEmpty()) {
                        int min = findLowest(grades);
                        System.out.println("Lowest Grade: " + min);
                    } else {
                        System.out.println("No grades entered yet.");
                    }
                    break;
                case 6:
                    System.out.println("Exiting program. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Try again.");
            }
        } while (choice != 6);

        scanner.close();
    }

    public static double calculateAverage(ArrayList<Integer> grades) {
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return (double) sum / grades.size();
    }

    public static int findHighest(ArrayList<Integer> grades) {
        int max = grades.get(0);
        for (int grade : grades) {
            if (grade > max) {
                max = grade;
            }
        }
        return max;
    }

    public static int findLowest(ArrayList<Integer> grades) {
        int min = grades.get(0);
        for (int grade : grades) {
            if (grade < min) {
                min = grade;
            }
        }
        return min;
    }
}
