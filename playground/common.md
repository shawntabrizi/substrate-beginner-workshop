# Common Patterns Moving Forward

We are about to jump into the coding part of this workshop, but before we go there, let's review some common patterns you will repeatedly use throughout.

#### Start and Stop Your Node

Use the drop down menu `Substrate > Start Node` to start your Substrate node. Or run:

```bash
./target/release/node-template --dev --ws-external
```

To stop, just press `ctrl + c`.

#### Reset Your Node

When you stop a node, you are able to just start it again and pick up where you left off.
That means when you start your node again, all previous state remains the same!

If you want to **reset** your node, run the `purge-chain` command:

```bash
# Removes the database file for your Substrate developer node
./target/release/node-template purge-chain --dev -y
```

_In general_, make sure that your database is cleaned up whenever you are making changes to your Substrate node.

**If you don't do this, you may find that code changes you made do not appear on your node!**

<!-- slide:break -->

#### Check Your Code

Doing a full compile of your Substrate node can take a while, even with minor changes.
It is faster to run `cargo check` instead:

```bash
cargo check
```

Output:

```
Compiling node-template-runtime v2.0.0 (/home/workspace/substrate-node-template/runtime)
Checking node-template v2.0.0 (/home/workspace/substrate-node-template)
Finished dev [unoptimized + debuginfo] target(s) in 8.77s
```

#### Compile Your Node

When you want to finally compile your node, you need to make sure to build in **release mode**.

```bash
cargo build --release
```



