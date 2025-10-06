# -------------------------------
# To-Do List App (Console Version)
# -------------------------------

# This project helps users manage daily tasks
# It includes features to add, view, remove, and mark tasks as completed

# Step 1: Define an empty list to store tasks
tasks = []

# Step 2: Define a function to display the menu
def display_menu():
    """Displays menu options for the user."""
    print("\n====== TO-DO LIST MENU ======")
    print("1. Add a Task")
    print("2. View All Tasks")
    print("3. Remove a Task")
    print("4. Mark Task as Completed")
    print("5. Exit")

# Step 3: Define a function to add a new task
def add_task():
    """Adds a new task entered by the user."""
    task = input("Enter the new task: ")
    tasks.append({"task": task, "completed": False})  # Store as dictionary with completion status
    print(f"✅ Task '{task}' added successfully!")

# Step 4: Define a function to view all tasks
def view_tasks():
    """Displays all tasks with their completion status."""
    if not tasks:
        print("No tasks found. Add some tasks first!")
        return
    print("\nYour Tasks:")
    for i, t in enumerate(tasks, 1):
        status = "✔️ Completed" if t["completed"] else "❌ Not Completed"
        print(f"{i}. {t['task']} - {status}")

# Step 5: Define a function to remove a task
def remove_task():
    """Removes a task based on its number."""
    view_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to remove: "))
        removed = tasks.pop(task_num - 1)
        print(f"🗑️ Task '{removed['task']}' removed successfully!")
    except (ValueError, IndexError):
        print("⚠️ Invalid input! Please enter a valid task number.")

# Step 6: Define a function to mark task as completed
def mark_completed():
    """Marks a selected task as completed."""
    view_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to mark as completed: "))
        tasks[task_num - 1]["completed"] = True
        print(f"🎉 Task '{tasks[task_num - 1]['task']}' marked as completed!")
    except (ValueError, IndexError):
        print("⚠️ Invalid input! Please enter a valid task number.")

# Step 7: Main program loop
while True:
    display_menu()
    choice = input("Enter your choice (1-5): ")

    if choice == "1":
        add_task()
    elif choice == "2":
        view_tasks()
    elif choice == "3":
        remove_task()
    elif choice == "4":
        mark_completed()
    elif choice == "5":
        print("👋 Exiting To-Do List... Have a productive day!")
        break
    else:
        print("⚠️ Invalid choice! Please enter a number between 1 and 5.")
