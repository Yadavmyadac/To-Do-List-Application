# To-Do-List-Application
Basic command-line To-Do List application that allows users to add, remove, view, and mark tasks as complete.

# Define a list to store tasks
tasks = []

# Function to display the menu
def show_menu():
    print("\nTo-Do List Application")
    print("1. Add a Task")
    print("2. View Tasks")
    print("3. Remove a Task")
    print("4. Mark Task as Complete")
    print("5. Exit")

# Function to add a task
def add_task():
    task = input("Enter the task: ")
    tasks.append({"task": task, "completed": False})
    print(f"Task '{task}' added!")

# Function to view tasks
def view_tasks():
    if not tasks:
        print("No tasks to display.")
    else:
        for i, task in enumerate(tasks, 1):
            status = "Completed" if task["completed"] else "Pending"
            print(f"{i}. {task['task']} - {status}")

# Function to remove a task
def remove_task():
    view_tasks()
    try:
        task_number = int(input("Enter the task number to remove: "))
        if 1 <= task_number <= len(tasks):
            removed_task = tasks.pop(task_number - 1)
            print(f"Task '{removed_task['task']}' removed!")
        else:
            print("Invalid task number!")
    except ValueError:
        print("Please enter a valid number.")

# Function to mark a task as complete
def mark_complete():
    view_tasks()
    try:
        task_number = int(input("Enter the task number to mark as complete: "))
        if 1 <= task_number <= len(tasks):
            tasks[task_number - 1]["completed"] = True
            print(f"Task '{tasks[task_number - 1]['task']}' marked as complete!")
        else:
            print("Invalid task number!")
    except ValueError:
        print("Please enter a valid number.")

# Main program loop
def main():
    while True:
        show_menu()
        choice = input("Choose an option: ")

        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            remove_task()
        elif choice == "4":
            mark_complete()
        elif choice == "5":
            print("Exiting the application...")
            break
        else:
            print("Invalid choice. Please try again.")

# Run the program
if __name__ == "__main__":
    main()
