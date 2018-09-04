# swift-html-kitura

[![Swift 4.1](https://img.shields.io/badge/swift-4.1-ED523F.svg?style=flat)](https://swift.org/download/)
[![Linux CI](https://img.shields.io/travis/pointfreeco/swift-html-kitura/master.svg?label=linux)](https://travis-ci.org/pointfreeco/swift-html-kitura)
[![@pointfreeco](https://img.shields.io/badge/contact-@pointfreeco-5AA9E7.svg?style=flat)](https://twitter.com/pointfreeco)

[Kitura](https://www.kitura.io) plugin for type-safe, transformable HTML views using [swift-html](https://github.com/pointfreeco/swift-html).

## Motivation

The most popular choice for rendering HTML in a Kitura web app is to use the Stencil templating language, but it exposes your application to **runtime errors** and **invalid HTML**. Our plugin prevents these runtime issues at compile-time by embedding HTML directly into Swift’s powerful type system. It uses the [swift-html](https://github.com/pointfreeco/swift-html) DSL for constructing HTML documents using plain Swift data structures.

## Example

To use the plugin all you have to do is return a `Node` value from your router callback:

``` swift
import HtmlKituraSupport
import Kitura

let router = Router()

router.get("/") { request, response, next in
  response.send(
    h1(["Hello, type-safe HTML on Kitura!"])
  )
  next()
}

Kitura.addHTTPServer(onPort: 8080, with: router)
Kitura.run()
```

## Installation

If you want to use swift-html-kitura in a project that uses [SwiftPM](https://swift.org/package-manager/), it's as simple as adding a `dependencies` clause to your `Package.swift`:

``` swift
dependencies: [
  .package(url: "https://github.com/pointfreeco/swift-html-kitura.git", from: "0.1.0")
]
```

### Xcode Sub-project

Submodule, clone, or download swift-html-kitura, and drag `HtmlKituraSupport.xcodeproj` into your project.

## License

All modules are released under the MIT license. See [LICENSE](LICENSE) for details.
