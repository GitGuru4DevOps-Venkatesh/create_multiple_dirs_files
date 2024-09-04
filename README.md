# Create_multiple_dirs_files
To create multiple directories and files with custom names provided by the user

🌟 This script allows you to insert content into specific files within specific directories, you can add additional prompts to ask the user for the directory and file name, as well as the content to be added. Here's how you can modify the script:

### Extended Shell Script with Content Insertion

```bash
#!/bin/bash

# Prompt the user for the number of directories to create
read -p "Enter the number of directories to create: " dir_count

# Prompt the user for the number of files to create in each directory
read -p "Enter the number of files to create in each directory: " file_count

# Prompt the user for the base name to be used for directories
read -p "Enter the base name for the directories: " base_dir_name

# Prompt the user for the base name to be used for files
read -p "Enter the base name for the files: " base_file_name

# Loop to create the specified number of directories
for i in $(seq 1 $dir_count); do
    dir_name="${base_dir_name}${i}"
    mkdir "$dir_name"  # Create directory with the specified name

    # Loop to create the specified number of files in each directory
    for j in $(seq 1 $file_count); do
        file_name="${base_file_name}${j}"
        touch "$dir_name/$file_name"  # Create file with the specified name inside the directory
    done
done

echo "$dir_count directories and $((dir_count * file_count)) files have been created with the specified names."

# Prompt to add content to files
while true; do
    # Ask if the user wants to add content to any file
    read -p "Do you want to add content to any file? (yes/no): " add_content
    if [ "$add_content" == "no" ]; then
        break
    fi
    
    # Prompt the user to specify the directory
    read -p "Enter the directory name where the file is located: " target_dir

    # Prompt the user to specify the file
    read -p "Enter the file name where you want to add the content: " target_file

    # Prompt the user for the content to add
    read -p "Enter the content you want to add: " content

    # Check if the directory and file exist before adding content
    if [ -d "$target_dir" ] && [ -f "$target_dir/$target_file" ]; then
        echo "$content" >> "$target_dir/$target_file"
        echo "Content added to $target_dir/$target_file"
    else
        echo "Error: Directory or file does not exist."
    fi
done

echo "Script execution completed."
```

### How to Use This Script

1. **Save the Script**: Save the script to a file, for example, `create_and_add_content.sh`.

2. **Make the Script Executable**: Run the following command to make the script executable.

   ```bash
   chmod +x create_and_add_content.sh
   ```

3. **Run the Script**: Execute the script by running:

   ```bash
   ./create_and_add_content.sh
   ```

4. **Provide Input When Prompted**: The script will guide you through the process of creating directories, files, and adding content.

### Example Run

```bash
Enter the number of directories to create: 2
Enter the number of files to create in each directory: 2
Enter the base name for the directories: Project
Enter the base name for the files: file

2 directories and 4 files have been created with the specified names.

Do you want to add content to any file? (yes/no): yes
Enter the directory name where the file is located: Project1
Enter the file name where you want to add the content: file1
Enter the content you want to add: This is the content for file1 in Project1
Content added to Project1/file1

Do you want to add content to any file? (yes/no): no
Script execution completed.
```

### How It Works:

1. **Creation of Directories and Files**: The script first creates the specified number of directories and files with base names provided by you.
   
2. **Content Addition**: After creating the directories and files, the script will ask if you want to add content to any file. If you choose "yes," it will prompt for the directory name, file name, and the content you want to add. It then checks if the directory and file exist before appending the content.

3. **Repeat**: You can repeat the content addition for different files until you choose "no."

This approach gives you flexibility in not only creating directories and files but also adding custom content to any of the files you create.

💻 Checkout the Video to know more: https://youtu.be/9eRjKGHaAmg
