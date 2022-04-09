# parseit

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/orhun/parseit/Continuous%20Integration)](https://github.com/orhun/parseit/actions)
[![Crates.io](https://img.shields.io/crates/v/parseit)](https://crates.io/crates/parseit)
[![docs.rs](https://img.shields.io/docsrs/parseit)](https://docs.rs/parseit/latest)
[![Codecov](https://img.shields.io/codecov/c/gh/orhun/parseit)](https://app.codecov.io/gh/orhun/parseit)

Simple text file parsing library powered by [regex](https://en.wikipedia.org/wiki/Regular_expression) and [glob patterns](<https://en.wikipedia.org/wiki/Glob_(programming)>).

```rs
// Create a parser to parse sections in Cargo.toml (and optionally Cargo.lock)
let parser = Parser::new(&["Cargo.*"], &["Cargo.toml"], r#"^\[(.*)\]$\n"#).unwrap();

// Parse the files in the manifest directory.
let documents = parser
    .parse(&PathBuf::from(env!("CARGO_MANIFEST_DIR")))
    .unwrap();

// Print results.
for document in documents {
    println!("Path: {}", document.path.to_string_lossy());
    for paragraph in document.paragraphs {
        println!("Title: {}", paragraph.title);
        println!("Contents: {}", paragraph.contents);
        println!();
    }
}
```

## Examples

See [examples](./examples/).

## Cargo Features

- `gzip`: support reading gzip (`.gz`) files

## License

Licensed under either of [Apache License Version 2.0](http://www.apache.org/licenses/LICENSE-2.0) or [The MIT License](http://opensource.org/licenses/MIT) at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache 2.0 License, shall be dual licensed as above, without any additional terms or conditions.

## Copyright

Copyright © 2022, [Orhun Parmaksız](mailto:orhunparmaksiz@gmail.com)
