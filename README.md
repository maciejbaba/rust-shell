# rust-shell

A simple shell implementation written in Rust that provides basic command execution with support for built-in commands and piping.

## Features

- **Command Execution**: Execute system commands with arguments
- **Built-in Commands**: 
  - `cd <directory>` - Change current directory
  - `exit` - Exit the shell
- **Piping Support**: Chain commands together using pipes (`|`)
- **Interactive Prompt**: Clean command-line interface with `>` prompt
- **Error Handling**: Graceful error reporting for invalid commands or directories

## Installation

### Prerequisites

- Rust (2024 edition or later)
- Cargo package manager

### Build from Source

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd rust-shell
   ```

2. Build the project:
   ```bash
   cargo build --release
   ```

3. Run the shell:
   ```bash
   cargo run
   ```

## Usage

Once started, the shell will display a `>` prompt where you can enter commands:

```
> ls -la
> cd /home/user
> pwd
> echo "Hello World" | grep "Hello"
> exit
```

### Built-in Commands

#### `cd <directory>`
Change the current working directory.

```
> cd /home/user
> cd ..
> cd ~
```

If no directory is specified, defaults to the root directory (`/`).

#### `exit`
Exit the shell and return to the parent shell.

```
> exit
```

### Piping

Commands can be chained together using the pipe operator (`|`):

```
> ls -la | grep "rust"
> cat file.txt | sort | uniq
> ps aux | grep "python" | wc -l
```

## Examples

Here are some example command sequences:

```bash
# Basic file operations
> ls
> pwd
> cd src
> ls -la

# Using pipes
> cat Cargo.toml | grep "name"
> ps aux | grep "bash"
> find . -name "*.rs" | head -5

# Directory navigation
> cd ..
> pwd
> cd /tmp
> ls
```

## Implementation Details

- Written in Rust 2024 edition
- Uses standard library modules: `std::env`, `std::io`, `std::path`, `std::process`
- Implements command piping through `Stdio` redirection
- Handles built-in commands (`cd`, `exit`) internally
- External commands are spawned as child processes

## Architecture

The shell operates in a simple loop:
1. Display prompt (`>`)
2. Read user input
3. Parse commands and detect pipes
4. Execute commands sequentially, connecting outputs to inputs for piped commands
5. Wait for final command completion
6. Repeat

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source. Please check the repository for license details.

## Development

### Running in Debug Mode

```bash
cargo run
```

### Running Tests

```bash
cargo test
```

### Building for Release

```bash
cargo build --release
```

The compiled binary will be available in `target/release/rust-shell`.