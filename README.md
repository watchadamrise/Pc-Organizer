# These instructions are written very detailed for people like me that are just starting out and don't know all the jargan and lingo used. I struggled a lot in the beginning with things that would be written as if it were common sense. But I was not privvy to such knowledge until i started this journey. It would fill me with such self doubt and frustration. I'd like to help anyone avoid that if possible. 

# Windows only 
#### I Don't know linux or other OS's well enough to put my name on anything there yet.
# Pc-Organizer

This Python script helps you move files from one folder to another based on their file type (like videos, pictures, etc.). You can easily customize which types of files you want to move. Best for external drives.


## What This Script Does

- The script looks at all the files in a folder you choose.
- It moves specific types of files (like `.mp4` videos or `.jpg` images) to another folder you choose.
- You can decide which types of files you want to move by changing a simple list in the script.

# **Important Disclaimer**

**Warning:** This script should not be used on your main system drive (usually the `C:` drive), or in any critical system folders. Moving files from these areas can cause your computer to stop working properly or result in data loss.

**Avoid using this script on the following:**
- **`C:\Windows`**: This is where your operating system files are stored.
- **`C:\Program Files` and `C:\Program Files (x86)`**: These folders contain installed software.
- **`C:\Users\YourName\AppData`**: This folder stores important settings and data for your programs.
- **System folders or drives**: Any folder that contains important files needed by your computer to run properly.

Always double-check the folder you are targeting to make sure it does not contain critical system files.

## Step-by-Step Instructions

### Step 1: Install Python

**Python is a program that allows you to run scripts like this one. Here's how to install it:**

1. **Open your web browser:** Click the "Start" button (the Windows logo in the bottom left corner) and type "Chrome" or "Edge" to open your web browser.
   
2. **Go to the Python website:** Type [python.org](https://www.python.org/) in the address bar and press "Enter".
   
3. **Download Python:**
   - On the Python homepage, find the yellow button that says "Download Python".
   - Click on it to start downloading the Python installer.
   
4. **Install Python:**
   - Once the download is finished, go to your "Downloads" folder and find the file that starts with "python".
   - Double-click on this file to open the installer.
   - **Important:** On the first screen, check the box that says "Add Python to PATH".
   - Then click "Install Now" and follow the instructions on the screen. This will take a few minutes.
   - 
****you should know what folder you're moving to or should create one now.****

### Step 2: Save the Script

**A script is a set of instructions that tells your computer what to do. Here's how to save this script:**

1. **Open Notepad:**
   - Click the "Start" button and type "Notepad". Press "Enter" to open it.

2. **Copy the Script:**
   - Copy the script below by selecting the text and pressing `Ctrl + C` on your keyboard.

   ```python
   import os
   import shutil

   # Specify the source and destination folders
   source_folder = 'E:\\Sorted Files'  # Change this to your source folder
   destination_folder = 'E:\\Moved Files'  # Change this to your destination folder

   # List of file extensions to move
   file_extensions = ['.mp4', '.jpg', '.png', '.avi', '.mkv']  # Add or remove extensions as needed

   # Create the destination folder if it does not exist
   if not os.path.exists(destination_folder):
       os.makedirs(destination_folder)

   # Walk through the directory tree
   for root, dirs, files in os.walk(source_folder):
       for file in files:
           if any(file.lower().endswith(ext) for ext in file_extensions):
               source_file = os.path.join(root, file)
               destination_file = os.path.join(destination_folder, file)
               try:
                   shutil.move(source_file, destination_file)
                   print(f'Moved: {source_file} -> {destination_file}')
               except Exception as e:
                   print(f'Error moving file {source_file}: {e}')

   print('All specified files have been moved!')

3. **Paste the Script:**

-Go back to Notepad and paste the script by pressing Ctrl + V.


###Step 3: Modify the Script
-To change which files get moved or where they go, follow these steps:

**if you still have notepad open with the script you just pasted, great. Lets edit that now. 
Look for the lines in the script that say source_folder and destination_folder.
-Line 6 change 'E:\\Sorted Files' to the folder or drive where your files currently are. For example, 'E:\\Users\\YourName\\Videos' for full drive 'E:\\. keep the '''', paste between them. 
-Line 7 change 'E:\\Moved Files' to the folder where you want the files to go. For example, 'E:\\Videos'.
-Line 16 change the File Extensions: this is the 3 letters that follow the file name. pic.jpg, jpg is the extension.
-Save the edited script on the location you wish to pull from. this is critical when moving from drive to drive. 

**If you closed notepad, Open the Script:**

-Find the Pc-Organizer.py file you saved (for example, in your "Documents" folder) and right-click it.
-Select "Open with" and choose "Notepad".
-Change the Folder Paths:

-Look for the lines in the script that say source_folder and destination_folder.
-Line 6 change 'E:\\Sorted Files' to the folder or drive where your files currently are. For example, 'E:\\Users\\YourName\\Videos' for full drive 'E:\\
-Line 7 change 'E:\\Moved Files' to the folder where you want the files to go. For example, 'E:\\Videos'.
-Line 16 change the File Extensions:

4. **Save the Script:**

-Click "File" in the top left corner of Notepad, then click "Save As".
-In the "Save as type" dropdown, select "All Files".
-In the "File name" field, type Pc-Organizer.py.
-Choose a location where you want to save the file (like "Documents"). Must be on the drive you are moving from. 


###Step 4: Run the Script
Now it's time to make the script do its job. Here’s how:

**Open PowerShell (or Command Prompt):**

Right-click the "Start" button (the Windows logo in the bottom left corner) and choose "Windows PowerShell" or "Command Prompt".
Note: PowerShell and Command Prompt are similar. Either one works for this step.
can also push the windows key then while holding it down. press the 'x' key and it'll pull up a list of programs. choose powershell or terminal. 

Navigate to the Script Location:

If you saved your script in "Documents", type the following command and press "Enter":


cd Documents

4.  If you saved it in a different location:
First, type cd followed by a space.
Then, drag and drop the folder where you saved the script into the PowerShell or Command Prompt window. This will automatically fill in the path.
Press "Enter".
or type out the full path

cd E:\\Users 
press enter

Run the Script:

To run the script, type the following command and press "Enter":

python Pc-Organizer.py

Check the Result:

After running the script, go to the folder where you wanted the files to be moved (the destination_folder you specified) and check if the files have been moved there.

Example Script
Below is what it should look like but your info in line 6, line 7, line 16

 ```python
import os
import shutil

# Specify the source and destination folders
source_folder = 'E:\\Sorted Files'
destination_folder = 'E:\\Moved Files'

# Create the destination folder if it does not exist
if not os.path.exists(destination_folder):
    os.makedirs(destination_folder)

# Walk through the directory tree
for root, dirs, files in os.walk(source_folder):
    for file in files:
        if any(file.lower().endswith(ext) for ext in file_extensions):
            source_file = os.path.join(root, file)
            destination_file = os.path.join(destination_folder, file)
            try:
                shutil.move(source_file, destination_file)
                print(f'Moved: {source_file} -> {destination_file}')
            except Exception as e:
                print(f'Error moving file {source_file}: {e}')

print('All specified files have been moved!')


