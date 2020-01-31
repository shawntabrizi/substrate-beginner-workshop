# Add Events

To start thinking about our blockchain runtime, we can first write some events it will emit.

* `ClaimCreated`
	* Data: `AccountId`, `Vec<u8>`

* `ClaimRevoked`
	* Data: `AccountId`, `Vec<u8>`

To use `Vec` you need to import `sp_std::prelude::Vec`:

```rust
use sp_std::prelude::Vec;
```

<!-- slide:break-40 -->

<!-- tabs:start -->

#### ** Hide Hints **

Click the other tabs to view hints.

![Image of Runtime Events](./assets/events.png ':size=300')

#### ** Hint: Events **

```rust
ClaimCreated(AccountId, Vec<u8>),
ClaimRevoked(AccountId, Vec<u8>),
```

#### ** Hint: Deposit Event **

```rust
fn deposit_event() = default;
```

#### ** Solution **

```rust
use frame_support::{decl_module, decl_storage, decl_event};
use sp_std::prelude::Vec;

pub trait Trait: system::Trait {
	type Event: From<Event<Self>> + Into<<Self as system::Trait>::Event>;
}

decl_event! {
	pub enum Event<T> where AccountId = <T as system::Trait>::AccountId {
		ClaimCreated(AccountId, Vec<u8>),
		ClaimRevoked(AccountId, Vec<u8>),
	}
}

decl_storage! {
	trait Store for Module<T: Trait> as TemplateModule {
		// Storage
	}
}

decl_module! {
	pub struct Module<T: Trait> for enum Call where origin: T::Origin {
		fn deposit_event() = default;
	}
}

decl_error! {
	pub enum Error for Module<T: Trait> {
		// Errors
	}
}
```

<!-- tabs:end -->