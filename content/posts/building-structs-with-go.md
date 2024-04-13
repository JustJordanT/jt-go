---
title: 'Building Structs With Go'
date: 2023-09-08T13:43:53-06:00
draft: false
# image: brand_image.jpg
tags: ["go"]
# series: "How to use poison"
---

# Introduction

Structs in the Go programming language serve as fundamental building blocks for creating custom data structures. They enable us to encapsulate and organize data effectively. In this blog post, we'll explore Go structs by using the analogy of creating a toy to better understand their syntax, usage, and best practices.

## What is a Struct?

In Go, a struct is like a blueprint for creating custom data types. Think of it as a recipe for building something unique. For our analogy, let's imagine we're creating a toy car:

```go
type ToyCar struct {
    Model  string
    Color  string
    Wheels int
}
```

Here, we've defined a `ToyCar` struct with three key attributes: `Model`, `Color`, and `Wheels`, each representing an essential feature of our toy car.

## Creating Toy Instances

Just as you would assemble a real toy car, you can create instances (or instances of your toy) from the `ToyCar` struct. Here's how you can create a toy car:

```go
myToyCar := ToyCar{
    Model:  "Sports",
    Color:  "Red",
    Wheels: 4,
}
```

In this code, `myToyCar` is an instance of our `ToyCar` struct, and we've given it specific values for its attributes.

## Playing with Toy Fields

To enjoy our toy car, we need to know how to interact with it. In Go, we access a struct's attributes using dot notation. For instance, if we want to know the model of `myToyCar`, we can do this:

```go
fmt.Println(myToyCar.Model) // Output: Sports
```

## Toy Composition: Adding Extra Features

Just like you might want to add a turbocharger or racing stripes to your toy car, Go allows you to embed one struct within another. This feature is called "struct embedding" and allows you to compose more complex data structures. Let's say we want to add a radio to our toy car:

```go
type ToyWithRadio struct {
    ToyCar
    Radio bool
}
```

Now, a `ToyWithRadio` includes all the attributes of a `ToyCar` as well as an extra `Radio` feature.

## Toy Methods: Making It Move

To make our toy car zoom around, we need to define methods. In Go, methods are functions that operate on a struct's instances. For example, let's add a method to start our toy car:

```go
func (t ToyCar) Start() {
    fmt.Println("Starting the", t.Color, t.Model, "toy car!")
}
```

With this method, we can start our toy car like this:

```go
myToyCar.Start() // Output: Starting the Red Sports toy car!
```

Certainly! Let's improve the example in the "Decorating Our Toy: Using Struct Tags" section by using JSON tags, and I'll explain why they are essential.

## Decorating Our Toy: Using JSON Tags

In the world of Go structs, JSON tags are commonly used to provide metadata about struct fields. These tags are particularly important when you need to serialize a struct into JSON format or deserialize JSON data into a struct. Here's a revised example:

```go
type ToyCar struct {
    Model  string `json:"model"`
    Color  string `json:"color"`
    Wheels int    `json:"wheels"`
}
```

In this updated `ToyCar` struct, we've added JSON tags to each field. The JSON tags are specified within backticks and follow the field name. The tags provide information to Go's JSON encoding and decoding functions.

## Conclusion

Creating Go structs is akin to crafting your own toys, with each field and method defining a unique feature or behavior. By understanding how to define, build, and play with structs, you'll be well-equipped to design and develop complex applications in Go. So, unleash your creativity and start building incredible Go "toys" today!