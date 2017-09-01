![](img/rocket.png)
<!-- .element: style="margin-top: -5%;" -->

#### [Mario Garcia](http://mattdark.github.io) · [@mariogmd](https://twitter.com/mariogmd)

---

## Rocket

_[rocket.rs](https://rocket.rs)_

---

## What is Rocket?

***

### A web framework for Rust

---

## Requirements

***

### A nightly version of Rust

#### Installing Rust
```
  $ rustup install nightly
```

***

#### Check version installed

```
  $ rustup run nightly rustc --version
  rustc 1.21.0-nightly (7eeac1b81 2017-08-30)
```

***

#### Set default

```
  $ rustup default nightly
```

***

#### Set default for project

```
  $ rustup override set nightly
```

---

### Running examples

```
  $ git clone https://github.com/SergioBenitez/rocket
  $ cd rocket/examples/hello_world
  $ cargo run
```

---

### Hello, world!

***

### Create project

```
  $ cargo new hello_rocket --bin
  $ cd hello_rocket
```

***

### Manifest

```
  [package]
  name = "hello_rocket"
  version = "0.1.0"
  authors = "[mattdark]"

  [dependencies]
  rocket = "0.3.2"
  rocket_codegen = "0.3.2"
```

***

### main.rs

```
  #![feature(plugin)]
  #![plugin(rocket_codegen)]

  extern crate rocket;

  #[cfg(test)] mod tests;

  #[get("/")]
  fn index() -> &'static str {
      "Hello, world!"
  }

  fn main() {
      rocket::ignite().mount("/", routes![index]).launch();
  }
```

---

### Running

```
  $ cargo build
  $ cargo run
```

***

```
🔧  Configured for development.
    => address: localhost
    => port: 8000
    => log: normal
    => workers: 4
    => secret key: generated
    => limits: forms = 32KiB
    => tls: disabled
🛰  Mounting '/':
    => GET /
🚀  Rocket has launched from http://localhost:8000
```

***

### Running in Firefox

```
  http://localhost:8000
  Hello, world!
```

---

## Routing

***

```
  #[get("/world")]  // <- route attribute
  fn world() -> &'static str {  // <- request handler
    "Hello, world!"
  }
```

---

## Mounting

***

```
  rocket::ignite().mount("/hello", routes![world]);
```

---

## main.rs

```
  #![feature(plugin)]
  #![plugin(rocket_codegen)]

  extern crate rocket;

  #[get("/world")]
  fn world() -> &'static str {
    "Hello, world!"
  }

  fn main() {
    rocket::ignite().mount("/hello", routes![world]).launch();
  }
```

---

## Running

```
  $ cargo run
```

***

```
🔧  Configured for development.
    => address: localhost
    => port: 8000
    => log: normal
    => workers: 4
    => secret key: generated
    => limits: forms = 32KiB
    => tls: disabled
🛰  Mounting '/hello':
    => GET /hello/world
🚀  Rocket has launched from http://localhost:8000
```

***

### Running in Firefox

```
  http://localhost:8000/hello/world
  Hello, world!
```

---

## Requests

***

```
  #![feature(plugin)]
  #![plugin(rocket_codegen)]

  extern crate rocket;

  #[get("/hello/<name>")]
  fn hello(name: String) -> String {
    format!("Hello, {}!", name.as_str())
  }

  fn main() {
    rocket::ignite().mount("/", routes![hello]).launch();
  }
```

***

### Running

```
  $ cargo run
```

***

```
🔧  Configured for development.
    => address: localhost
    => port: 8000
    => log: normal
    => workers: 4
    => secret key: generated
    => limits: forms = 32KiB
    => tls: disabled
🛰  Mounting '/':
    => GET /hello/<name>
🚀  Rocket has launched from http://localhost:8000
```

***

#### Running in Firefox

```
  http://localhost:8000/hello/Mario
  Hello, Mario!
```

---

## Learn More

_[rocket.rs](https//rocket.rs)_

___

[@mariogmd](https://twitter.com/mariogmd)

[fb.com/iscmariog](https://fb.com/iscmariog)

mattdark@mozilla-mexico.org
