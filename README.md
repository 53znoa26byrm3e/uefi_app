# About
Just a test for an UEFI app

# Test

Build
```shell
cargo build --target x86_64-unknown-uefi
```

Copy UEFI file
```shell
cp target/x86_64-unknown-uefi/debug/uefi_app.efi esp/efi/boot/bootx64.efi
```

Launch VM
```shell
qemu-system-x86_64 -enable-kvm \
    -drive if=pflash,format=raw,readonly=on,file=OVMF_CODE.fd \
    -drive if=pflash,format=raw,readonly=on,file=OVMF_VARS.fd \
    -drive format=raw,file=fat:rw:esp
```

