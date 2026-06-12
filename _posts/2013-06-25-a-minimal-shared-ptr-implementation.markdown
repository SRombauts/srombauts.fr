---
title:  "A minimal shared/unique_ptr implementation."
tags:
  - c++
  - github
---

Sometimes you are stuck on an old toolchain without C++11, but you still want a reference-counted smart pointer.
For that reason, we were using Boost shared_ptr.

But for a specific embedded project, we hit a problem trying to compile and link our code with boost smart pointer library: the binary was too big for the target!

So I wrote [shared_ptr](https://github.com/SRombauts/shared_ptr), a minimal header-only `shared_ptr` (a subset of the C++11 `std::shared_ptr` / `boost::shared_ptr`) for C++98/03.

It is small and simple on purpose: header-only, STL-only dependencies, about 92 bytes per template instantiation. It also ships a fake `unique_ptr` as a placeholder on compilers that lack the real one (it does not conform to the standard, it is just there so the same code compiles).

What it deliberately does not do:

- no `weak_ptr`
- no array support (it won't call `delete[]`)
- not thread-safe (monothreaded by design)
- it needs virtual destructors to delete a derived object through a base pointer

It comes with documentation and unit tests, and is tested with GCC, Clang and Visual Studio on Linux and Windows.
It's published under the MIT license, like everything I do.

Obviously, if you are on a modern compiler, just use `std::shared_ptr`. This is only for when you can't.

[shared_ptr on GitHub](https://github.com/SRombauts/shared_ptr)
