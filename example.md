# `buenum-synth`

## Directory `/`

```sh
|-- .git/
|-- .github/
    `-- workflows/
        `-- rust.yml    [text]
|-- .idea/
|-- benchmarks/
|-- docs/
    `-- Note.md    [text]
|-- src/
    |-- parser/
        |-- ast.rs    [text]
        |-- eval.rs    [text]
        |-- grammar.pest    [text]
        `-- visitor.rs    [text]
    |-- solver/
        |-- baseline_solver.rs    [text]
        `-- egg_solver.rs    [text]
    |-- main.rs    [text]
    |-- parser.rs    [text]
    `-- solver.rs    [text]
|-- .gitignore    [text]
|-- Cargo.toml    [text]
|-- LICENSE    [text]
|-- README.md    [text]
|-- rust-toolchain.toml    [text]
`-- rustfmt.toml    [text]
```

### Directory `.git/`

```sh
```

### Source file: `.gitignore`

```
# Generated by Cargo
# will have compiled files and executables
debug/
target/
...

# MSVC Windows builds of rustc generate these, which store debugging information
*.pdb

```

### Source file: `LICENSE`

```
MIT License

Copyright (c) 2024 UCSD-CSE291D-2024-BUEnum

...

OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

### Directory `src/`

```sh
|-- parser/
    |-- ast.rs    [text]
    |-- eval.rs    [text]
    |-- grammar.pest    [text]
    `-- visitor.rs    [text]
|-- solver/
    |-- baseline_solver.rs    [text]
    `-- egg_solver.rs    [text]
|-- main.rs    [text]
|-- parser.rs    [text]
`-- solver.rs    [text]
```

#### Directory `src/parser/`

```sh
|-- ast.rs    [text]
|-- eval.rs    [text]
|-- grammar.pest    [text]
`-- visitor.rs    [text]
```

### Source file: `src/parser/grammar.pest`

```pest
/// The SyGuS Language Standard Version 2.1

...

VarGTerm   = { "(" ~ "Variable" ~ Sort ~ ")" }

```

### Source file: `src/parser/ast.rs`

```rust
use std::collections::HashMap;

...

#[derive(Debug, Clone, PartialEq, Default)]
pub enum GExpr {
    ...
    
    #[default]
    UnknownGExpr
}

```

### Source file: `src/parser/eval.rs`

```rust
use std::ops::*;

...

#[derive(Debug, Clone, PartialEq, Default)]
pub struct EvalEnv {
    ...
}

impl EvalEnv {
    fn get_var(&self, name: &str) -> Value {
        ...
    }

    fn set_var(&mut self, name: String, val: Value) {
       ...
    }

    fn apply_func(&self, func_name: &str, args: &[Value]) -> Value {
        ...
    }
}

```

### Source file: `src/parser/visitor.rs`

```rust
use pest::{
    ...
}

...

macro_rules! parse_expr {
    ...
}

impl Visitor for SyGuSVisitor {
    ...
}

```

#### Directory `src/solver/`

```sh
|-- baseline_solver.rs    [text]
`-- egg_solver.rs    [text]
```

### Source file: `src/solver/egg_solver.rs`

```rust


```

### Source file: `src/solver/baseline_solver.rs`

```rust
use crate::solver::ast::GTerm;
...

pub struct BaselineSolver;

...

impl Solver for BaselineSolver {
    ...
}

```

### Source file: `src/parser.rs`

```rust
use pest::error::Error;
...

pub mod ast;
pub mod eval;
pub mod visitor;

#[derive(Parser)]
#[grammar = "parser/grammar.pest"] // relative to project `src`
pub struct SyGuSParser;

pub fn parse(input: &str) -> Result<ast::SyGuSProg, Error<Rule>> {
    ...
}

```

### Source file: `src/main.rs`

```rust
#![allow(dead_code)]
use std::fs;

mod parser;
mod solver;

fn main() {
    ...
}

```

### Source file: `src/solver.rs`

```rust
pub mod baseline_solver;
pub mod egg_solver;

use std::cell::RefCell;

use crate::parser::ast;

pub trait Solver {
    ...
}
pub trait ProgTrait {
    ...
}

impl ProgTrait for ast::SyGuSProg {
    ...
}

pub trait GrammarTrait {
    ...
}

impl GrammarTrait for ast::GrammarDef {
    ...
}

```

### Directory `benchmarks/`

```sh
```

### Directory `docs/`

```sh
`-- Note.md    [text]
```

### Source file: `docs/Note.md`

```markdown

```

### Source file: `rust-toolchain.toml`

```toml
[toolchain]
channel = "stable"
```

### Source file: `rustfmt.toml`

```toml
max_width = 120
fn_single_line = false
where_single_line = false
imports_indent = "Block"
imports_layout = "Vertical"
group_imports = "StdExternalCrate"
array_width = 60
control_brace_style = "AlwaysSameLine"
trailing_comma = "Never"
trailing_semicolon = true
match_arm_blocks = true
error_on_line_overflow = false
error_on_unformatted = true
```

### Source file: `README.md`

```markdown
...

## Warning: `z3` dependencies

If you fail to run `cargo build` because of `z3-sys` related errors, you may want to try the following:

1. Install `clang`:

    ...

2. Install `z3`:

    ...

## Run tests

```bash
cargo test
```

```

### Directory `.github/`

```sh
`-- workflows/
    `-- rust.yml    [text]
```

#### Directory `.github/workflows/`

```sh
`-- rust.yml    [text]
```

### Source file: `.github/workflows/rust.yml`

```yml
name: Rust

...
      run: cargo test --verbose

```

### Directory `.idea/`

```sh
```

### Source file: `Cargo.toml`

```toml
[package]
name = "buenum-synth"
version = "0.1.0"
edition = "2021"
description = "Bottom-up Enumerative Synthesizer using Egg"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
anyhow = "1.0.79"
cfg = "0.8.0"
clap = "4.5.1"        # CLI Arguments: clap
egg = "0.9.5"         # EGraph-Good
env = "0.0.0"
log4rs = "1.3.0"      # Log4j-like logging
pest = "2.7.7"        # Parser Generator
pest_derive = "2.7.7"
strum = "0.26"        # Enum utils (to iter())
strum_macros = "0.26"
#z3 = "0.12.0"         # SMT Solver
#z3-sys = "=0.8.1"
#
#[build-dependencies]
#z3-sys = "=0.8.1"

```