# Unit-Converter-Using-Tkinter
import tkinter as tk
from tkinter import ttk

# Conversion functions
def convert():
    input_value = float(entry_value.get())
    input_unit = combo_input.get()
    output_unit = combo_output.get()

  #Conversion rates relative to meters
    conversions = {
        'Meters': 1,
        'Kilometers': 0.001,
        'Miles': 0.000621371,
        'Feet': 3.28084
    }
    
  #Convert input value to meters, then to the output unit
    value_in_meters = input_value / conversions[input_unit]
    converted_value = value_in_meters * conversions[output_unit]

  label_result.config(text=f"{converted_value:.4f} {output_unit}")

# Setting up the GUI
root = tk.Tk()
root.title("Unit Converter")

# Input value
label_value = tk.Label(root, text="Enter value:")
label_value.grid(row=0, column=0, padx=10, pady=10)

entry_value = tk.Entry(root)
entry_value.grid(row=0, column=1, padx=10, pady=10)

# Input unit
label_input = tk.Label(root, text="From:")
label_input.grid(row=1, column=0, padx=10, pady=10)

combo_input = ttk.Combobox(root, values=["Meters", "Kilometers", "Miles", "Feet"], state="readonly")
combo_input.grid(row=1, column=1, padx=10, pady=10)
combo_input.current(0)

# Output unit
label_output = tk.Label(root, text="To:")
label_output.grid(row=2, column=0, padx=10, pady=10)

combo_output = ttk.Combobox(root, values=["Meters", "Kilometers", "Miles", "Feet"], state="readonly")
combo_output.grid(row=2, column=1, padx=10, pady=10)
combo_output.current(1)

# Convert button
button_convert = tk.Button(root, text="Convert", command=convert)
button_convert.grid(row=3, column=0, columnspan=2, padx=10, pady=10)

# Result display
label_result = tk.Label(root, text="Result:", font=("Arial", 14))
label_result.grid(row=4, column=0, columnspan=2, padx=10, pady=20)

# Start the Tkinter event loop
root.mainloop()
