![](img/rocket.png)
<!-- .element: style="margin-top: -5%;" -->

#### [Mario Garcia](http://mariog.xyz) · [@mariogmd](https://twitter.com/mariogmd)

---

## What is Rust?

---

### A systems programming language focus on:

<br>

<span class="fragment">safety</span><span class="fragment">, speed</span><span class="fragment">, and concurrency.</span>

<!-- .element: class="fragment" -->

---

## Installing Rust

### Linux or Mac:

```
  $ curl https://sh.rustup.rs -sSf | sh
```

---

```
  $ rustc --version
  rustc 1.15.0 (10893a9a3 2017-01-19)
```

---

## IDEs

---

## Atom

_[atom.io](https://atom.io)_

---

## SolidOak

_[sekao.net/solidoak](https://sekao.net/solidoak)_

---

## Ride

_[github.com/madeso/ride](https://github.com/madeso/ride)_

---

## Hello world!

---

## Print text

```
  println!("string {} literal", expressions);
```

---

```
  // hello.rs
  fn main() {
      println!("Hello, world!");
  }
```

---

## Comments

```
  // This is a comment
```

---

## Running

```
  $ rustc hello.rs
  $ ./hello
  Hello, world!
```

---

![](img/cargo-logo.png)

## Cargo

---

## What is Cargo?

---

### Cargo is Rust’s build system and package manager.

---

## New project with Cargo

```
  $ cargo new hello_world --bin
```

---

```
  ~/hello_world$ ls -R 
```

---

```
  .:
  Cargo.toml src

  ./src:
  main.rs
```

---

## Manifest

```
  [package]
  name = "hello_world" # the name of the package
  version = "0.1.0"    # the current version
  authors = ["you@example.com"] # author
```

---

## Build & Run

```
  $ cargo build
  $ cargo run
```

---

## Rocket

_[rocket.rs](https://rocket.rs)_

---

## What is Rocket?

---

### A web framework for Rust

---

## Requirements

---

### A nightly version of Rust

```
  $ rustup install nightly
```

---

```
  $ rustup run nightly rustc --version
  rustc 1.17.0-nightly (c49d10207 2017-02-07)
```

---

```
  $ rustup default nightly
```

---

## Hello, world!

---

### Running examples

```
  $ git clone https://github.com/SergioBenitez/rocket
  $ cd rocket/examples/hello_world
  $ cargo run
```

---

### Manifest

```
  [package]
  name = "hello_world"
  version = "0.0.1"
  workspace = "../../"

  [dependencies]
  rocket = { path = "../../lib" }
  rocket_codegen = { path = "../../codegen" }

  [dev-dependencies]
  rocket = { path = "../../lib", features = ["testing"] }
```

---

### main.rs

```
  #![feature(plugin)]
  #![plugin(rocket_codegen)]

  extern crate rocket;

  #[cfg(test)] mod tests;

  #[get("/")]
  fn hello() -> &'static str {
      "Hello, world!"
  }

  fn main() {
      rocket::ignite().mount("/", routes![hello]).launch();
  }
```

---

### Cargo project

```
  $ cargo new hello-rocket --bin
  $ cd hello-rocket
```

---

### Modify Cargo.toml

```
  [package]
  name = "hello_rocket"
  version = "0.1.0"
  authors = ["mattdark@mozilla-mexico.org"]
  
  [dependencies]
  rocket = "0.2.0"
  rocket_codegen = "0.2.0"
```

---

### Modify main.rs

```
  #![feature(plugin)]
  #![plugin(rocket_codegen)]

  extern crate rocket;

  #[get("/")]
  fn index() -> &'static str {
      "Hello, world!"
  }

  fn main() {
      rocket::ignite().mount("/", routes![index]).launch();
  }
```

---

## Learn More

_[rocket.rs](https//rocket.rs)_

___

[@mariogmd](https://twitter.com/mariogmd)

mattdark@mozilla-mexico.org
