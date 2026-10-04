import java.util.ArrayList;
import java.util.Scanner;

class Student {
    int id;
    String name;
    int age;
    String course;
    double marks;

    Student(int id, String name, int age, String course, double marks) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.course = course;
        this.marks = marks;
    }

    void display() {
        System.out.println("--------------------------------");
        System.out.println("ID     : " + id);
        System.out.println("Name   : " + name);
        System.out.println("Age    : " + age);
        System.out.println("Course : " + course);
        System.out.println("Marks  : " + marks);
    }
}

public class StudentManagementSystem {

    static ArrayList<Student> students = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    // Add student
    static void addStudent() {
        System.out.print("Enter Student ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Student Name: ");
        String name = sc.nextLine();

        System.out.print("Enter Age: ");
        int age = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Course: ");
        String course = sc.nextLine();

        System.out.print("Enter Marks: ");
        double marks = sc.nextDouble();

        students.add(new Student(id, name, age, course, marks));

        System.out.println("Student added successfully!");
    }

    // View students
    static void viewStudents() {
        if (students.isEmpty()) {
            System.out.println("No students found.");
            return;
        }

        for (Student student : students) {
            student.display();
        }
    }

    // Search student
    static void searchStudent() {
        System.out.print("Enter Student ID: ");
        int id = sc.nextInt();

        for (Student student : students) {
            if (student.id == id) {
                student.display();
                return;
            }
        }

        System.out.println("Student not found.");
    }

    // Update student
    static void updateStudent() {
        System.out.print("Enter Student ID to update: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (Student student : students) {
            if (student.id == id) {

                System.out.print("Enter New Name: ");
                student.name = sc.nextLine();

                System.out.print("Enter New Age: ");
                student.age = sc.nextInt();
                sc.nextLine();

                System.out.print("Enter New Course: ");
                student.course = sc.nextLine();

                System.out.print("Enter New Marks: ");
                student.marks = sc.nextDouble();

                System.out.println("Student updated successfully!");
                return;
            }
        }

        System.out.println("Student not found.");
    }

    // Delete student
    static void deleteStudent() {
        System.out.print("Enter Student ID to delete: ");
        int id = sc.nextInt();

        for (Student student : students) {
            if (student.id == id) {
                students.remove(student);
                System.out.println("Student deleted successfully!");
                return;
            }
        }

        System.out.println("Student not found.");
    }

    public static void main(String[] args) {

        while (true) {

            System.out.println("\n===== STUDENT MANAGEMENT SYSTEM =====");
            System.out.println("1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Search Student");
            System.out.println("4. Update Student");
            System.out.println("5. Delete Student");
            System.out.println("6. Exit");

            System.out.print("Enter your choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    addStudent();
                    break;

                case 2:
                    viewStudents();
                    break;

                case 3:
                    searchStudent();
                    break;

                case 4:
                    updateStudent();
                    break;

                case 5:
                    deleteStudent();
                    break;

                case 6:
                    System.out.println("Thank you!");
                    sc.close();
                    return;

                default:
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }
}# student-management-system