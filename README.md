import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Task {
    private String name;
    private String description;
    private boolean completed;

    public Task(String name, String description) {
        this.name = name;
        this.description = description;
        this.completed = false;
    }

    public String getName() {
        return name;
    }

    public String getDescription() {
        return description;
    }

    public boolean isCompleted() {
        return completed;
    }

    public void setCompleted(boolean completed) {
        this.completed = completed;
    }
}

public class ToDoList {
    private List<Task> tasks;

    public ToDoList() {
        this.tasks = new ArrayList<>();
    }

    public void addTask(Task task) {
        tasks.add(task);
    }

    public void editTask(int index, Task updatedTask) {
        tasks.set(index, updatedTask);
    }

    public void deleteTask(int index) {
        tasks.remove(index);
    }

    public void displayTasks() {
        for (int i = 0; i < tasks.size(); i++) {
            Task task = tasks.get(i);
            System.out.println((i + 1) + ". " + task.getName() + " - " + task.getDescription() + " - " + (task.isCompleted() ? "Completed" : "Not Completed"));
        }
    }

    public static void main(String[] args) {
        ToDoList toDoList = new ToDoList();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add a task");
            System.out.println("2. Edit a task");
            System.out.println("3. Delete a task");
            System.out.println("4. Display tasks");
            System.out.println("5. Exit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter task name: ");
                    String name = scanner.next();
                    System.out.print("Enter task description: ");
                    String description = scanner.next();
                    Task task = new Task(name, description);
                    toDoList.addTask(task);
                    break;
                case 2:
                    toDoList.displayTasks();
                    System.out.print("Enter the task number to edit: ");
                    int editIndex = scanner.nextInt() - 1;
                    System.out.print("Enter new task name: ");
                    String newName = scanner.next();
                    System.out.print("Enter new task description: ");
                    String newDescription = scanner.next();
                    Task updatedTask = new Task(newName, newDescription);
                    toDoList.editTask(editIndex, updatedTask);
                    break;
                case 3:
                    toDoList.displayTasks();
                    System.out.print("Enter the task number to delete: ");
                    int deleteIndex = scanner.nextInt() - 1;
                    toDoList.deleteTask(deleteIndex);
                    break;
                case 4:
                    toDoList.displayTasks();
                    break;
                case 5:
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
