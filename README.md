# Calculator-python
code for GUI Calculator using Python
import tkinter as tk

# Function to update the expression when a button is clicked
def button_click(event):
    text = event.widget.cget("text")

    if text == "=":
        try:
            result = str(eval(screen.get()))
            screen.delete(0, tk.END)
            screen.insert(tk.END, result)
        except Exception as e:
            screen.delete(0, tk.END)
            screen.insert(tk.END, "Error")
    elif text == "C":
        screen.delete(0, tk.END)
    else:
        screen.insert(tk.END, text)

# Create a GUI window
root = tk.Tk()
root.title("Calculator")

# Create an entry field for the expression
screen = tk.Entry(root, font=("Arial", 20))
screen.pack(fill=tk.BOTH, expand=True, padx=10, pady=10, ipadx=10, ipady=10)

# Create buttons for the calculator
button_frame = tk.Frame(root)
button_frame.pack()

buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    'C', '0', '=', '+'
]

row, col = 0, 0
for button_text in buttons:
    button = tk.Button(button_frame, text=button_text, font=("Arial", 20), padx=20, pady=20)
    button.grid(row=row, column=col, padx=5, pady=5)
    button.bind("<Button-1>", button_click)  # Bind the click event to the button
    col += 1
    if col > 3:
        col = 0
        row += 1

root.mainloop()
