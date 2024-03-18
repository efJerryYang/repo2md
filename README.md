# Repository to Markdown (repo2md)

> Credit to Claude-3

## Usage

```bash
Usage: repo2md <REPO> [OPTIONS]

Arguments:
  <REPO>  Path to the local repository

Options:
      --include          <INCLUDE>...  Patterns of files/directories to include
      --ignore/--exclude <IGNORE>...   Patterns of files/directories to ignore/exclude
  -h, --help                           Print help
  -V, --version                        Print version
```

Or clone this project and run with `cargo` from this project root:

```bash
cargo run -- <REPO> [OPTIONS]
```

## Example Output

See [example_repo2md.md](example_repo2md.md) for an example of the output of this tool.

```sh
cargo run --  .
# or
repo2md .
```

## TODO

- [ ] Auto-completion (relative path from the repository root)
  - [ ] use `clap-complete` to handle this
- [ ] Add default `.gitignore` patterns for different languages (point to github repo, cache locally)
  - [ ] maybe we can have `resources` directory and build the binary with the resources
- [ ] Allow automatic update using `--update` or `--upgrade` command
  - [ ] find the latest version from the github repo
  - [ ] locate the binary in the system like `which repo2md` command
  - [ ] download the latest version and try to replace the current binary (should use `sudo` if necessary, distinguish between different OS) 