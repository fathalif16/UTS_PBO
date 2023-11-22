public class Student {
 private String name;
 private int age;
 public Student(String name, int age) {
 this.name = name;
 this.age = age;
 }
 public String getName() {
 return name;
 }
 public int getAge() {
 return age;
 }
}
import java.util.ArrayList;
import java.util.List;
public class StudentModel {
 private List<Student> students = new ArrayList<>();
 public void addStudent(Student student) {
 students.add(student);
 }
 public List<Student> getStudents() {
 return students;
 }
}
import java.util.List;
public class StudentView {
 public void displayStudents(List<Student> students) {
 System.out.println("List of Students:");
 for (Student student : students) {
 System.out.println("Name: " + student.getName() + ", Age: " + 
student.getAge());
 }
 }
}
import java.util.List;
public class StudentController {
 private StudentModel model;
 private StudentView view;
 public StudentController(StudentModel model, StudentView view) {
 this.model = model;
 this.view = view;
 }
 public void addStudent(String name, int age) {
 Student student = new Student(name, age);
 model.addStudent(student);
 }
 public void displayStudents() {
 List<Student> students = model.getStudents();
 view.displayStudents(students);
 }
}
import java.util.Scanner;
class Main {
 public static void main(String[] args) {
 StudentModel model = new StudentModel();
 StudentView view = new StudentView();
 StudentController controller = new StudentController(model, view);
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter the number of students: ");
 int numberOfStudents = scanner.nextInt();
 for (int i = 0; i < numberOfStudents; i++) {
 System.out.print("Enter student name: ");
 String name = scanner.next();
 System.out.print("Enter student age: ");
 int age = scanner.nextInt();
 controller.addStudent(name, age);
 }
 controller.displayStudents();
 scanner.close();
 }
}
