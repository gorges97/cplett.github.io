---
layout: default
title: Installation
parent: "CREST"
nav_order: 1
has_children: false
permalink: /page/crest/installation
---

## General Considerations

Similar to **xtb**, the **crest** software is open-source and available under the LGPL 3.0 license on the GitHub platform. The [guideline](https://crest-lab.github.io/crest-docs/page/installation) for installation is also similar to **xtb**. In case of any issues, you can always refer to the full documentation for further details.

{% include warning.html content="Primary operating system (OS) for the development and application of **xtb** is Linux. While it is possible to install **xtb** on Windows and macOS, support for these platforms may be more limited." %}


## Straighforward Installation
The most straightforward way to install xtb is by downloading the [precompiled binaries](https://github.com/crest-lab/crest/releases). You can also get bleeding-edge version of the program.
After downloading the appropriate version, extract it, make it executable, and add it to your `PATH` variable:

To verify that the executable is correctly linked, use:

```bash
which crest
```
And check the installed version with:
```bash
crest --version
```

{% include tip.html content='You can add the full path to your Bash shell configuration file (~/.bashrc) to automatically load **crest** in new sessions.'%}

For **crest** to work properly, **xtb** is required. **crest** will automaticall use the **xtb** program sourced, but with the keyword `--xnam <Path to xtb>` you can define the **xtb** binary that will be used by **crest**.

## Compilation 
A more advanced approach is to compile **crest** from the source code. Native compilation has certain advantages over precompiled binaries, such as producing a system-tailored binary and allowing modifications to the software in place.

Here, we follow a minimalistic build using our default toolchain: the `meson` build system and the `ifort`/`icc` compilers.

First step is to clone the official GitHub repository via:
```bash
git clone https://github.com/crest-lab/crest.git
```

Then, define the Fortran and C compilers, which can be installed via Intel's [Developer Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#base-kit):

```bash
export FC=ifort CC=icc
```

Finally, you can build the project with [Meson](https://mesonbuild.com/):

```bash
meson setup _build --prefix=$PWD/_dist
meson install -C _build
```

Alternatively, `gfortran`/`gcc` compilers are also supported. For a complete list of supported compilers and backends, please see the [github page](https://github.com/crest-lab/crest?tab=readme-ov-file#option-3-compiling-from-source).
