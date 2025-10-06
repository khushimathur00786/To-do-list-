# ----------------------------- TO-DO LIST APPLICATION -----------------------------
# This program allows the user to manage a list of tasks.
# The user can add, view, and remove tasks from the list.

# Function to display the main menu options
def display_menu():
    """Displays the main menu options to the user."""
    print("\n--- To-Do List Menu ---")      # Menu header
    print("1. Add Task")                   # Option 1: Add a new task
    print("2. View Tasks")                 # Option 2: Display all tasks
    print("3. Remove Task")                # Option 3: Delete a specific task
    print("4. Exit")                       # Option 4: Exit the program


# Function to add a new task to the list
def add_task(tasks, new_task):
    """Adds a new task to the list."""
    tasks.append(new_task)                 # Append the new task to the list
    print(f"Task '{new_task}' added.")     # Confirmation message


# Function to view all tasks in the list
def view_tasks(tasks):
    """Displays all tasks in the list."""
    if not tasks:                          # If the list is empty
        print("No tasks in the list.")     # Inform the user
    else:
        print("\n--- Your Tasks ---")      # Header for task list
        for i, task in enumerate(tasks):   # Loop through all tasks with their index
            print(f"{i + 1}. {task}")      # Display task number and name


# Function to remove a task from the list using its number
def remove_task(tasks, task_index):
    """Removes a task from the list by its index."""
    try:
        if 1 <= task_index <= len(tasks):          # Check if the entered index is valid
            removed_task = tasks.pop(task_index - 1)   # Remove task (list index starts from 0)
            print(f"Task '{removed_task}' removed.")   # Confirmation message
        else:
            print("Invalid task number.")              # Invalid number entered
    except ValueError:
        print("Invalid input. Please enter a number.") # Error handling for invalid input


# Main function that runs the program
def main():
    """Main function to run the To-Do List application."""
    tasks = []                                # Empty list to store all tasks

    while True:                               # Infinite loop to keep program running
        display_menu()                        # Show menu options each time
        choice = input("Enter your choice (1-4): ")  # Take user input for choice

        # Option 1: Add new task
        if choice == '1':
            task = input("Enter the task to add: ")   # Ask user for new task
            add_task(tasks, task)                     # Call function to add task

        # Option 2: View all tasks
        elif choice == '2':
            view_tasks(tasks)

        # Option 3: Remove a specific task
        elif choice == '3':
            view_tasks(tasks)                         # Show all tasks first
            if tasks:                                 # Proceed only if list is not empty
                try:
                    task_num_to_remove = int(input("Enter the number of the task to remove: "))
                    remove_task(tasks, task_num_to_remove)  # Call function to remove
                except ValueError:
                    print("Invalid input. Please enter a number.")  # Handle wrong input

        # Option 4: Exit program
        elif choice == '4':
            print("Exiting To-Do List. Goodbye!")      # Exit message
            break                                      # Stop the while loop

        # Invalid choice handling
        else:
            print("Invalid choice. Please enter a number between 1 and 4.")


# Entry point of the program
# This ensures the code runs only when the file is executed directly
if __name__ == "__main__":
    main()