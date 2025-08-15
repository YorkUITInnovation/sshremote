# SSH Server Selector Script

A simple and user-friendly bash script that provides an interactive menu to quickly connect to predefined SSH servers. Perfect for developers and system administrators who frequently connect to multiple remote servers.

## Features

- 🖥️ **Interactive Menu**: Select servers from a numbered list instead of remembering hostnames
- ⚡ **Quick Access**: Predefined server configurations with friendly names
- ✅ **Input Validation**: Handles invalid selections gracefully
- 🔧 **Easy Configuration**: Simple array-based server definitions
- 🚀 **Lightweight**: Pure bash script with no external dependencies

## Prerequisites

- Bash shell
- SSH client installed
- SSH keys configured for passwordless authentication (recommended)

## Installation

1. **Clone or download the script**:
   ```bash
   git clone <your-repository-url>
   cd <repository-name>
   ```

2. **Make the script executable**:
   ```bash
   chmod +x sshremote
   ```

3. **Optional: Add to PATH for global access**:
   ```bash
   # Create a bin directory in your home folder (if it doesn't exist)
   mkdir -p ~/bin
   
   # Copy the script
   cp sshremote ~/bin/
   
   # Add to PATH (add this line to your ~/.bashrc or ~/.zshrc)
   echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
   
   # Reload your shell configuration
   source ~/.bashrc
   ```

4. **Alternative: Create an alias**:
   ```bash
   # Add to your ~/.bashrc or ~/.zshrc
   echo 'alias sshremote="/home/thibaud/scripts/sshremote"' >> ~/.bashrc
   source ~/.bashrc
   ```

## Usage

Run the script:
```bash
./sshremote
```

Example output:
```
Available servers:
1. friendly-name (username@hostname)
2. production (username@hostname)
3. staging (username@hostname)
4. edevelopment (username@hostname)
Enter the number of the server to connect: 2
Connecting to username@hostname...
```

## Configuration

### Adding New Servers

Edit the `servers` array in the script to add your own SSH connections:

```bash
servers=(
  "name=friendly-name,path=username@hostname"
  "name=production,path=admin@prod.example.com"
  "name=staging,path=deploy@staging.example.com"
  "name=development,path=dev@dev.example.com"
)
```

### Server Entry Format

Each server entry follows this format:
- `name=`: A friendly name for the server (displayed in the menu)
- `path=`: The SSH connection string (username@hostname or IP)

## Making the Script Available Globally

### Method 1: Add to PATH (Recommended)

1. **Create a bin directory** in your home folder:
   ```bash
   mkdir -p ~/bin
   ```

2. **Copy or link your script**:
   ```bash
   cp /home/thibaud/scripts/sshremote ~/bin/
   # OR create a symbolic link
   ln -s /home/thibaud/scripts/sshremote ~/bin/sshremote
   ```

3. **Add ~/bin to your PATH** by editing `~/.bashrc`:
   ```bash
   echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

### Method 2: Create an Alias

1. **Open your shell configuration file**:
   ```bash
   nano ~/.bashrc
   ```

2. **Add an alias** at the end of the file:
   ```bash
   alias ssh-select="/home/thibaud/scripts/sshremote"
   ```

3. **Reload your shell configuration**:
   ```bash
   source ~/.bashrc
   ```

Now you can run `ssh-select` in any terminal to use your script.

**Note**: Using `ssh` as the command name would override the system's SSH command, which is why we recommend using `ssh-select` or similar name instead.

## Troubleshooting

### Common Issues

1. **Permission Denied**: Make sure the script is executable
   ```bash
   chmod +x sshremote
   ```

2. **Command Not Found**: If you added the script to PATH, reload your shell
   ```bash
   source ~/.bashrc  # or ~/.zshrc
   ```

3. **SSH Connection Fails**: Verify the server details and your SSH configuration
   ```bash
   ssh -v username@hostname  # Verbose mode for debugging
   ```

### Error Messages

- `Invalid selection.`: You entered a number outside the valid range
- SSH connection errors: Check your network connection and server availability

## Contributing

Feel free to submit issues and enhancement requests!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Author

Created by Patrick Thibaudeau

---

**Note**: Always ensure your SSH keys are properly configured and secured when using automated SSH connections.
