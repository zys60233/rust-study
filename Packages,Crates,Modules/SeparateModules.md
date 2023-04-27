## Separating Modules into Different Files

```rust
// src/lib.rs

mod front_of_house;

pub use crate::front_of_house::hosting;

pub fn eat_at_restanurant() {
    hosting::add_to_waitlist();
}
```

```rust
// src/front_of_house.rs

pub mod hosting;
```

```rust
// src/front_of_house/hosting.rs

pub fn add_to_waitlist() {}
```

