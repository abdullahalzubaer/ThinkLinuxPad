# Prompts CLI Script

This script provides a command-line interface (CLI) for accessing predefined prompts. You can quickly retrieve prompts like `explain`, `critically-analyze`, or any custom prompts you add. Follow the steps below to create and use the script.

---

## Installation Steps

### 1. Create the Script
1. Open a terminal and create the script file:
   ```bash
   nvim ~/prompts.sh
   ```

2. Paste the following content into the file:

```bash
#!/bin/bash

# Define a list of options
available_options=("explain" "critically-analyze")

# Check the argument passed to the script
case "$1" in
    explain)
        echo "First you must explain to me what you have: 1) understood 2) the requirements 3) the purpose of my task. Then you provide the answer. If you need further information you must ask me."
        ;;
    critically-analyze)
        echo "Provide a detailed critical analysis: identify strengths, weaknesses, and any potential improvements. Ensure your evaluation is thorough and well-supported."
        ;;
    list)
        echo "Available options:"
        for option in "${available_options[@]}"; do
            echo "- $option"
        done
        ;;
    *)
        echo "Usage: prompts [explain|critically-analyze|list]"
        ;;
esac
```

Save the file and exit:


### 2. Make the Script Executable

Run the following command to make the script executable:

```bash
chmod +x ~/prompts.sh
```


### 3. Move the Script to a Global Location

Move the script to /usr/local/bin to make it accessible system-wide:

```bash
sudo mv ~/prompts.sh /usr/local/bin/prompts
```


### 4. Test the Script

Run the script to ensure it works:

```bash
prompts list
```
Output:
```
Available options:
- explain
- critically-analyze

```

## Adding More Prompts

### Steps to Add New Prompts

1. Open the script for editing:

```bash
sudo nvim /usr/local/bin/prompts

```

2. Add the new prompt to the `available_options` array and its corresponding logic in the `case` block. For example:
```bash
# Define a list of options
available_options=("explain" "critically-analyze" "summarize" "brainstorm")

# Check the argument passed to the script
case "$1" in
    explain)
        echo "First you must explain to me what you have: 1) understood 2) the requirements 3) the purpose of my task. Then you provide the answer. If you need further information you must ask me."
        ;;
    critically-analyze)
        echo "Provide a detailed critical analysis: identify strengths, weaknesses, and any potential improvements. Ensure your evaluation is thorough and well-supported."
        ;;
    summarize)
        echo "Summarize the main points concisely, covering the most important aspects without unnecessary detail."
        ;;
    brainstorm)
        echo "Generate a list of creative ideas or solutions, considering different angles and possibilities for the task at hand."
        ;;
    list)
        echo "Available options:"
        for option in "${available_options[@]}"; do
            echo "- $option"
        done
        ;;
    *)
        echo "Usage: prompts [explain|critically-analyze|summarize|brainstorm|list]"
        ;;
esac
```

3. Save the file and exit:

4. Test the updated Script

Run the script to ensure it works:

```bash
prompts list
```
Output:
```
Available options:
- explain
- critically-analyze
- summarize
- brainstorm

```

## Usage Examples:

- list all prompts :
  ```bash
  prompt list
  ```
- Get the `explain prompt`:
  ```bash
  prompts explain
  ```



## Contributing

Feel free to fork this repository and submit pull requests to add more prompts or improve the functionality of the script.


## License

This script is licensed under the MIT License. See the LICENSE file for more information.
