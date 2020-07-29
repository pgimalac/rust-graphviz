### Description
FFI bindings for the [Graphviz C library](https://graphviz.org/) generated with [Rust-bindgen](https://github.com/rust-lang/rust-bindgen). Very unsafe and not very usable in my opinion.

### Other similar crates
I discovered that the [graphviz-sys crate](https://crates.io/crates/graphviz-sys) (which is almost exactly the same as this crate) existed when I decided to publish this crate on [crates.io](https://crates.io/). Nevertheless I decided to publish it since I'd like (one day) to crate safe API bindings for the graphviz library. Any help with that would be appreciated.

### How to use
One example of use of the graphviz C library (from [this document](https://www.graphviz.org/pdf/libguide.pdf), although slightly modified) is

```C
#include <graphviz/gvc.h>

int main(int argc, char**argv){
    FILE *fp;
    if (argc > 1)
        fp = fopen(argv[1], "r");
    else
        fp = stdin;

    GVC_t *gvc = gvContext();
    Agraph_t *g = agread(fp, 0);

    gvLayout(gvc, g, "dot");
    gvRender(gvc, g, "plain", stdout);

    gvFreeLayout(gvc, g);
    agclose(g);

    return gvFreeContext(gvc);
}
```

A similar Rust code would be
```Rust

```
