# thing-king/dom

**thing-king/dom** is a drop-in, cross-target replacement for Nim's [`std/dom`](https://nim-lang.org/docs/dom.html).  
It exposes the full set of DOM environment procedures (e.g., `getElementById`, `querySelector`, etc.) in both **native** and **JavaScript** compilation targets.

In JavaScript builds, procedures map directly to the standard DOM API.  
In native builds, the same procedures are defined as **no-ops**, ensuring seamless compilation without conditional logic.

---

## Key Features
- **1:1 compatibility** with `std/dom`
- **Cross-target** support: works in both native and JS builds
- **Safe no-op stubs** on native targets
- **Framework ready**: designed for use within [thing](https://github.com/thing-king)
- **Extended API**: includes modern web APIs not available in `std/dom`

---

## Extended APIs

Beyond `std/dom` compatibility, **thing-king/dom** includes modern web APIs:

### Observers
- **MutationObserver** - Watch for DOM tree changes
- **ResizeObserver** - Monitor element size changes  
- **IntersectionObserver** - Track element visibility

### Additional APIs
- **Date.now()** - High-resolution timestamp

---

## Example
```nim
import thingking/dom

# Standard DOM API (same as std/dom)
let node = getElementById("myDiv")

# Modern Observer APIs (not in std/dom)
proc mutationCallback(mutations: seq[MutationRecord], observer: MutationObserver) =
  console.log("DOM changed!")

let observer = newMutationObserver(mutationCallback)
let options = newMutationObserverInit()
options.childList = true
observer.observe(document.body, options)

# Utility functions
let timestamp = now()  # Date.now()

# On JS builds → behaves as expected
# On native builds → compiles cleanly, no-ops at runtime
```