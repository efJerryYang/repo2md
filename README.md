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
