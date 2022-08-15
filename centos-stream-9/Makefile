.PHONY: build login run shell

RAW_IMAGE = mkosi.output/image.raw

$(RAW_IMAGE):
	sudo mkosi --force build

build: $(RAW_IMAGE)

login: $(RAW_IMAGE)
	sudo systemd-nspawn --capability=CAP_NET_ADMIN -b -i $(RAW_IMAGE)

run: $(RAW_IMAGE)
	qemu-system-x86_64                                                   \
		-enable-kvm -cpu host -smp 2 -m 4G                               \
		-nic user,model=virtio-net-pci -bios /usr/share/ovmf/x64/OVMF.fd \
		-vga virtio                                                      \
		-drive format=raw,file=$(RAW_IMAGE)

shell: $(RAW_IMAGE)
	sudo systemd-nspawn --capability=CAP_NET_ADMIN -i $(RAW_IMAGE) /usr/bin/zsh
