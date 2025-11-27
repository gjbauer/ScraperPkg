# ScraperPkg
A rewrite of the scraper_efi application in C.

## Wait, you re-wrote a *Rust* program in *C*? *Heresy!!* (Why?)

As it would turn out, LLVM does not have a COFF backend for RISC-V. This makes it incredibly difficult to compile UEFI applications written in Rust for RISC-V. As it would also turn out, trying to compile the UEFI application using an ELF target caused all of the code to get optimized out, lending `objcopy` totally useless.

## How to build and use

Clone the [EDK2 repository](https://github.com/tianocore/edk2), build the base tools, and source the `edksetup.sh` script. After that, clone this repository in the `edk2` source repository, and execute the following command to build with Clang...

`build -p ScraperPkg/ScraperPkg.dsc -a RISCV64 -t CLANGDWARF -b RELEASE`
