---
title: Rust Installation.
description: Step by step document showing the installation of Rust Language in windows & Unix.
authors:
  -
    name: Arun kumar N
    avatar: ../assets/image/favicon.png
    description: Creator
update_date : 2026-08-04
published_date : 2026-08-04
banner_image : assets/image/favicon.png
tags:
  - rust lang
hide:
  - navigation
---


## Installation Steps

### Linux and MacOs

To install Rust programming language on linux or macOs system execute the following command on your prefered terminal.

```bash

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

```

<video controls autoplay loop>
  <source src="../static/rust_install.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


- Verify the install.
`rustc --version`

<video controls autoplay loop>
  <source src="../static/rustc_version.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

- Verify Cargo install
`cargo --version`

<video controls autoplay loop>
  <source src="../static/cargo_version.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

- verify rustup install
`rustup --version`


<video controls autoplay loop>
  <source src="../static/rustup_version.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Windows OS

1. For Windows 64-bit download and run `rustup‑init.exe` then follow the onscreen instructions.

[Win 64 bit :octicons-download-16:](https://win.rustup.rs/x86_64){ .md-button }

2. For Windows 32-bit download and run `rustup‑init.exe` then follow the onscreen instructions.

[Win 32 bit :octicons-download-16:](https://win.rustup.rs/i686){ .md-button }

3. For Windows on ARM, download and run `rustup-init.exe` then follow the onscreen instructions. 

[Win on Arm :octicons-download-16:](https://win.rustup.rs/aarch64){ .md-button .md-grid}
 

## Update Rust Language

To update rust language, simply use `rustup` command.

```bash
rustup update stable   
```

<video controls autoplay loop>
  <source src="../static/update_rust.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


## Uninstall Rust and rustup

Run the following commands on your shell or terminal

```sh
rustup self uninstall 
  
```


<video controls autoplay loop>
  <source src="../static/rust_uninstall.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

