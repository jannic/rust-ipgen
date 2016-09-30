# Rust IPGen Library

Official implementation of the IPGen Spec in [Rust]

[![Build Status](https://github.com/ipgen/rust-lib.svg?branch=master)](https://github.com/ipgen/rust-lib) [![Latest Version](https://img.shields.io/crates/v/ipgen.svg)](https://crates.io/crates/ipgen) [![Docs](https://docs.rs/ipgen/badge.svg)](https://docs.rs/ipgen)

IPGen is a library for generating unique and reproducible IP addresses in [Rust]. The IP addresses generated by this library are highly unique (depending on your subnet prefix), yet if you pass it the same input it will produce the same IP address.

[Rust]: https://www.rust-lang.org

## Getting Started

Add `ipgen` as a dependancy in your `Cargo.toml` file.
```toml
[dependencies]
ipgen = "0.0.1"
```

Use it in your program as follows:-
```rust
extern crate ipgen;

fn main() {
  // Compute subnet ID
  let subnet = ipgen::subnet("App 1"); 
  assert_eq!("ba3d".to_string(), subnet);
  
  // Or compute an IPv6 address
  // Note you can also pass in an IPv4 network to generate an IPv4
  let ip = ipgen::ip("App 1", "fd52:f6b0:3162::/48").unwrap();
  assert_eq!("fd52:f6b0:3162:46a1:2a4f:89e8:8aed:1327".to_string(), ip.to_string());
}
```
