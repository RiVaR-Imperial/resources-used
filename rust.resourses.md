# Rust Fundamentals 

* **The Rust Programming Language (aka *the Book*)** – comprehensive guide from basics to advanced Rust concepts. [https://doc.rust-lang.org/book/](https://doc.rust-lang.org/book/)

* **Rust by Example** – interactive code examples you can try in Playgrounds. [https://doc.rust-lang.org/rust-by-example/](https://doc.rust-lang.org/rust-by-example/)


### Ownership, Borrowing & Lifetimes

* *Lifetime and ownership course* (free video): [https://www.youtube.com/watch?v=zF34dRivLOw](https://www.youtube.com/watch?v=zF34dRivLOw)


### Traits, Generics & Type System


* *Traits and Generics section* in *The Book*
* *Rust Generic Programming Patterns* talk
  [https://youtu.be/1DV0l63kDp4](https://youtu.be/1DV0l63kDp4)

### Async, Concurrency & Parallelism

* Asynchronous Rust (async/await):
  [https://rust-lang.github.io/async-book/](https://rust-lang.github.io/async-book/)

* “Fearless Concurrency in Rust” article series:
  [https://rust-wasm.github.io/docs/book/concurrency.html](https://rust-wasm.github.io/docs/book/concurrency.html)


# Rust for Numerical Computing

| Task                 | Rust Library                      | What It Does                      |
| -------------------- | --------------------------------- | --------------------------------- |
| Arrays & math        | `ndarray`                         | n-dimensional arrays (like NumPy) |
| Linear algebra       | `nalgebra`                        | Vectors, matrices, decompositions |
| Random numbers       | `rand`                            | RNGs, distributions               |
| FFT                  | `rustfft`                         | Fast Fourier Transforms           |
| BLAS/LAPACK bindings | `blas`, `lapack`/`ndarray-linalg` | High-performance linear algebra   |
| Parallelism          | `rayon`                           | Data-parallelism                  |

**Links:**

* [https://crates.io/crates/ndarray](https://crates.io/crates/ndarray)
* [https://crates.io/crates/nalgebra](https://crates.io/crates/nalgebra)
* [https://crates.io/crates/rand](https://crates.io/crates/rand)
* [https://crates.io/crates/rayon](https://crates.io/crates/rayon)

---

## Example: Monte Carlo in Rust


```rust
use rand::prelude::*;
use rayon::prelude::*;

fn monte_carlo_sim(n: usize) -> f64 {
    (0..n).into_par_iter()
        .map(|_| {
            let mut rng = thread_rng();
            let x: f64 = rng.gen::<f64>();
            x * x
        })
        .sum::<f64>() / n as f64
}
```

This uses:

* `rand` for RNG
* `rayon` for parallel execution


# Rust Libraries for Quantitative Finance

### Finance & Math Crates

* `quantile` — compute percentiles & tail metrics (needed for VaR)
* `time_series` — basic time series types & tools
* `statistics` — descriptive statistics

Search on crates.io:
 [https://crates.io/search?q=finance](https://crates.io/search?q=finance)


# Rust Tooling for Development


* Cargo (official Rust build tool)
* Crates.io (Rust package registry)


* `#[test]` unit tests
* Property testing (`proptest`)


* Criterion.rs — powerful benchmarking harness
  [https://crates.io/crates/criterion](https://crates.io/crates/criterion)



* *Jon Gjengset’s Rust livestreams* — in-depth explanations
  [https://www.youtube.com/jonhoo](https://www.youtube.com/jonhoo)

* *Rust for Machine Learning / Data* playlists
  [https://www.youtube.com/playlist?list=PL85XCvVPmGQhV-eeDGtI52rtbG6qaLQ6E](https://www.youtube.com/playlist?list=PL85XCvVPmGQhV-eeDGtI52rtbG6qaLQ6E)

---


* **Rust QMath** — numerical primitives
  [https://github.com/rust-ndarray/ndarray](https://github.com/rust-ndarray/ndarray)
* **Portfolio simulation examples** — translate Python to Rust
* **Rust finance tutorials on GitHub** (search “rust monte carlo finance”)

*A practical tip:* Clone Python risk code and rewrite it in Rust to internalize patterns.

---

