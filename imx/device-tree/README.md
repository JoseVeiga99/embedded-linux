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
    node-name@unit-address {
        property-name = "value";
        property-list = <0x01 0x02 0x03>;   // hex values
        another-property;
        subnode@1 {
            sub-property = "subvalue";
        };
    };
};
```
