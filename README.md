# CodeAlpha_StudentGradeTracker
//This is my internship assignment which is a console based student grade tracker made using Java in IntelliJ IDEA.
import java.util.ArrayList;
import java.util.Scanner;

class Student {
    String name;
    ArrayList<Integer> grades;

    Student(String name) {
        this.name = name;
        this.grades = new ArrayList<>();
    }

    double getAverage() {
        if (grades.isEmpty()) return 0;
        int total = 0;
        for (int g : grades) total += g;
        return (double) total / grades.size();
    }

    int getHighest() {
        if (grades.isEmpty()) return 0;
        int max = grades.get(0);
        for (int g : grades) if (g > max) max = g;
        return max;
    }

    int getLowest() {
        if (grades.isEmpty()) return 0;
        int min = grades.get(0);
        for (int g : grades) if (g < min) min = g;
        return min;
    }

    void displayReport() {
        System.out.println("Student: " + name);
        System.out.println("Grades: " + grades);
        System.out.printf("Average: %.2f\n", getAverage());
        System.out.println("Highest: " + getHighest());
        System.out.println("Lowest: " + getLowest());
        System.out.println("-----------------------------");
    }
}

public class StudentGradeTracker {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.print("Enter number of students: ");
        int numStudents = sc.nextInt();
        sc.nextLine(); // Consume newline

        for (int i = 0; i < numStudents; i++) {
            System.out.print("Enter student name: ");
            String name = sc.nextLine();
            Student student = new Student(name);

            System.out.print("Enter number of grades for " + name + ": ");
            int numGrades = sc.nextInt();

            for (int j = 0; j < numGrades; j++) {
                System.out.print("Enter grade " + (j + 1) + ": ");
                int grade = sc.nextInt();
                student.grades.add(grade);
            }
            sc.nextLine(); // Clear newline
            students.add(student);
        }

        System.out.println("\n=== Summary Report ===");
        for (Student student : students) {
            student.displayReport();
        }

        sc.close();
    }
}
