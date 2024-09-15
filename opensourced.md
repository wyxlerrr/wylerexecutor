Wyler is Open-Sourced, Please don't copy us.
import tkinter as tk
from tkinter import filedialog
from tkinter import messagebox

def open_file():
    # Open file dialog to select a Python file
    filepath = filedialog.askopenfilename(
        title="Select Python File",
        filetypes=[("Python Files", "*.py")]
    )
    
    if filepath:
        try:
            # Open and read the file
            with open(filepath, 'r') as file:
                file_contents = file.read()

            # Execute the file contents
            exec(file_contents)

            # Notify user of success
            messagebox.showinfo("Success", f"Executed script from {filepath}")
        except Exception as e:
            # If something goes wrong, show an error message
            messagebox.showerror("Error", f"An error occurred: {e}")

# Set up the GUI
root = tk.Tk()
root.title("Script Executor")
root.geometry("300x200")

# Create a button to open and execute the file
execute_button = tk.Button(root, text="Open and Execute File", command=open_file)
execute_button.pack(pady=20)

# Start the Tkinter main loop
root.mainloop()
