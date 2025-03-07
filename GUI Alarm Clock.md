# GUI Alarm Clock using Tkinter

This project  alarm clock built using Tkinter in Python. It features a live digital clock display, an alarm-setting functionality, and plays a sound when the alarm time is reached.

## Prerequisites
- Install `pygame` for playing the alarm sound:
  ```sh
  pip install pygame
  ```
- Ensure you have an `alarm_sound.mp3` file in the same directory as the script.

## Code Explanation

```python
import tkinter as tk  # Importing Tkinter for GUI
from tkinter import messagebox  # Importing messagebox for pop-up alerts
import time  # Importing time module to get the current time
import datetime  # Importing datetime module for handling date and time
import pygame  # Importing pygame for playing alarm sound

# Initialize pygame mixer for alarm sound
pygame.mixer.init()
```
- `pygame.mixer.init()`: Initializes the mixer module in pygame to handle audio playback.

### Function to Play Alarm Sound
```python
def play_alarm_sound():
    pygame.mixer.music.load("alarm_sound.mp3")  # Load the alarm sound file
    pygame.mixer.music.play()  # Play the alarm sound
```
- This function loads and plays the alarm sound when triggered.

### Function to Update Clock Display
```python
def update_clock():
    current_time = time.strftime('%H:%M:%S')  # Get current time in HH:MM:SS format
    clock_label.config(text=current_time)  # Update the clock label with the current time
    clock_label.after(1000, update_clock)  # Refresh every second
    
    # Check if the alarm time matches the current time
    if alarm_time.get() == current_time:
        play_alarm_sound()
        messagebox.showinfo("Alarm", "Time to wake up!")  # Display an alert
```
- This function continuously updates the clock label every second.
- It also checks if the alarm time matches the current time and triggers the alarm sound.

### Function to Set Alarm Time
```python
def set_alarm():
    global alarm_time
    alarm_time.set(alarm_entry.get())  # Get user input from entry field
    messagebox.showinfo("Alarm Set", f"Alarm set for {alarm_time.get()}")  # Confirm alarm set
```
- This function retrieves the user-inputted alarm time and stores it in a variable.
- It then displays a confirmation message.

## GUI Setup
```python
root = tk.Tk()  # Initialize the main window
root.title("Colorful Alarm Clock")  # Set window title
root.geometry("400x300")  # Set window size
root.config(bg="#FFD700")  # Set background color

alarm_time = tk.StringVar()  # Variable to store the alarm time
```
- This sets up the main application window with a title, size, and background color.
- `alarm_time` is a Tkinter string variable to hold the alarm time.

### Digital Clock Display
```python
clock_label = tk.Label(root, font=("Arial", 40, "bold"), fg="white", bg="#FF4500")
clock_label.pack(pady=20)
update_clock()
```
- Creates a label to display the current time in a bold font with a colored background.
- Calls `update_clock()` to start the clock.

### Alarm Input Field
```python
alarm_entry = tk.Entry(root, font=("Arial", 20), justify='center')
alarm_entry.pack(pady=10)
alarm_entry.insert(0, "HH:MM:SS")
```
- Adds an input field for the user to enter the alarm time.
- Displays a placeholder text `HH:MM:SS`.

### Set Alarm Button
```python
set_button = tk.Button(root, text="Set Alarm", font=("Arial", 15), bg="#00FA9A", command=set_alarm)
set_button.pack(pady=10)
```
- Creates a button that, when clicked, calls the `set_alarm()` function.

### Run the Application
```python
root.mainloop()
```
- Starts the Tkinter event loop to keep the application running.

## Usage
1. Run the script.
2. Enter the alarm time in `HH:MM:SS` format.
3. Click "Set Alarm" to schedule the alarm.
4. When the time matches, a sound will play, and a pop-up will appear.

## Screenshot 
_Add a screenshot of the application interface here._

## License
This project is open-source and can be modified or distributed freely.
