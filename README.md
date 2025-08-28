# File-Handling-and-Exception-Handling-Assignment
def modify_content(content):
    """Example modification: convert text to uppercase"""
    return content.upper()

def main():
    # Get filename from user
    filename = input("Enter the filename to read: ").strip()
    
    # Try reading the file
    try:
        with open(filename, 'r') as file:
            content = file.read()
    except FileNotFoundError:
        print(f"Error: The file '{filename}' does not exist.")
        return
    except PermissionError:
        print(f"Error: Permission denied to read '{filename}'.")
        return
    except OSError as e:
        print(f"Error: Cannot read file '{filename}'. {e}")
        return
    
    # Process content and create new filename
    modified = modify_content(content)
    new_filename = f"modified_{filename}"
    
    # Try writing to new file
    try:
        with open(new_filename, 'w') as file:
            file.write(modified)
        print(f"Successfully created modified file: '{new_filename}'")
    except OSError as e:
        print(f"Error: Could not write to file '{new_filename}'. {e}")

if __name__ == "__main__":
    main()
