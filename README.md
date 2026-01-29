# Student-management-
import java.util.*;

public class StudentManagementApp {

    public static void main(String[] args) {

        // 1. Store student objects in ArrayList
        List<Student> students = new ArrayList<>();
        students.add(new Student(101, "Pavi", 20, 85.5));
        students.add(new Student(102, "Arun", 21, 90.0));
        students.add(new Student(103, "Kavi", 19, 78.5));
        students.add(new Student(101, "Pavi", 20, 85.5)); // duplicate

        // 2. Remove duplicates using Set
        Set<Integer> uniqueIds = new HashSet<>();
        List<Student> uniqueStudents = new ArrayList<>();

        for (Student s : students) {
            if (uniqueIds.add(s.id)) {
                uniqueStudents.add(s);
            }
        }

        // 3. Use HashMap for fast lookup
        Map<Integer, Student> studentMap = new HashMap<>();
        for (Student s : uniqueStudents) {
            studentMap.put(s.id, s);
        }

        // 4. Sorting using Comparator (by marks descending)
        uniqueStudents.sort((s1, s2) -> Double.compare(s2.marks, s1.marks));

        // 5. Print formatted report
        System.out.println("ID    Name       Age   Marks");
        System.out.println("--------------------------------");
        for (Student s : uniqueStudents) {
            System.out.println(s);
        }

        // 6. Fast lookup demonstration
        System.out.println("\nLookup Student with ID 102:");
        System.out.println(studentMap.get(102));
    }
}
