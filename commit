import tkinter as tk
import json

def add_task():
    task = task_entry.get()
    if task:
        tasks.append(task)
        update_task_list()
        task_entry.delete(0, tk.END)

def delete_task():
    selected_task = task_listbox.curselection()
    if selected_task:
        tasks.pop(selected_task[0])
        update_task_list()

def update_task_list():
    task_listbox.delete(0, tk.END)
    for task in tasks:
        task_listbox.insert(tk.END, task)

def save_tasks():
    with open("todo.json", "w") as file:
        json.dump(tasks, file)

def load_tasks():
    try:
        with open("todo.json", "r") as file:
            return json.load(file)
    except FileNotFoundError:
        return []

app = tk.Tk()
app.title("Simple Todo App")

tasks = load_tasks()

# UI Elements
task_entry = tk.Entry(app, width=40)
task_entry.pack(pady=5)

add_button = tk.Button(app, text="Add Task", command=add_task)
add_button.pack(pady=5)

task_listbox = tk.Listbox(app, width=50, height=15)
task_listbox.pack(pady=5)

delete_button = tk.Button(app, text="Delete Task", command=delete_task)
delete_button.pack(pady=5)

save_button = tk.Button(app, text="Save Tasks", command=save_tasks)
save_button.pack(pady=5)

update_task_list()
app.mainloop()
