# Repository to Markdown (repo2md)

> Credit to Claude-3

## Usage

```bash
repo2md <path_to_repo> [options]

Args:
  <path_to_repo>  Path to the repository to document

Options:
  --include <pattern1> <pattern2> ...
                         Include only files matching these patterns
  (--ignore|--exclude) <pattern1> <pattern2> ...
                         Ignore files matching these patterns
  --help                 Display this message
```

Or clone this project and run with `cargo` from this project root:

```bash
cargo run -- <path_to_repo> [options]
```

## Example Output

See [example.md](example.md) for an example of the output of this tool.

```sh
cargo run --  path/to/project/ --ignore benchmarks/ .idea/
```
