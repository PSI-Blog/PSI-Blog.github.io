---
title: "Functional Programming in Rust and Haskell"
date: 2022-07-12T01:50:42+01:00
draft: true
tags: ["Rust","Programming","Haskell"]
author: "Diogo Valério"
---

Have you ever wondered what is functional programming?
This big buzz word everyone is talking about?

## What is Functional Programming?

In **Functional Programming** everything is implemented using functions.

Functions are pieces of code which may receive some **input value**(parameters) and may return some **output value**.

In this case we have the `say_hello`  function which has no **parameters** and no **output value**, this function prints to the screen "hello world".

**Rust Example:**
```rust
fn say_hello(){
    println!("hello world");
}
```

**Haskell Example:**
```rust
say_hello = putStrLn "hello world"
```

And in this case we have the function `add_one` which has an **input value** `num` of the type `i32` and returns that value plus 1.

**Rust Example:**
```rust
fn add_one(num:i32) -> i32{
    return (num + 1);
}
```

## Why use Functional Programming?

Functional programming is one of the simplest programming paradigms and 
