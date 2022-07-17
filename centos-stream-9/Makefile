build:
	sudo mkosi --force build

login:
	sudo systemd-nspawn -b -i ./mkosi.output/image.raw

shell:
	sudo systemd-nspawn -i ./mkosi.output/image.raw /usr/bin/zsh

run:
	qemu-system-x86_64 -enable-kvm -cpu host -smp 2 -m 4096 -nic user,model=virtio-net-pci -bios /usr/share/ovmf/x64/OVMF.fd -drive format=raw,file=mkosi.output/image.raw

run-qcow2:
	qemu-system-x86_64 -enable-kvm -cpu host -smp 2 -m 4096 -nic user,model=virtio-net-pci -bios /usr/share/ovmf/x64/OVMF.fd -drive format=qcow2,file=mkosi.output/image.qcow2

.PHONY: build login shell run run-qcow2
