## Device Tree

- A Device Tree is a data structure that describes the hardware layout.
- The Linux kernel reads it during boot to know which hardware is present and how to use it.
- It replaces the need for hardcoding platform-specific code into the kernel.

## Device Tree File Types

In the kernel source tree:

    .dtsi → Shared SoC-level definitions (e.g. imx6ull.dtsi)

    .dts → Board-level configuration (e.g. imx6ull-evk.dts)

Example file hierarchy:

## Sintax
Device Tree syntax is based on a simple, C-like declarative format. The source files usually have .dts or .dtsi extensions.
More info here: https://events.static.linuxfound.org/sites/events/files/slides/petazzoni-device-tree-dummies.pdf
```c
/ {
    node1 {
        a-string-property = "a string";
        a-string-list-property = "first string", "second string";
        a-byte-data-property = [0x01 0x02 0x03];
        child-node1 {
            first-child-property;
            second-child-property
            a-string-property = "child string";
        };
        child-node2 {
        };
    };
    node2 {
        an-empty-property;
        a-cell-property = <1 2 3>;
        child-node1 {
        };
    };
};
```

Where:

    / is the root node of the tree
    node1 and node2 are child nodes of the root node
    node1 has two child nodes: child-node1 and child-node2

Each node has a set of properties associated with it:

    Null-terminated text strings are wrapped with double quotes:
        a-string-property = "a string";

    Cells (32-bit unsigned integers) are space-delimited and wrapped with angle brackets:
        a-cell-property = <1 2 3>;

    Binary data is space-delimited and wrapped with square brackets:
        a-binary-property = [0x01 0x02 0x03];

    Mixed representation data can be concatenated using commas:
        a-mixed-property = "a string", [0x01 0x02 0x03], <1 2 3>;

    Commas are also used to create string lists:
        a-string-list = "first string", "second string";

