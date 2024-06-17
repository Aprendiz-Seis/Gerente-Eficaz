class Task:
    def __init__(self, title, description, due_date, responsible, status):
        self.title = title
        self.description = description
        self.due_date = due_date
        self.responsible = responsible
        self.status = status

class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def remove_task(self, task):
        self.tasks.remove(task)

    def update_task(self, task, new_title, new_description, new_due_date, new_responsible, new_status):
        task.title = new_title
        task.description = new_description
        task.due_date = new_due_date
        task.responsible = new_responsible
        task.status = new_status

    def get_tasks_by_status(self, status):
        return [task for task in self.tasks if task.status == status]

    def get_tasks_by_due_date(self, due_date):
        return [task for task in self.tasks if task.due_date == due_date]

    def get_tasks_by_responsible(self, responsible):
        return [task for task in self.tasks if task.responsible == responsible]

    def print_tasks(self):
        for task in self.tasks:
            print(f"Title: {task.title}")
            print(f"Description: {task.description}")
            print(f"Due Date: {task.due_date}")
            print(f"Responsible: {task.responsible}")
            print(f"Status: {task.status}")
            print("-" * 20)

# Example usage
task_manager = TaskManager()

task1 = Task("Create a new project", "Design and implement a new project management system.", "2024-06-20", "John Doe", "Pending")
task2 = Task("Review sales report", "Analyze sales data for the past quarter.", "2024-06-23", "Jane Smith", "In Progress")
task3 = Task("Schedule marketing meeting", "Organize and schedule a meeting with the marketing team.", "2024-06-25", "Peter Jones", "To Do")

task_manager.add_task(task1)
task_manager.add_task(task2)
task_manager.add_task(task3)

print("All tasks:")
task_manager.print_tasks()

print("\nTasks pending review:")
pending_tasks = task_manager.get_tasks_by_status("Pending")
for task in pending_tasks:
    print(f"Title: {task.title}")

print("\nTasks due on June 23rd:")
tasks_due_june_23rd = task_manager.get_tasks_by_due_date("2024-06-23")
for task in tasks_due_june_23rd:
    print(f"Title: {task.title}")

print("\nTasks assigned to Jane Smith:")
tasks_assigned_jane = task_manager.get_tasks_by_responsible("Jane Smith")
for task in tasks_assigned_jane:
    print(f"Title: {task.title}")

# Update task status
task_manager.update_task(task2, "Review sales report", "Analyze sales data for the past quarter and identify trends.", "2024-06-22", "Jane Smith", "Completed")

print("\nUpdated tasks:")
task_manager.print_tasks()
