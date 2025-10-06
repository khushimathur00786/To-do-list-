# To-do-list-
def display_menu():
    """Displays the main menu options to the user."""
    print("\n--- To-Do List Menu ---")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Remove Task")
    print("4. Exit")

def add_task(tasks, new_task):
    """Adds a new task to the list."""
    tasks.append(new_task)
    print(f"Task '{new_task}' added.")

def view_tasks(tasks):
    """Displays all tasks in the list."""
    if not tasks:
        print("No tasks in the list.")
    else:
        print("\n--- Your Tasks ---")
        for i, task in enumerate(tasks):
            print(f"{i + 1}. {task}")

def remove_task(tasks, task_index):
    """Removes a task from the list by its index."""
    try:
        if 1 <= task_index <= len(tasks):
            removed_task = tasks.pop(task_index - 1)
            print(f"Task '{removed_task}' removed.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def main():
    """Main function to run the To-Do List application."""
    tasks = []
    while True:
        display_menu()
        choice = input("Enter your choice (1-4): ")

        if choice == '1':
            task = input("Enter the task to add: ")
            add_task(tasks, task)
        elif choice == '2':
            view_tasks(tasks)
        elif choice == '3':
            view_tasks(tasks) # Show tasks before asking for removal
            if tasks:
                try:
                    task_num_to_remove = int(input("Enter the number of the task to remove: "))
                    remove_task(tasks, task_num_to_remove)
                except ValueError:
                    print("Invalid input. Please enter a number.")
        elif choice == '4':
            print("Exiting To-Do List. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 4.")

if __name__ == "__main__":
    main()
