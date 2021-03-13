# How To Create NodeJS Command-Line Package

### Step 1. Convert JS file into a NodeJS command-line script
Add this **shebang line** at the top of the JS file: ```#!/usr/bin/env node``` 
  - On unix-like platforms, the _shebang(`#!`) line_ at the top of the file tells the system to which interpreter (in the above case, it is `node`) to pass the file for execution.

### Step 2. Modify permission to make the new file executable.
Execute `chmod +x <filename>`. 
  - `chmod` : change the access permission of the files and directories
  - `+x` : add 'execute' mode

### Step 3. Configure the `package.json` file to map a command-line script to a command name
In the `package.json`, add this:
  ```json
  "bin": {
    "command-name": "<filename>"
  }
  ```
  - `bin` field in `package.json` : it is required if the package is an executable file. It maps the command names and local file names (the executable file).

## Step 4. Symlink the command globally
Execute `npm link` inside the package directory.