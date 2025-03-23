# Complete Guide to Deleting Apps and Their Associated Files on macOS

This guide provides step-by-step instructions to completely remove an app and all its associated files (cache, preferences, logs, etc.) from your MacBook Pro or any macOS device. This ensures you free up space and eliminate all traces of the app.

---

## Steps to Delete an App and Its Associated Files

### 1. Delete the Application
1. Open the **Applications** folder.
2. Locate the app you want to delete (e.g., "Coarsen" or "Trae").
3. Drag the app to the **Trash** or right-click and select **Move to Trash**.

---

### 2. Remove Associated Files and Folders
Apps often leave behind cache, preferences, and support files. To remove these:

1. Open **Finder**.
2. Press **Command + Shift + G** to open the "Go to Folder" dialog.
3. Enter the following paths one by one and look for folders or files related to the app:

   ```bash
   ~/Library/Application Support/
   ~/Library/Caches/
   ~/Library/Preferences/
   ~/Library/Logs/
   ~/Library/Saved Application State/