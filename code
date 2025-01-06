https://github.com/Adathelove/
https://github.com/Adathelove/terraform
https://github.com/Adathelove/terraform/commit/e2de4b6a36825ced61b70ccbee05fbc8f2046e90
provider "libvirt" {
  uri = "qemu:///system"
}

resource "libvirt_volume" "vm_disk" {
  name = "terraform-vm.qcow2"
  pool = "default"
  source = "/path/to/your/base-image.qcow2"
  format = "qcow2"
}

resource "libvirt_domain" "terraform_vm" {
  name   = "terraform-vm"
  memory = 1024
  vcpu   = 1

  disk {
    volume_id = libvirt_volume.vm_disk.id
  }

  network_interface {
    network_name = "default"
  }

  console {
    type        = "pty"
    target_port = "0"
    target_type = "serial"
  }

  graphics {
    type = "spice"
    listen_type = "none"
  }

  video {
    type = "vga"
  }

  boot {
    dev = ["hd"]
  }
}