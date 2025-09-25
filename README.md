# thing-king/dom

**thing-king/dom** is a drop-in, cross-target replacement for Nim’s [`std/dom`](https://nim-lang.org/docs/dom.html).  
It exposes the full set of DOM environment procedures (e.g., `getElementById`, `querySelector`, etc.) in both **native** and **JavaScript** compilation targets.

In JavaScript builds, procedures map directly to the standard DOM API.  
In native builds, the same procedures are defined as **no-ops**, ensuring seamless compilation without conditional logic.

---

## Key Features
- **1:1 compatibility** with `std/dom`
- **Cross-target** support: works in both native and JS builds
- **Safe no-op stubs** on native targets
- **Framework ready**: designed for use within [thing](https://github.com/thing-king)

---

## Example

```nim
import thingking/dom

# Write DOM code once, without worrying about target.
let node = getElementById("myDiv")

# On JS builds → behaves as expected
# On native builds → compiles cleanly, no-ops at runtime
```